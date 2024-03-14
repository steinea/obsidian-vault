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
  {
    title: "Timeline",
    query: 'LIST FROM "dataview/timeline" SORT file.name ASC',
    content: `---\npermalink: timeline\n---\n`,
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

// Activity

  {
    title: "Building",
    query: 'TABLE WITHOUT ID file.link AS Set, series AS Series, item AS Item, pieces AS Pieces, age AS Age, status AS Status FROM "constellation/lego" WHERE status = "built" OR status = "unbuilt" OR status = "wishlist" SORT status ASC, file.name ASC',
    content: `---\npermalink: activity/building\n---\n`,
  },
  {
    title: "Dreaming",
    query: 'TABLE WITHOUT ID file.link AS "Dreaming" FROM "activity/dreaming" SORT date DESC',
    content: `---\npermalink: activity/dreaming\n---\n`,
  },
  {
    title: "Drinking",
    query: 'TABLE WITHOUT ID file.link AS "Drinking" FROM "activity/drinking" SORT date DESC',
    content: `---\npermalink: activity/drinking\n---\n`,
  },
  {
    title: "Exercising",
    query: 'TABLE WITHOUT ID file.link AS "Exercising" FROM "activity/exercising" SORT date DESC',
    content: `---\npermalink: activity/exercising\n---\n`,
  },
  {
    title: "Listening",
    query: 'TABLE WITHOUT ID file.link AS "Listening" FROM "activity/listening" SORT date DESC',
    content: `---\npermalink: activity/listening\n---\n`,
  },
  {
    title: "Playing Now",
    query: 'TABLE WITHOUT ID file.link AS "Playing", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies FROM "constellation/games" WHERE progress = "now" SORT duration DESC',
    content: `---\npermalink: activity/playing/now\n---\n`,
  },
  {
    title: "Playing Next",
    query: 'TABLE WITHOUT ID file.link AS "Library", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "next" SORT platform, howlongtobeat ASC',
    content: `---\npermalink: activity/playing/next\n---\n`,
  },
  {
    title: "Playing Completed",
    query: 'TABLE WITHOUT ID file.link AS "Played", duration.hours AS "Hours", trophies AS Trophies, percent AS "★", date AS Date FROM "constellation/games" WHERE progress = "complete" OR progress = "stopped" SORT date DESC',
    content: `---\npermalink: activity/playing/completed\n---\n`,
  },
  {
    title: "Playing Stopped",
    query: 'TABLE WITHOUT ID file.link AS "Incomplete Games", platform AS Platform, duration.hours AS "Hours", trophies AS Trophies, percent AS "★", date AS Date FROM "constellation/games" WHERE progress = "stopped" SORT date DESC',
    content: `---\npermalink: activity/playing/stopped\n---\n`,
  },
  {
    title: "Playing Most",
    query: 'TABLE WITHOUT ID file.link AS "Most Played", platform AS Platform, duration.hours AS "Hours" FROM "constellation/games" WHERE progress != "next" SORT duration DESC LIMIT 10',
    content: `---\npermalink: activity/playing/most\n---\n`,
  },
  {
    title: "Playing Shortest",
    query: 'TABLE WITHOUT ID file.link AS "Shortest to Play", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "next" SORT howlongtobeat ASC LIMIT 10',
    content: `---\npermalink: activity/playing/shortest\n---\n`,
  },
  {
    title: "Playing Wishlist",
    query: 'TABLE WITHOUT ID file.link AS "Wishlist", platform AS Platform, howlongtobeat.hours AS "Hours" FROM "constellation/games" WHERE progress = "wishlist" SORT file.name ASC',
    content: `---\npermalink: activity/playing/wishlist\n---\n`,
  },
  {
    title: "Posting",
    query: 'TABLE WITHOUT ID file.link AS Post, date AS Date FROM "activity/posting" SORT date DESC',
    content: `---\npermalink: activity/posting\n---\n`,
  },
  {
    title: "Reading",
    query: 'TABLE WITHOUT ID file.link AS "Reading" FROM "activity/reading" SORT date DESC',
    content: `---\npermalink: activity/reading\n---\n`,
  },
  {
    title: "Sleeping",
    query: 'TABLE WITHOUT ID file.link AS "Sleeping" FROM "activity/sleeping" SORT date DESC',
    content: `---\npermalink: activity/sleeping\n---\n`,
  },
  {
    title: "Traveling",
    query: 'TABLE WITHOUT ID file.link AS "Traveling" FROM "activity/traveling" SORT date DESC',
    content: `---\npermalink: activity/traveling\n---\n`,
  },
  {
    title: "Watching Film",
    query: 'TABLE WITHOUT ID file.link AS "Film", rating AS Rating, liked AS Liked, watchedDate AS Date FROM "constellation/film" WHERE watched = "Yes" SORT watchedDate DESC',
    content: `---\npermalink: activity/watching/film\n---\n`,
  },
  {
    title: "Watching Television",
    query: 'TABLE WITHOUT ID file.link AS Title, series AS Series, seasonEpisode AS Episode, watchedDate AS Date FROM "constellation/episodes" WHERE watched = "Yes" SORT watchedDate DESC, seasonEpisode DESC',
    content: `---\npermalink: activity/watching/television\n---\n`,
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

// Constellation

  {
    title: "Associations",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/associations" SORT file.name ASC',
    content: `---\npermalink: constellation/associations\n---\n`,
  },
  {
    title: "Books",
    query: 'TABLE WITHOUT ID file.link AS "Title", author AS Author, date AS Date FROM "constellation/books" SORT author ASC, date ASC, file.name ASC',
    content: `---\npermalink: constellation/books\n---\n`,
  },
  {
    title: "Book Series",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/bookseries" SORT file.name ASC',
    content: `---\npermalink: constellation/book-series\n---\n`,
  },
  {
    title: "Certifications",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/certifications" SORT file.name ASC',
    content: `---\npermalink: constellation/certifications\n---\n`,
  },
  {
    title: "Channels",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/channels" SORT file.name ASC',
    content: `---\npermalink: constellation/channels\n---\n`,
  },
  {
    title: "Climate",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/climate" SORT file.name ASC',
    content: `---\npermalink: constellation/climate\n---\n`,
  },
  {
    title: "Collectives",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/collectives" SORT file.name ASC',
    content: `---\npermalink: constellation/collectives\n---\n`,
  },
  {
    title: "Comics",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/comics" SORT file.name ASC',
    content: `---\npermalink: constellation/comics\n---\n`,
  },
  {
    title: "Companies",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/companies" SORT file.name ASC',
    content: `---\npermalink: constellation/companies\n---\n`,
  },
  {
    title: "Concepts",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/concepts" SORT file.name ASC',
    content: `---\npermalink: constellation/concepts\n---\n`,
  },
  {
    title: "Conferences",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/conferences" SORT file.name ASC',
    content: `---\npermalink: constellation/conferences\n---\n`,
  },
  {
    title: "Conventions",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/conventions" SORT file.name ASC',
    content: `---\npermalink: constellation/conventions\n---\n`,
  },
  {
    title: "Episodes",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/episodes" SORT date DESC',
    content: `---\npermalink: constellation/episodes\n---\n`,
  },
  {
    title: "Film",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/film" SORT file.name ASC',
    content: `---\npermalink: constellation/film\n---\n`,
  },
  {
    title: "Funds",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/funds" SORT file.name ASC',
    content: `---\npermalink: constellation/funds\n---\n`,
  },
  {
    title: "Games",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/games" SORT file.name ASC',
    content: `---\npermalink: constellation/games\n---\n`,
  },
  {
    title: "Institutes",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/institutes" SORT file.name ASC',
    content: `---\npermalink: constellation/institutes\n---\n`,
  },
  {
    title: "Jams",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/jams" SORT file.name ASC',
    content: `---\npermalink: constellation/jams\n---\n`,
  },
  {
    title: "Journals",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/journals" SORT file.name ASC',
    content: `---\npermalink: constellation/journals\n---\n`,
  },
  {
    title: "Lego",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/lego" SORT file.name ASC',
    content: `---\npermalink: constellation/lego\n---\n`,
  },
  {
    title: "Literary Reviews",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/literaryreviews" SORT file.name ASC',
    content: `---\npermalink: constellation/literary-reviews\n---\n`,
  },
  {
    title: "Magazines",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/magazines" SORT file.name ASC',
    content: `---\npermalink: constellation/magazines\n---\n`,
  },
  {
    title: "Music",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/music" SORT file.name ASC',
    content: `---\npermalink: constellation/music\n---\n`,
  },
  {
    title: "People",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/people" SORT file.name ASC',
    content: `---\npermalink: constellation/people\n---\n`,
  },
  {
    title: "Places",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/places" SORT file.name ASC',
    content: `---\npermalink: constellation/places\n---\n`,
  },
  {
    title: "Podcasts",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/podcasts" SORT file.name ASC',
    content: `---\npermalink: constellation/podcasts\n---\n`,
  },
  {
    title: "Proficiencies",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/proficiencies" SORT file.name ASC',
    content: `---\npermalink: constellation/proficiencies\n---\n`,
  },
  {
    title: "Psychometrics",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/psychometrics" SORT file.name ASC',
    content: `---\npermalink: constellation/psychometrics\n---\n`,
  },
  {
    title: "Publications",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/publications" SORT file.name ASC',
    content: `---\npermalink: constellation/publications\n---\n`,
  },
  {
    title: "Standards",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/standards" SORT file.name ASC',
    content: `---\npermalink: constellation/standards\n---\n`,
  },
  {
    title: "Schools",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/schools" SORT file.name ASC',
    content: `---\npermalink: constellation/schools\n---\n`,
  },
  {
    title: "Social",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/social" SORT file.name ASC',
    content: `---\npermalink: constellation/social\n---\n`,
  },
  {
    title: "Television",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/television" SORT file.name ASC',
    content: `---\npermalink: constellation/television\n---\n`,
  },
  {
    title: "Tools",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/tools" SORT file.name ASC',
    content: `---\npermalink: constellation/tools\n---\n`,
  },
  {
    title: "Workshops",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/workshops" SORT file.name ASC',
    content: `---\npermalink: constellation/workshops\n---\n`,
  },
  {
    title: "Worldbuilding",
    query: 'TABLE WITHOUT ID file.link AS "File", date AS Date FROM "constellation/worldbuilding" SORT file.name ASC',
    content: `---\npermalink: constellation/worldbuilding\n---\n`,
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