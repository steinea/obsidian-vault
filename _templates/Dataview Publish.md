<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;

// Add as many filenames and queries as you'd like!
const queries = [

// Root

  {
    title: "About",
    query: 'LIST FROM "dataview/about" SORT file.name ASC',
    content: `---\npermalink: about\n---\n`,
  },
  {
    title: "Activity",
    query: 'LIST FROM "dataview/activity" AND -"dataview/activity/playingcompleted" AND -"dataview/activity/playingmost" AND -"dataview/activity/playingnext" AND -"dataview/activity/playingnow" AND -"dataview/activity/playingshortest" AND -"dataview/activity/playingstopped" AND -"dataview/activity/playingwishlist" AND -"dataview/activity/watchingfilm" AND -"dataview/activity/watchingtelevision" SORT file.name ASC',
    content: `---\npermalink: activity\n---\n`,
  },
  {
    title: "Collections",
    query: 'LIST FROM "dataview/collections" SORT file.name ASC',
    content: `---\npermalink: collections\n---\n`,
  },
  {
    title: "Constellation",
    query: 'LIST FROM "dataview/constellation" SORT file.name ASC',
    content: `---\npermalink: constellation\n---\n`,
  },

// About

  {
    title: "Biography",
    query: 'LIST FROM "about/biography" SORT date DESC',
    content: `---\npermalink: about/biography\n---\n`,
  },
  {
    title: "Now",
    query: 'LIST FROM "about/now" SORT date DESC',
    content: `---\npermalink: about/now\n---\n`,
  },
  {
    title: "Personality",
    query: 'LIST FROM "about/personality" SORT date DESC',
    content: `---\npermalink: about/personality\n---\n`,
  },
  {
    title: "Updates",
    query: 'LIST FROM "about/updates" SORT date DESC',
    content: `---\npermalink: about/updates\n---\n`,
  },

// Blog

  {
    title: "Latest",
    query: 'TABLE WITHOUT ID file.link AS "Latest", date AS Date FROM "blog" WHERE category="blog" SORT date DESC',
    content: `---\npermalink: blog/latest\n---\n`,
  },
  {
    title: "Juvenilia, 3",
    query: 'TABLE WITHOUT ID file.link AS "Juvenilia, 3", date AS Date FROM "blog" WHERE category="juvenilia-3" SORT date DESC',
    content: `---\npermalink: blog/juvenilia3\n---\n`,
  },
  {
    title: "Field Notes, 2",
    query: 'TABLE WITHOUT ID file.link AS "Field Notes, 2", date AS Date FROM "blog" WHERE category="field-notes-2" SORT date DESC',
    content: `---\npermalink: blog/fieldnotes2\n---\n`,
  },
  {
    title: "Ludology",
    query: 'TABLE WITHOUT ID file.link AS "Ludology", date AS Date FROM "blog" WHERE category="ludology" SORT date DESC',
    content: `---\npermalink: blog/ludology\n---\n`,
  },
  {
    title: "Excurses, 3",
    query: 'TABLE WITHOUT ID file.link AS "Excurses, 3", date AS Date FROM "blog" WHERE category="excurses-3" SORT date DESC',
    content: `---\npermalink: blog/excurses3\n---\n`,
  },
  {
    title: "Dialogues",
    query: 'TABLE WITHOUT ID file.link AS "Dialogues", date AS Date FROM "blog" WHERE category="dialogues" SORT date DESC',
    content: `---\npermalink: blog/dialogues\n---\n`,
  },
  {
    title: "Excurses, 2",
    query: 'TABLE WITHOUT ID file.link AS "Excurses, 2", date AS Date FROM "blog" WHERE category="excurses-2" SORT date DESC',
    content: `---\npermalink: blog/excurses2\n---\n`,
  },
  {
    title: "Juvenilia, 2",
    query: 'TABLE WITHOUT ID file.link AS "Juvenilia, 2", date AS Date FROM "blog" WHERE category="dialogues" SORT date DESC',
    content: `---\npermalink: blog/juvenilia2\n---\n`,
  },
  {
    title: "Excurses",
    query: 'TABLE WITHOUT ID file.link AS "Excurses", date AS Date FROM "blog" WHERE category="excurses" SORT date DESC',
    content: `---\npermalink: blog/excurses\n---\n`,
  },
  {
    title: "Juvenilia",
    query: 'TABLE WITHOUT ID file.link AS "Juvenilia", date AS Date FROM "blog" WHERE category="juvenilia" SORT date DESC',
    content: `---\npermalink: blog/juvenilia\n---\n`,
  },
  {
    title: "Field Notes",
    query: 'TABLE WITHOUT ID file.link AS "Field Notes", date AS Date FROM "blog" WHERE category="field-notes" SORT date DESC',
    content: `---\npermalink: blog/fieldnotes\n---\n`,
  },

// Collections

  {
    title: "Annotations",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/annotations" SORT date DESC',
    content: `---\npermalink: collections/annotations\n---\n`,
  },
  {
    title: "Bibliographies",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/bibliographies" SORT date DESC',
    content: `---\npermalink: collections/bibliographies\n---\n`,
  },
  {
    title: "Commonplace",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/commonplace" SORT date DESC',
    content: `---\npermalink: collections/commonplace\n---\n`,
  },
  {
    title: "Playlists",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/playlists" SORT date DESC',
    content: `---\npermalink: collections/playlists\n---\n`,
  },
  {
    title: "Study",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/study" SORT date DESC',
    content: `---\npermalink: collections/study\n---\n`,
  },
  {
    title: "Teaching",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "collections/teaching" SORT date DESC',
    content: `---\npermalink: collections/teaching\n---\n`,
  },
];

await queries.forEach(async (el) => {
  const { title: filename, query, content } = el;
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }
  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent =  `${content}\n\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
openPublishPanel();

// Credit to Joschua Drescher,  https://joschua.io/posts/2023/09/01/obsidian-publish-dataview/, for this solution. Joschua was also kind enough to provide me with a modification via email to include content before the dataview query table, allowing me to set permalinks, as seen above. Thanks Joschua!

%>