<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;

// Add as many filenames and queries as you'd like!
const fileAndQuery = new Map([


// Activity dataview maps

  [
	"Building",
	'TABLE WITHOUT ID file.link AS Set, series AS Series, item AS Item, pieces AS Pieces, age AS Age, status AS Status FROM "constellation/lego" WHERE status = "built" OR status = "unbuilt" OR status = "wishlist" SORT status ASC, file.name ASC',
  ],
  [
	"Dreaming",
	'TABLE WITHOUT ID file.link AS "Dreaming" FROM "activity/dreaming" SORT date DESC',
  ],
  [
	"drinking",
	'TABLE WITHOUT ID file.link AS "Drinking" FROM "activity/drinking" SORT date DESC',
  ],
  [
	"Exercising",
	'TABLE WITHOUT ID file.link AS "Exercising" FROM "activity/exercising" SORT date DESC',
  ],
  [
	"Listening",
	'TABLE WITHOUT ID file.link AS "Listening" FROM "activity/listening" SORT date DESC',
  ],
  [
	"playingnow",
	'TABLE WITHOUT ID file.link AS "Playing", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies FROM "constellation/games" WHERE progress = "now" SORT duration DESC',
  ],
  [
	"playingnext",
	'TABLE WITHOUT ID file.link AS "Library", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "next" SORT platform, howlongtobeat ASC',
  ],
  [
	"playingcompleted",
	'TABLE WITHOUT ID file.link AS "Played", duration.hours AS "Hours", trophies AS Trophies, percent AS "★", date AS Date FROM "constellation/games" WHERE progress = "complete" OR progress = "stopped" SORT date DESC',
  ],
  [
	"playingstopped",
	'TABLE WITHOUT ID file.link AS "Incomplete Games", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies, percent AS "★", date AS Date FROM "constellation/games" WHERE progress = "stopped" SORT date DESC',
  ],
  [
	"playingmost",
	'TABLE WITHOUT ID file.link AS "Most Played", platform AS Platform, duration.hours AS "Hours" FROM "constellation/games" WHERE progress != "next" SORT duration DESC LIMIT 10',
  ],
  [
	"playingshortest",
	'TABLE WITHOUT ID file.link AS "Shortest to Play", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "next" SORT howlongtobeat ASC LIMIT 10',
  ],
  [
	"playingwishlist",
	'TABLE WITHOUT ID file.link AS "Wishlist", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "wishlist" SORT file.name ASC',
  ],
  [
    "Posting",
	'TABLE WITHOUT ID file.link AS Post, date AS Date FROM "activity/posting" SORT date DESC',
  ],
  [
	"Reading",
	'TABLE WITHOUT ID file.link AS "Reading" FROM "activity/reading" SORT date DESC',
  ],
  [
	"Sleeping",
	'TABLE WITHOUT ID file.link AS "Sleeping" FROM "activity/sleeping" SORT date DESC',
  ],
  [
	"Traveling",
	'TABLE WITHOUT ID file.link AS "Traveling" FROM "activity/traveling" SORT date DESC',
  ],
  [
	"watchingfilm",
	'TABLE WITHOUT ID file.link AS "Film", rating AS Rating, liked AS Liked, watchedDate AS Date FROM "constellation/film" WHERE watched = "Yes" SORT watchedDate DESC',
  ],
  [
	"watchingtelevision",
	'TABLE WITHOUT ID file.link AS Title, series AS Series, seasonEpisode AS Episode, watchedDate AS Date FROM "constellation/episodes" WHERE watched = "Yes" SORT watchedDate DESC, seasonEpisode DESC',
  ],



// Timeline dataview maps

  [
	"dataview/timeline",
	'LIST FROM "mocs/timeline" SORT file.name ASC',
  ],

]);

await fileAndQuery.forEach(async (query, filename) => {
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }
  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent = `%% #Ignore update via "Update Publish Files" template %% \n\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
openPublishPanel();
%>