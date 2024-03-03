<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;

// Add as many filenames and queries as you'd like!
const fileAndQuery = new Map([
  [
	"dataview-about",
	'LIST FROM "dataview/about" SORT file.name ASC',
  ],
  [
	"dataview-activity",
	'LIST FROM "dataview/activity" AND -"dataview/activity/playingcompleted" AND -"dataview/activity/playingmost" AND -"dataview/activity/playingnext" AND -"dataview/activity/playingnow" AND -"dataview/activity/playingshortest" AND -"dataview/activity/playingstopped" AND -"dataview/activity/playingwishlist" AND -"dataview/activity/watchingfilm" AND -"dataview/activity/watchingtelevision" SORT file.name ASC',
  ],
  [
	"dataview-collections",
	'LIST FROM "dataview/collections" SORT file.name ASC',
  ],
  [
	"dataview-constellation",
	'LIST FROM "dataview/constellation" SORT file.name ASC',
  ],

// About dataview maps

  [
	"biography",
	'TABLE WITHOUT ID file.link AS "Biography", date AS Date FROM "about/biography" SORT date DESC',
  ],
  [
	"personality",
	'TABLE WITHOUT ID file.link AS "Personality", date AS Date FROM "about/personality" SORT date DESC',
  ],

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
	'TABLE WITHOUT ID file.link AS "Now Playing", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies FROM "constellation/games" WHERE progress = "now" SORT duration DESC',
  ],
  [
	"playingnext",
	'TABLE WITHOUT ID file.link AS "Library", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "next" SORT platform, howlongtobeat ASC',
  ],
  [
	"playingcompleted",
	'TABLE WITHOUT ID file.link AS "Perfect Games", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies, date AS Date FROM "constellation/games" WHERE progress = "complete" SORT date DESC',
  ],
  [
	"playingstopped",
	'TABLE WITHOUT ID file.link AS "Incomplete Games", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies, date AS Date FROM "constellation/games" WHERE progress = "stopped" SORT date DESC',
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

// Blog dataview maps

  [
	"latest",
	'TABLE WITHOUT ID file.link AS "Latest", date AS Date FROM "blog" WHERE category ="blog" SORT date DESC',
  ],
  [
	"juvenilia3",
	'TABLE WITHOUT ID file.link AS "Juvenilia, 3", date AS Date FROM "blog" WHERE category ="juvenilia-3" SORT date DESC',
  ],
  [
	"fieldnotes2",
	'TABLE WITHOUT ID file.link AS "Field Notes, 2", date AS Date FROM "blog" WHERE category ="field-notes-2" SORT date DESC',
  ],
  [
	"ludology",
	'TABLE WITHOUT ID file.link AS "Ludology", date AS Date FROM "blog" WHERE category ="ludology" SORT date DESC',
  ],
  [
	"excurses3",
	'TABLE WITHOUT ID file.link AS "Excurses, 3", date AS Date FROM "blog" WHERE category ="excurses-3" SORT date DESC',
  ],
  [
	"dialogues",
	'TABLE WITHOUT ID file.link AS "Dialogues", date AS Date FROM "blog" WHERE category ="dialogues" SORT date DESC',
  ],
  [
	"excurses2",
	'TABLE WITHOUT ID file.link AS "Excurses, 2", date AS Date FROM "blog" WHERE category ="excurses-2" SORT date DESC',
  ],
  [
	"juvenilia2",
	'TABLE WITHOUT ID file.link AS "Juvenilia, 2", date AS Date FROM "blog" WHERE category ="juvenilia-2" SORT date DESC',
  ],
  [
	"excurses",
	'TABLE WITHOUT ID file.link AS "Excurses", date AS Date FROM "blog" WHERE category ="excurses" SORT date DESC',
  ],
  [
	"juvenilia",
	'TABLE WITHOUT ID file.link AS "Juvenilia", date AS Date FROM "blog" WHERE category ="juvenilia" SORT date DESC',
  ],
  [
	"fieldnotes",
	'TABLE WITHOUT ID file.link AS "Field Notes", date AS Date FROM "blog" WHERE category ="field-notes" SORT date DESC',
  ],

// Collections dataview maps

  [
	"annotations",
	'TABLE WITHOUT ID file.link AS "Title", date AS Date FROM "collections/annotations" SORT date DESC',
  ],
  [
	"bibliographies",
	'TABLE WITHOUT ID file.link AS "Bibliographies", date AS Date FROM "collections/bibliographies" SORT date DESC',
  ],
  [
	"commonplace",
	'TABLE WITHOUT ID file.link AS "Commonplace", date AS Date FROM "collections/commonplace" SORT date DESC',
  ],
  [
	"playlists",
	'TABLE WITHOUT ID file.link AS "Playlists", date AS Date FROM "collections/playlists" SORT date DESC',
  ],
  [
	"study",
	'TABLE WITHOUT ID file.link AS "Study", date AS Date FROM "collections/study" SORT date DESC',
  ],
  [
	"teaching",
	'TABLE WITHOUT ID file.link AS "Teaching", date AS Date FROM "collections/teaching" SORT date DESC',
  ],

// Constellation dataview maps

  [
	"associations",
	'TABLE WITHOUT ID file.link AS "Associations" FROM "constellation/associations" SORT file.name ASC',
  ],
  [
	"books",
	'TABLE WITHOUT ID file.link AS "Books", author AS Author, date AS Date FROM "constellation/books" SORT author DESC, date ASC, file.name ASC',
  ],
  [
	"bookseries",
	'TABLE WITHOUT ID file.link AS "Book Series" FROM "constellation/bookseries" SORT file.name ASC',
  ],
  [
	"certifications",
	'TABLE WITHOUT ID file.link AS "Certifications" FROM "constellation/certifications" SORT file.name ASC',
  ],
  [
	"channels",
	'TABLE WITHOUT ID file.link AS "Channels" FROM "constellation/channels" SORT file.name ASC',
  ],
  [
	"climate",
	'TABLE WITHOUT ID file.link AS "Climate" FROM "constellation/climate" SORT file.name ASC',
  ],
  [
	"collectives",
	'TABLE WITHOUT ID file.link AS "Collectives" FROM "constellation/collectives" SORT file.name ASC',
  ],
  [
	"comics",
	'TABLE WITHOUT ID file.link AS "Comics" FROM "constellation/comics" SORT file.name ASC',
  ],
  [
	"companies",
	'TABLE WITHOUT ID file.link AS "Companies" FROM "constellation/companies" SORT file.name ASC',
  ],
  [
	"concepts",
	'TABLE WITHOUT ID file.link AS "Concepts" FROM "constellation/concepts" SORT file.name ASC',
  ],
  [
	"conferences",
	'TABLE WITHOUT ID file.link AS "Conferences" FROM "constellation/conferences" SORT file.name ASC',
  ],
  [
	"conventions",
	'TABLE WITHOUT ID file.link AS "Conventions" FROM "constellation/conventions" SORT file.name ASC',
  ],
  [
	"economics",
	'TABLE WITHOUT ID file.link AS "Economics" FROM "constellation/economics" SORT file.name ASC',
  ],
  [
	"episodes",
	'TABLE WITHOUT ID file.link AS "Episodes" FROM "constellation/episodes" SORT date DESC',
  ],
  [
	"film",
	'TABLE WITHOUT ID file.link AS "Film" FROM "constellation/film" SORT file.name ASC',
  ],
  [
	"funds",
	'TABLE WITHOUT ID file.link AS "Funds" FROM "constellation/funds" SORT file.name ASC',
  ],
  [
	"games",
	'TABLE WITHOUT ID file.link AS "Games" FROM "constellation/games" SORT file.name ASC',
  ],
  [
	"institutes",
	'TABLE WITHOUT ID file.link AS "Institutes" FROM "constellation/institutes" SORT file.name ASC',
  ],
  [
	"jams",
	'TABLE WITHOUT ID file.link AS "Jams" FROM "constellation/jams" SORT file.name ASC',
  ],
  [
	"journals",
	'TABLE WITHOUT ID file.link AS "Journals" FROM "constellation/journals" SORT file.name ASC',
  ],
  [
	"lego",
	'TABLE WITHOUT ID file.link AS "Lego" FROM "constellation/lego" SORT file.name ASC',
  ],
  [
	"literaryreviews",
	'TABLE WITHOUT ID file.link AS "Literary Reviews" FROM "constellation/literaryreviews" SORT file.name ASC',
  ],
  [
	"magazines",
	'TABLE WITHOUT ID file.link AS "Magazines" FROM "constellation/magazines" SORT file.name ASC',
  ],
  [
	"music",
	'TABLE WITHOUT ID file.link AS "Music" FROM "constellation/music" SORT file.name ASC',
  ],
  [
	"people",
	'TABLE WITHOUT ID file.link AS "People" FROM "constellation/people" SORT file.name ASC',
  ],
  [
	"places",
	'TABLE WITHOUT ID file.link AS "Places" FROM "constellation/places" SORT file.name ASC',
  ],
  [
	"podcasts",
	'TABLE WITHOUT ID file.link AS "Podcasts" FROM "constellation/podcasts" SORT file.name ASC',
  ],
  [
	"proficiencies",
	'TABLE WITHOUT ID file.link AS "Proficiencies" FROM "constellation/proficiencies" SORT file.name ASC',
  ],
  [
	"psychometrics",
	'TABLE WITHOUT ID file.link AS "Psychometrics" FROM "constellation/psychometrics" SORT file.name ASC',
  ],
  [
	"publications",
	'TABLE WITHOUT ID file.link AS "Publications" FROM "constellation/publications" SORT file.name ASC',
  ],
  [
	"standards",
	'TABLE WITHOUT ID file.link AS "Standards" FROM "constellation/standards" SORT file.name ASC',
  ],
  [
	"schools",
	'TABLE WITHOUT ID file.link AS "Schools" FROM "constellation/schools" SORT file.name ASC',
  ],
  [
	"social",
	'TABLE WITHOUT ID file.link AS "Social" FROM "constellation/social" SORT file.name ASC',
  ],
  [
	"television",
	'TABLE WITHOUT ID file.link AS "Television" FROM "constellation/television" SORT file.name ASC',
  ],
  [
	"tools",
	'TABLE WITHOUT ID file.link AS "Tools" FROM "constellation/tools" SORT file.name ASC',
  ],
  [
	"workshops",
	'TABLE WITHOUT ID file.link AS "Workshops" FROM "constellation/workshops" SORT file.name ASC',
  ],
  [
	"worldbuilding",
	'TABLE WITHOUT ID file.link AS "Worldbuilding" FROM "constellation/worldbuilding" SORT file.name ASC',
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