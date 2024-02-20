<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;

// Add as many filenames and queries as you'd like!
const fileAndQuery = new Map([
  [
	"dataview-activity",
	'LIST FROM "mocs/activity" SORT file.name ASC',
  ],
  [
	"dataview-collections",
	'LIST FROM "mocs/collections" SORT file.name ASC',
  ],
  [
	"dataview-constellation",
	'LIST FROM "mocs/constellation" SORT file.name ASC',
  ],
  [
	"dataview-timeline",
	'LIST FROM "mocs/timeline" SORT file.name ASC',
  ],
  [
	"Building",
	'TABLE WITHOUT ID file.link AS Set, series AS Series, item AS Item, pieces AS Pieces, age AS Age, status AS Status FROM "constellation/lego" WHERE status = "built" OR status = "unbuilt" OR status = "wishlist" SORT status ASC, file.name ASC',
  ],
  [
    "Posting",
	'TABLE WITHOUT ID file.link AS Post, date AS Date FROM "activity/posting" SORT date DESC',
  ],
  [
	"latest",
	'TABLE WITHOUT ID file.link AS "Latest", date AS Date FROM "blog" WHERE category ="blog" SORT date DESC',
  ],
  [
	"juvenilia-3",
	'TABLE WITHOUT ID file.link AS "Juvenilia, 3", date AS Date FROM "blog" WHERE category ="juvenilia-3" SORT date DESC',
  ],
  [
	"field-notes-2",
	'TABLE WITHOUT ID file.link AS "Field Notes, 2", date AS Date FROM "blog" WHERE category ="field-notes-2" SORT date DESC',
  ],
  [
	"ludology",
	'TABLE WITHOUT ID file.link AS "Ludology", date AS Date FROM "blog" WHERE category ="ludology" SORT date DESC',
  ],
  [
	"excurses-3",
	'TABLE WITHOUT ID file.link AS "Excurses, 3", date AS Date FROM "blog" WHERE category ="excurses-3" SORT date DESC',
  ],
  [
	"dialogues",
	'TABLE WITHOUT ID file.link AS "Dialogues", date AS Date FROM "blog" WHERE category ="dialogues" SORT date DESC',
  ],
  [
	"excurses-2",
	'TABLE WITHOUT ID file.link AS "Excurses, 2", date AS Date FROM "blog" WHERE category ="excurses-2" SORT date DESC',
  ],
  [
	"juvenilia-2",
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
	"field-notes",
	'TABLE WITHOUT ID file.link AS "Field Notes", date AS Date FROM "blog" WHERE category ="field-notes" SORT date DESC',
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