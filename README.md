# Actor - Metacritic Scraper

## Metacritic scraper

Since Metacritic doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Metacritic data scraper supports the following features:

-   Search any keyword - You can search any keyword to retrieve games, people, musics, movies, TV shows, companies and many more things Metacritic provides. Type any keyword you want to get the results of.

-   Scrape lists - Scrape any list that you'd like to get from Metacritic

-   Scrape reviews - Get reviews from any object. Even if it is a game or a music, you can get all the reviews from Metacritic.

-   Movies, Games, Albums, TV Shows, People or Companies. All of the information can be retrieved right away from Metacritic!

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/metacritic-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Metacritic that should be visited. Possible fields are:

- `startUrls`: (Optional) (Array) List of Metacritic URLs. You can provide search, browse, game detail, movie detail, music detail, TV show detail, person detail, company detail and many more different detail URLs.

- `search`: (Optional) (String) Keyword that you want to search on Metacritic.

- `searchMode`: (Optional) (String) Search mode is only required when `search` attribute is provided into the scraper. It changes the search results and provide you the best outcome from Metacritic.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that Metacritic provides inside the data points. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all detail requests. If actor doesn't block very often it'll scrape 100 items in 2 minutes with ~0.04-0.06 compute units.

### Metacritic Scraper Input example

```json
{
  "startUrls": [
    "https://www.metacritic.com/company/rca",
    "https://www.metacritic.com/music/sos/sza",
    "https://www.metacritic.com/tv/the-witcher-blood-origin",
    "https://www.metacritic.com/movie/whitney-houston-i-wanna-dance-with-somebody",
    "https://www.metacritic.com/game/playstation-5/elden-ring",
    "https://www.metacritic.com/person/robert-downey-jr",
    "https://www.metacritic.com/search/all/hel/results",
    "https://www.metacritic.com/search/person/hel/results",
    "https://www.metacritic.com/search/game/hel/results",
    "https://www.metacritic.com/browse/movies/score/metascore/all/filtered/netflix",
    "https://www.metacritic.com/browse/tv/score/metascore/year/filtered?sort=desc&view=detailed",
    "https://www.metacritic.com/browse/games/genre/date/action/ps4"
  ],
  "search": "last of us",
  "searchMode": "all",
  "includeReviews": false,
  "proxy": {
      "useApifyProxy": true
  },
  "endPage": 5,
  "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Metacritic Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Metacritic actor.

## Scraped Metacritic Properties

The structure of each item in Metacritic looks like this:

### Movie Detail

```json
{
	"type": "movie",
	"url": "https://www.metacritic.com/movie/whitney-houston-i-wanna-dance-with-somebody",
	"title": "Whitney Houston: I Wanna Dance With Somebody",
	"year": "2022",
	"metascore": 51,
	"userscore": 6,
	"starring": [
		{
			"name": "Alana Monteiro",
			"url": "https://www.metacritic.com/person/alana-monteiro"
		},
		{
			"name": "Ashton Sanders",
			"url": "https://www.metacritic.com/person/ashton-sanders"
		},
		{
			"name": "Bria Danielle Singleton",
			"url": "https://www.metacritic.com/person/bria-danielle-singleton"
		},
		{
			"name": "Clarke Peters",
			"url": "https://www.metacritic.com/person/clarke-peters"
		},
		{
			"name": "Daniel Washington",
			"url": "https://www.metacritic.com/person/daniel-washington"
		},
		{
			"name": "Heidi Garza",
			"url": "https://www.metacritic.com/person/heidi-garza"
		},
		{
			"name": "Marilyn Swick",
			"url": "https://www.metacritic.com/person/marilyn-swick"
		},
		{
			"name": "Mary Ann Schaub",
			"url": "https://www.metacritic.com/person/mary-ann-schaub"
		},
		{
			"name": "Moses Ingram",
			"url": "https://www.metacritic.com/person/moses-ingram"
		},
		{
			"name": "Nafessa Williams",
			"url": "https://www.metacritic.com/person/nafessa-williams"
		},
		{
			"name": "Naheem Garcia",
			"url": "https://www.metacritic.com/person/naheem-garcia"
		},
		{
			"name": "Naomi Ackie",
			"url": "https://www.metacritic.com/person/naomi-ackie"
		},
		{
			"name": "Rob Lévesque",
			"url": "https://www.metacritic.com/person/rob-levesque"
		},
		{
			"name": "Stanley Tucci",
			"url": "https://www.metacritic.com/person/stanley-tucci"
		},
		{
			"name": "Tamara Tunie",
			"url": "https://www.metacritic.com/person/tamara-tunie"
		},
		{
			"name": "Tanner Beard",
			"url": "https://www.metacritic.com/person/tanner-beard"
		}
	],
	"summary": "The joyous, emotional and heart-breaking celebration of the life and music of Whitney Houston, the greatest female R&B pop vocalist of all time. Tracking her journey from obscurity to musical super stardom",
	"director": {
		"name": "Kasi Lemmons",
		"url": "https://www.metacritic.com/person/kasi-lemmons"
	},
	"genres": [
		"Biography",
		"Drama",
		"Music"
	],
	"buyLinks": [
		"https://play.google.com/store/movies/details/Whitney_Houston_I_Wanna_Dance_with_Somebody?id=-9kQ6ddektQ.P&hl=en&gl=US&PAffiliateID=1100lHMW&PCamRefID=[subid_value]",
		"https://www.anrdoezrs.net/links/9011673/type/dlg/sid/[subid_value]/https://www.vudu.com/content/movies/details/Whitney-Houston-I-Wanna-Dance-With-Somebody/2231428?"
	],
	"trailer": "https://video.internetvideoarchive.net/video.mp4?cmd=6&fmt=4&customerid=654126&publishedid=113544&e=2208902400&videokbrate=1500&h=b9cde4201f3fe05746a315a21f5fe202"
}
```

### Game Detail

```json
{
	"type": "game",
	"url": "https://www.metacritic.com/game/playstation-5/elden-ring",
	"title": "Elden Ring",
	"publisherName": "Bandai Namco Games",
	"publisherUrl": "https://www.metacritic.com/company/bandai-namco-games",
	"summary": "A New World Created By Hidetaka Miyazaki And George R. R. Martin. ELDEN RING, developed by FromSoftware, Inc. and BANDAI NAMCO Entertainment Inc., is a fantasy action-RPG adventure set within a world created by Hidetaka Miyazaki creator of the influential DARK SOULS video game series; and George R.R. Martin author of The New York Times best-selling fantasy series, A Song of Ice and Fire. Danger and discovery lurk around every corner in FromSoftware's largest game to-date.  Hidetaka Miyazaki, President and Game Director of FromSoftware Inc. Known for directing critically-acclaimed games in beloved franchises including Armored Core, Dark Souls, and Sekiro: Shadows Die Twice.  George R.R. Martin is the #1 New York Times bestselling author of many novels, including the acclaimed series A Song of Ice and Fire - A Game of Thrones, A Clash of Kings, A Storm of Swords, A Feast For Crows, and A Dance with Dragons. As a writer-producer, he has worked on The Twilight Zone, Beauty and the Beast, and various feature films and pilots that were never made.",
	"metascore": 96,
	"userscore": 7.7,
	"genres": [
		"Role-Playing",
		"Action RPG"
	],
	"trailer": "https://mt-rv-v1.gamespot.com/vr/2022/03/04/trailer_eldenring_lore_8000.mp4",
	"awards": [
		"#1 Best PlayStation 5 Game of 2022",
		"#3 Most Discussed PlayStation 5 Game of 2022"
	],
	"platform": [
		"PC",
		"PlayStation 4",
		"Xbox One",
		"Xbox Series X",
		"PlayStation 5"
	]
}
```

### Series Detail

```json
{
	"type": "series",
	"url": "https://www.metacritic.com/tv/the-witcher-blood-origin",
	"title": "The Witcher: Blood Origin",
	"metascore": 45,
	"userscore": 1,
	"distributor": [
		{
			"title": "NETFLIX",
			"url": "https://www.metacritic.com/company/netflix"
		}
	],
	"releaseDate": "December 25, 2022",
	"summary": "The six-part prequel to The Witcher set 1200 years before Geralt of Rivia tells the story of the first Witcher and the events that led to the conjunction of the spheres.",
	"genres": [
		"Drama",
		"Movie/Mini-Series",
		"Action & Adventure",
		"Fantasy",
		"Science Fiction"
	],
	"buyLinks": [
		"https://www.netflix.com/watch/81323602?"
	],
	"trailer": "https://video.internetvideoarchive.net/video.mp4?cmd=6&fmt=4&customerid=654126&publishedid=41256&e=2208902400&videokbrate=1500&h=4e642389faf74cf174271c6cf62a3a03",
	"episodes": [
		{
			"title": "S1:E4. Of Mages, Malice, and Monstrous Mayhem",
			"airDate": "November 30, -0001",
			"url": "https://www.metacritic.com/tv/the-witcher-blood-origin/season-1/episode-4-of-mages-malice-and-monstrous-mayhem"
		},
		{
			"title": "S1:E3. Of Warriors, Wakes, and Wondrous Worlds",
			"airDate": "November 30, -0001",
			"url": "https://www.metacritic.com/tv/the-witcher-blood-origin/season-1/episode-3-of-warriors-wakes-and-wondrous-worlds"
		},
		{
			"title": "S1:E2. Of Dreams, Defiance, and Desperate Deeds",
			"airDate": "November 30, -0001",
			"url": "https://www.metacritic.com/tv/the-witcher-blood-origin/season-1/episode-2-of-dreams-defiance-and-desperate-deeds"
		},
		{
			"title": "S1:E1. Of Ballads, Brawlers, and Bloodied Blades",
			"airDate": "November 30, -0001",
			"url": "https://www.metacritic.com/tv/the-witcher-blood-origin/season-1/episode-1-of-ballads-brawlers-and-bloodied-blades"
		}
	]
}
```

### Person Detail

```json
{
	"type": "person",
	"url": "https://www.metacritic.com/person/robert-downey-jr?page=1",
	"title": "Robert Downey Jr.",
	"categories": [
		"Movies",
		"TV",
		"Games"
	],
	"averageCareerScore": 60,
	"highestMetaScore": {
		"url": "https://www.metacritic.com/movie/richard-iii",
		"title": "Richard III",
		"score": 86
	},
	"lowestMetaScore": {
		"url": "https://www.metacritic.com/movie/johnny-be-good",
		"title": "Johnny Be Good",
		"score": 10
	},
	"shows": [
		{
			"title": "Oppenheimer",
			"url": "https://www.metacritic.com/movie/oppenheimer",
			"year": "Jul 21, 2023",
			"credit": "Lewis Strauss",
			"metascore": "",
			"userscore": 6.1
		},
		{
			"title": "Sr.",
			"url": "https://www.metacritic.com/movie/sr",
			"year": "Nov 18, 2022",
			"credit": "Executive Producer / Producer / Self",
			"metascore": 78,
			"userscore": 6.2
		},
		{
			"title": "Black Widow",
			"url": "https://www.metacritic.com/movie/black-widow",
			"year": "Jul 9, 2021",
			"credit": "Tony Stark",
			"metascore": 67,
			"userscore": 6
		},
		{
			"title": "Dolittle",
			"url": "https://www.metacritic.com/movie/dolittle",
			"year": "Jan 17, 2020",
			"credit": "Executive Producer / Executive Producer / Dr. John Dolittle / Dr. John Dolittle / Dr. John Dolittle / Dr. John Dolittle",
			"metascore": 26,
			"userscore": 3.3
		},
		{
			"title": "Avengers: Endgame",
			"url": "https://www.metacritic.com/movie/avengers-endgame",
			"year": "Apr 26, 2019",
			"credit": "Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 78,
			"userscore": 7.9
		},
		{
			"title": "Avengers: Infinity War",
			"url": "https://www.metacritic.com/movie/avengers-infinity-war",
			"year": "Apr 27, 2018",
			"credit": "Tony Stark / Tony Stark / Tony Stark/Iron Man / Tony Stark/Iron Man / Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 68,
			"userscore": 7.7
		},
		{
			"title": "Spider-Man: Homecoming",
			"url": "https://www.metacritic.com/movie/spider-man-homecoming",
			"year": "Jul 7, 2017",
			"credit": "Tony Stark / Tony Stark / Tony Stark/Iron Man / Tony Stark/Iron Man / Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 73,
			"userscore": ""
		},
		{
			"title": "Captain America: Civil War",
			"url": "https://www.metacritic.com/movie/captain-america-civil-war",
			"year": "May 6, 2016",
			"credit": "Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 75,
			"userscore": 8
		},
		{
			"title": "Avengers: Age of Ultron",
			"url": "https://www.metacritic.com/movie/avengers-age-of-ultron",
			"year": "May 1, 2015",
			"credit": "Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 66,
			"userscore": 7.1
		},
		{
			"title": "The Judge",
			"url": "https://www.metacritic.com/movie/the-judge",
			"year": "Oct 10, 2014",
			"credit": "Executive Producer / Producer / Hank Palmer / Hank Palmer",
			"metascore": 48,
			"userscore": 7.1
		},
		{
			"title": "Chef",
			"url": "https://www.metacritic.com/movie/chef",
			"year": "May 9, 2014",
			"credit": "Cast / Principal Cast / Marvin",
			"metascore": 68,
			"userscore": 7.7
		},
		{
			"title": "Iron Man 3",
			"url": "https://www.metacritic.com/movie/iron-man-3",
			"year": "May 3, 2013",
			"credit": "Tony Stark/Iron Man / Tony Stark / Tony Stark/Iron Man",
			"metascore": 62,
			"userscore": 6.7
		},
		{
			"title": "The Avengers",
			"url": "https://www.metacritic.com/movie/the-avengers-2012",
			"year": "May 4, 2012",
			"credit": "Tony Stark/Iron Man / Tony Stark/Iron Man",
			"metascore": 69,
			"userscore": ""
		},
		{
			"title": "Sherlock Holmes: A Game of Shadows",
			"url": "https://www.metacritic.com/movie/sherlock-holmes-2",
			"year": "Dec 16, 2011",
			"credit": "Sherlock Holmes",
			"metascore": 48,
			"userscore": 7.4
		},
		{
			"title": "Due Date",
			"url": "https://www.metacritic.com/movie/due-date",
			"year": "Nov 5, 2010",
			"credit": "Peter Highman / Peter Highman",
			"metascore": 51,
			"userscore": ""
		},
		{
			"title": "Iron Man 2",
			"url": "https://www.metacritic.com/movie/iron-man-2",
			"year": "May 7, 2010",
			"credit": "Tony Stark",
			"metascore": 57,
			"userscore": 6.4
		},
		{
			"title": "Sherlock Holmes",
			"url": "https://www.metacritic.com/movie/sherlock-holmes",
			"year": "Dec 25, 2009",
			"credit": "Sherlock Holmes",
			"metascore": 57,
			"userscore": 7.4
		},
		{
			"title": "The Soloist",
			"url": "https://www.metacritic.com/movie/the-soloist",
			"year": "Apr 24, 2009",
			"credit": "Steve Lopez",
			"metascore": 61,
			"userscore": 6.9
		},
		{
			"title": "Tropic Thunder",
			"url": "https://www.metacritic.com/movie/tropic-thunder",
			"year": "Aug 13, 2008",
			"credit": "Kirk Lazarus / Kirk Lazarus",
			"metascore": 71,
			"userscore": 6.5
		},
		{
			"title": "Iron Man",
			"url": "https://www.metacritic.com/movie/iron-man",
			"year": "May 2, 2008",
			"credit": "Tony Stark / Tony Stark/Iron Man",
			"metascore": 79,
			"userscore": 8.6
		},
		{
			"title": "Charlie Bartlett",
			"url": "https://www.metacritic.com/movie/charlie-bartlett",
			"year": "Feb 22, 2008",
			"credit": "Principal Nathan Gardner / Principal Nathan Gardner",
			"metascore": 54,
			"userscore": ""
		},
		{
			"title": "Lucky You",
			"url": "https://www.metacritic.com/movie/lucky-you",
			"year": "May 4, 2007",
			"credit": "Telephone Jack",
			"metascore": 49,
			"userscore": 6.6
		},
		{
			"title": "Zodiac",
			"url": "https://www.metacritic.com/movie/zodiac",
			"year": "Mar 2, 2007",
			"credit": "Paul Avery",
			"metascore": 78,
			"userscore": 8.4
		},
		{
			"title": "Fur: An Imaginary Portrait of Diane Arbus",
			"url": "https://www.metacritic.com/movie/fur-an-imaginary-portrait-of-diane-arbus",
			"year": "Nov 10, 2006",
			"credit": "Lionel Sweeney / Lionel Sweeney",
			"metascore": 50,
			"userscore": ""
		},
		{
			"title": "A Guide to Recognizing Your Saints",
			"url": "https://www.metacritic.com/movie/a-guide-to-recognizing-your-saints",
			"year": "Sep 29, 2006",
			"credit": "Co-Producer / Dito",
			"metascore": 67,
			"userscore": 6.9
		},
		{
			"title": "A Scanner Darkly",
			"url": "https://www.metacritic.com/movie/a-scanner-darkly",
			"year": "Jul 7, 2006",
			"credit": "James Barris",
			"metascore": 73,
			"userscore": 7.7
		},
		{
			"title": "The Outsider",
			"url": "https://www.metacritic.com/movie/the-outsider",
			"year": "Apr 7, 2006",
			"credit": "Himself",
			"metascore": 64,
			"userscore": 7.3
		},
		{
			"title": "The Shaggy Dog",
			"url": "https://www.metacritic.com/movie/the-shaggy-dog",
			"year": "Mar 10, 2006",
			"credit": "Dr. Kozak",
			"metascore": 43,
			"userscore": 5.3
		},
		{
			"title": "Game 6",
			"url": "https://www.metacritic.com/movie/game-6",
			"year": "Mar 10, 2006",
			"credit": "Steven Schwimmer",
			"metascore": 56,
			"userscore": 7.1
		},
		{
			"title": "Kiss Kiss Bang Bang",
			"url": "https://www.metacritic.com/movie/kiss-kiss-bang-bang",
			"year": "Oct 21, 2005",
			"credit": "Harry Lockhart",
			"metascore": 72,
			"userscore": 8.5
		},
		{
			"title": "Good Night, and Good Luck.",
			"url": "https://www.metacritic.com/movie/good-night-and-good-luck",
			"year": "Oct 7, 2005",
			"credit": "Joe Wershba",
			"metascore": 80,
			"userscore": 7.2
		},
		{
			"title": "Eros",
			"url": "https://www.metacritic.com/movie/eros",
			"year": "Apr 8, 2005",
			"credit": "Nick Penrose (Segment \"Equilibrium\") / Nick Penrose (Segment \"Equilibrium\")",
			"metascore": 51,
			"userscore": ""
		},
		{
			"title": "Charlie: The Life and Art of Charles Chaplin",
			"url": "https://www.metacritic.com/movie/charlie-the-life-and-art-of-charles-chaplin",
			"year": "Feb 13, 2004",
			"credit": "Himself / Himself",
			"metascore": 80,
			"userscore": ""
		},
		{
			"title": "Gothika",
			"url": "https://www.metacritic.com/movie/gothika",
			"year": "Nov 21, 2003",
			"credit": "Pete Graham",
			"metascore": 38,
			"userscore": 6.5
		},
		{
			"title": "The Singing Detective",
			"url": "https://www.metacritic.com/movie/the-singing-detective",
			"year": "Oct 24, 2003",
			"credit": "Dan Dark / Dan Dark",
			"metascore": 45,
			"userscore": ""
		},
		{
			"title": "Black and White",
			"url": "https://www.metacritic.com/movie/black-and-white",
			"year": "Apr 5, 2000",
			"credit": "Terry Donager",
			"metascore": 47,
			"userscore": 5.6
		},
		{
			"title": "Wonder Boys",
			"url": "https://www.metacritic.com/movie/wonder-boys",
			"year": "Feb 25, 2000",
			"credit": "Terry Crabtree / Terry Crabtree",
			"metascore": 73,
			"userscore": ""
		},
		{
			"title": "Bowfinger",
			"url": "https://www.metacritic.com/movie/bowfinger",
			"year": "Aug 13, 1999",
			"credit": "Jerry Renfro",
			"metascore": 71,
			"userscore": 8.3
		},
		{
			"title": "Two Girls and a Guy",
			"url": "https://www.metacritic.com/movie/two-girls-and-a-guy",
			"year": "Apr 24, 1998",
			"credit": "Blake",
			"metascore": 66,
			"userscore": 7.4
		},
		{
			"title": "U.S. Marshals",
			"url": "https://www.metacritic.com/movie/us-marshals",
			"year": "Mar 6, 1998",
			"credit": "Special Agent John Royce / Special Agent John Royce",
			"metascore": 47,
			"userscore": ""
		},
		{
			"title": "The Gingerbread Man",
			"url": "https://www.metacritic.com/movie/the-gingerbread-man",
			"year": "Jan 23, 1998",
			"credit": "Clyde Pell / Clyde Pell",
			"metascore": 65,
			"userscore": 8
		},
		{
			"title": "Restoration",
			"url": "https://www.metacritic.com/movie/restoration",
			"year": "Feb 2, 1996",
			"credit": "Merivel / Merivel",
			"metascore": 66,
			"userscore": 8.4
		},
		{
			"title": "Richard III",
			"url": "https://www.metacritic.com/movie/richard-iii",
			"year": "Dec 29, 1995",
			"credit": "Lord Rivers",
			"metascore": 86,
			"userscore": ""
		},
		{
			"title": "Home for the Holidays",
			"url": "https://www.metacritic.com/movie/home-for-the-holidays",
			"year": "Nov 3, 1995",
			"credit": "Tommy Larson / Tommy Larson",
			"metascore": 56,
			"userscore": ""
		},
		{
			"title": "Natural Born Killers",
			"url": "https://www.metacritic.com/movie/natural-born-killers",
			"year": "Aug 26, 1994",
			"credit": "Wayne Gale / Wayne Gale",
			"metascore": 74,
			"userscore": 6.4
		},
		{
			"title": "Short Cuts",
			"url": "https://www.metacritic.com/movie/short-cuts",
			"year": "Oct 3, 1993",
			"credit": "Bill Bush",
			"metascore": 81,
			"userscore": 7.4
		},
		{
			"title": "Heart and Souls",
			"url": "https://www.metacritic.com/movie/heart-and-souls",
			"year": "Aug 13, 1993",
			"credit": "Thomas Reilly",
			"metascore": 56,
			"userscore": ""
		},
		{
			"title": "Chaplin",
			"url": "https://www.metacritic.com/movie/chaplin",
			"year": "Jan 8, 1993",
			"credit": "Charles Spencer Chaplin / Charles Spencer Chaplin",
			"metascore": 47,
			"userscore": 7.5
		},
		{
			"title": "Soapdish",
			"url": "https://www.metacritic.com/movie/soapdish",
			"year": "May 31, 1991",
			"credit": "David Seton Barnes / David Seton Barnes",
			"metascore": 65,
			"userscore": 7.4
		},
		{
			"title": "Air America",
			"url": "https://www.metacritic.com/movie/air-america",
			"year": "Aug 10, 1990",
			"credit": "Billy Covington / Billy Covington",
			"metascore": 33,
			"userscore": ""
		},
		{
			"title": "Chances Are",
			"url": "https://www.metacritic.com/movie/chances-are",
			"year": "Mar 10, 1989",
			"credit": "Alex Finch",
			"metascore": 62,
			"userscore": 6.2
		},
		{
			"title": "True Believer",
			"url": "https://www.metacritic.com/movie/true-believer",
			"year": "Feb 17, 1989",
			"credit": "Roger Baron",
			"metascore": 64,
			"userscore": ""
		},
		{
			"title": "Johnny Be Good",
			"url": "https://www.metacritic.com/movie/johnny-be-good",
			"year": "Mar 25, 1988",
			"credit": "Leo Wiggins",
			"metascore": 10,
			"userscore": ""
		},
		{
			"title": "Less Than Zero",
			"url": "https://www.metacritic.com/movie/less-than-zero",
			"year": "Nov 6, 1987",
			"credit": "Julian",
			"metascore": 48,
			"userscore": 7.5
		},
		{
			"title": "The Pick-up Artist",
			"url": "https://www.metacritic.com/movie/the-pick-up-artist",
			"year": "Sep 18, 1987",
			"credit": "Jack Jericho",
			"metascore": 47,
			"userscore": 7.5
		},
		{
			"title": "Back to School",
			"url": "https://www.metacritic.com/movie/back-to-school",
			"year": "Jun 13, 1986",
			"credit": "Derek Lutz / Derek Lutz / Derek Lutz",
			"metascore": 68,
			"userscore": ""
		},
		{
			"title": "Weird Science",
			"url": "https://www.metacritic.com/movie/weird-science",
			"year": "Aug 2, 1985",
			"credit": "Ian",
			"metascore": 46,
			"userscore": 8.3
		},
		{
			"title": "Tuff Turf",
			"url": "https://www.metacritic.com/movie/tuff-turf",
			"year": "Jan 11, 1985",
			"credit": "Jimmy Parker",
			"metascore": 37,
			"userscore": ""
		},
		{
			"title": "Firstborn",
			"url": "https://www.metacritic.com/movie/firstborn",
			"year": "Oct 26, 1984",
			"credit": "Lee",
			"metascore": 56,
			"userscore": ""
		}
	]
}
```

### Company Detail

```json
{
	"type": "company",
	"url": "https://www.metacritic.com/company/rca?page=8",
	"title": "RCA",
	"categories": [
		"Movies",
		"Music"
	],
	"averageCareerScore": 70,
	"highestMetaScore": {
		"url": "https://www.metacritic.com/music/black-messiah/dangelo",
		"title": "Black Messiah",
		"score": 95
	},
	"lowestMetaScore": {
		"url": "https://www.metacritic.com/music/fortune/chris-brown",
		"title": "Fortune",
		"score": 38
	},
	"products": [
		{
			"title": "S.O.S.",
			"metascore": 90,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/sos/sza",
			"year": "Dec 9, 2022"
		},
		{
			"title": "The Family",
			"metascore": 79,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/family/brockhampton",
			"year": "Nov 18, 2022"
		},
		{
			"title": "The Hardest Part",
			"metascore": 88,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/the-hardest-part/noah-cyrus",
			"year": "Sep 16, 2022"
		},
		{
			"title": "You Still Here, Ho?",
			"metascore": 76,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/you-still-here-ho/flo-milli",
			"year": "Jul 20, 2022"
		},
		{
			"title": "I Used to Think I Could Fly",
			"metascore": 75,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/i-used-to-think-i-could-fly/tate-mcrae",
			"year": "May 27, 2022"
		},
		{
			"title": "Who Cares?",
			"metascore": 70,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/who-cares/rex-orange-county",
			"year": "Mar 11, 2022"
		},
		{
			"title": "KEYS",
			"metascore": 65,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/keys/alicia-keys",
			"year": "Dec 10, 2021"
		},
		{
			"title": "Scenic Drive (The Tape)",
			"metascore": 58,
			"userscore": "",
			"url": "https://www.metacritic.com/music/scenic-drive-the-tape/khalid",
			"year": "Dec 3, 2021"
		},
		{
			"title": "And Then Life Was Beautiful",
			"metascore": 85,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/and-then-life-was-beautiful/nao",
			"year": "Sep 24, 2021"
		},
		{
			"title": "Dawn",
			"metascore": 84,
			"userscore": 9.6,
			"url": "https://www.metacritic.com/music/dawn/yebba",
			"year": "Sep 10, 2021"
		},
		{
			"title": "Saturday Night, Sunday Morning",
			"metascore": 56,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/saturday-night-sunday-morning/jake-bugg",
			"year": "Aug 20, 2021"
		},
		{
			"title": "Independence Day",
			"metascore": 76,
			"userscore": "",
			"url": "https://www.metacritic.com/music/independence-day/fredo",
			"year": "Aug 6, 2021"
		},
		{
			"title": "Take the Sadness Out of Saturday Night",
			"metascore": 71,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/take-the-sadness-out-of-saturday-night/bleachers",
			"year": "Jul 30, 2021"
		},
		{
			"title": "Back Of My Mind",
			"metascore": 75,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/back-of-my-mind/her",
			"year": "Jun 18, 2021"
		},
		{
			"title": "Blue Weekend",
			"metascore": 91,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/blue-weekend/wolf-alice",
			"year": "Jun 4, 2021"
		},
		{
			"title": "ROADRUNNER: NEW LIGHT, NEW MACHINE",
			"metascore": 79,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/roadrunner-new-light-new-machine/brockhampton",
			"year": "Apr 9, 2021"
		},
		{
			"title": "When You See Yourself",
			"metascore": 69,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/when-you-see-yourself/kings-of-leon",
			"year": "Mar 5, 2021"
		},
		{
			"title": "Judas and the Black Messiah: The Inspired Album",
			"metascore": 70,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/judas-and-the-black-messiah-the-inspired-album/original-music-soundtrack",
			"year": "Feb 12, 2021"
		},
		{
			"title": "Medicine at Midnight",
			"metascore": 75,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/medicine-at-midnight/foo-fighters",
			"year": "Feb 5, 2021"
		},
		{
			"title": "Nobody Is Listening",
			"metascore": 63,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/nobody-is-listening/zayn",
			"year": "Jan 15, 2021"
		},
		{
			"title": "Heaux Tales",
			"metascore": 81,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/heaux-tales/jazmine-sullivan",
			"year": "Jan 8, 2021"
		},
		{
			"title": "Plastic Hearts",
			"metascore": 75,
			"userscore": 9,
			"url": "https://www.metacritic.com/music/plastic-hearts/miley-cyrus",
			"year": "Nov 27, 2020"
		},
		{
			"title": "Confetti",
			"metascore": 74,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/confetti/little-mix",
			"year": "Nov 6, 2020"
		},
		{
			"title": "POST HUMAN: SURVIVAL HORROR [EP]",
			"metascore": 82,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/post-human-survival-horror-ep/bring-me-the-horizon",
			"year": "Oct 30, 2020"
		},
		{
			"title": "Moral Panic",
			"metascore": 68,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/moral-panic/nothing-but-thieves",
			"year": "Oct 23, 2020"
		},
		{
			"title": "Alicia",
			"metascore": 77,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/alicia/alicia-keys",
			"year": "Sep 18, 2020"
		},
		{
			"title": "Monovision",
			"metascore": 80,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/monovision/ray-lamontagne",
			"year": "Jun 26, 2020"
		},
		{
			"title": "The New Abnormal",
			"metascore": 75,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/the-new-abnormal/the-strokes",
			"year": "Apr 10, 2020"
		},
		{
			"title": "3.15.20",
			"metascore": 83,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/31520/childish-gambino",
			"year": "Mar 22, 2020"
		},
		{
			"title": "High Road",
			"metascore": 73,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/high-road/kesha",
			"year": "Jan 31, 2020"
		},
		{
			"title": "Treat Myself",
			"metascore": 51,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/treat-myself/meghan-trainor",
			"year": "Jan 31, 2020"
		},
		{
			"title": "Bubba",
			"metascore": 82,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/bubba/kaytranada",
			"year": "Dec 13, 2019"
		},
		{
			"title": "Get the Money",
			"metascore": 66,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/get-the-money/taylor-hawkins-the-coattail-riders",
			"year": "Nov 8, 2019"
		},
		{
			"title": "PONY",
			"metascore": 76,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/pony/rex-orange-county",
			"year": "Oct 25, 2019"
		},
		{
			"title": "Surviving",
			"metascore": 78,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/surviving/jimmy-eat-world",
			"year": "Oct 18, 2019"
		},
		{
			"title": "Saves the World",
			"metascore": 82,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/saves-the-world/muna",
			"year": "Sep 6, 2019"
		},
		{
			"title": "Fear Inoculum",
			"metascore": 81,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/fear-inoculum/tool",
			"year": "Aug 30, 2019"
		},
		{
			"title": "Country Squire",
			"metascore": 85,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/country-squire/tyler-childers",
			"year": "Aug 2, 2019"
		},
		{
			"title": "Brandon Banks",
			"metascore": 84,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/brandon-banks/maxo-kream",
			"year": "Jul 18, 2019"
		},
		{
			"title": "Bandana",
			"metascore": 88,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/bandana/freddie-gibbs",
			"year": "Jun 28, 2019"
		},
		{
			"title": "Late Night Feelings",
			"metascore": 75,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/late-night-feelings/mark-ronson",
			"year": "Jun 21, 2019"
		},
		{
			"title": "Diaspora",
			"metascore": 82,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/diaspora/goldlink",
			"year": "Jun 12, 2019"
		},
		{
			"title": "She Is Coming [EP]",
			"metascore": 64,
			"userscore": 8.8,
			"url": "https://www.metacritic.com/music/she-is-coming-ep/miley-cyrus",
			"year": "May 31, 2019"
		},
		{
			"title": "Hurts 2B Human",
			"metascore": 71,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/hurts-2b-human/p!nk",
			"year": "Apr 26, 2019"
		},
		{
			"title": "ARIZONA BABY",
			"metascore": 76,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/arizona-baby/kevin-abstract",
			"year": "Apr 25, 2019"
		},
		{
			"title": "Free Spirit",
			"metascore": 58,
			"userscore": 6.5,
			"url": "https://www.metacritic.com/music/free-spirit/khalid",
			"year": "Apr 5, 2019"
		},
		{
			"title": "Ulfilas' Alphabet",
			"metascore": 81,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/ulfilas-alphabet/sundara-karma",
			"year": "Mar 8, 2019"
		},
		{
			"title": "Third Avenue",
			"metascore": 68,
			"userscore": "",
			"url": "https://www.metacritic.com/music/third-avenue/fredo",
			"year": "Feb 8, 2019"
		},
		{
			"title": "Amo",
			"metascore": 85,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/amo/bring-me-the-horizon",
			"year": "Jan 25, 2019"
		},
		{
			"title": "DNA",
			"metascore": 67,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/dna/backstreet-boys",
			"year": "Jan 25, 2019"
		},
		{
			"title": "Future Hndrxx Presents: The WIZRD",
			"metascore": 70,
			"userscore": 6.3,
			"url": "https://www.metacritic.com/music/future-hndrxx-presents-the-wizrd/future",
			"year": "Jan 18, 2019"
		},
		{
			"title": "Icarus Falls",
			"metascore": 70,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/icarus-falls/zayn",
			"year": "Dec 14, 2018"
		},
		{
			"title": "Caution",
			"metascore": 82,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/caution/mariah-carey",
			"year": "Nov 16, 2018"
		},
		{
			"title": "Come Over When You’re Sober, Pt. 2",
			"metascore": 79,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/come-over-when-youre-sober-pt-2/lil-peep",
			"year": "Nov 9, 2018"
		},
		{
			"title": "Interstate Gospel",
			"metascore": 85,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/interstate-gospel/pistol-annies",
			"year": "Nov 2, 2018"
		},
		{
			"title": "Saturn",
			"metascore": 83,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/saturn/nao",
			"year": "Oct 26, 2018"
		},
		{
			"title": "Christmas Is Here!",
			"metascore": 66,
			"userscore": 6.6,
			"url": "https://www.metacritic.com/music/christmas-is-here!/pentatonix",
			"year": "Oct 26, 2018"
		},
		{
			"title": "Suncity [EP]",
			"metascore": 68,
			"userscore": 6.5,
			"url": "https://www.metacritic.com/music/suncity-ep/khalid",
			"year": "Oct 19, 2018"
		},
		{
			"title": "Shake the Spirit",
			"metascore": 76,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/shake-the-spirit/elle-king",
			"year": "Oct 19, 2018"
		},
		{
			"title": "Iridescence",
			"metascore": 85,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/iridescence/brockhampton",
			"year": "Sep 21, 2018"
		},
		{
			"title": "Harlan & Alondra",
			"metascore": 83,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/harlan-alondra/buddy",
			"year": "Jul 20, 2018"
		},
		{
			"title": "Liberation",
			"metascore": 71,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/liberation/christina-aguilera",
			"year": "Jun 15, 2018"
		},
		{
			"title": "The Blues Is Alive and Well",
			"metascore": 66,
			"userscore": "",
			"url": "https://www.metacritic.com/music/the-blues-is-alive-and-well/buddy-guy",
			"year": "Jun 15, 2018"
		},
		{
			"title": "so sad so sexy",
			"metascore": 71,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/so-sad-so-sexy/lykke-li",
			"year": "Jun 8, 2018"
		},
		{
			"title": "Come Tomorrow",
			"metascore": 71,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/come-tomorrow/dave-matthews-band",
			"year": "Jun 8, 2018"
		},
		{
			"title": "Part of the Light",
			"metascore": 74,
			"userscore": "",
			"url": "https://www.metacritic.com/music/part-of-the-light/ray-lamontagne",
			"year": "May 18, 2018"
		},
		{
			"title": "Virtue",
			"metascore": 68,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/virtue/the-voidz",
			"year": "Mar 30, 2018"
		},
		{
			"title": "Snoop Dogg Presents Bible of Love",
			"metascore": 54,
			"userscore": 6.4,
			"url": "https://www.metacritic.com/music/snoop-dogg-presents-bible-of-love/snoop-dogg",
			"year": "Mar 16, 2018"
		},
		{
			"title": "Man of the Woods",
			"metascore": 55,
			"userscore": 6.1,
			"url": "https://www.metacritic.com/music/man-of-the-woods/justin-timberlake",
			"year": "Feb 2, 2018"
		},
		{
			"title": "The Beautiful & Damned",
			"metascore": 59,
			"userscore": 6.1,
			"url": "https://www.metacritic.com/music/the-beautiful-damned/g-eazy",
			"year": "Dec 15, 2017"
		},
		{
			"title": "War & Leisure",
			"metascore": 81,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/war-leisure/miguel",
			"year": "Dec 1, 2017"
		},
		{
			"title": "The Architect",
			"metascore": 72,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/the-architect/paloma-faith",
			"year": "Nov 17, 2017"
		},
		{
			"title": "Super Slimey [Mixtape]",
			"metascore": 66,
			"userscore": 7,
			"url": "https://www.metacritic.com/music/super-slimey-mixtape/future",
			"year": "Oct 20, 2017"
		},
		{
			"title": "Beautiful Trauma",
			"metascore": 62,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/beautiful-trauma/p!nk",
			"year": "Oct 13, 2017"
		},
		{
			"title": "Visions of a Life",
			"metascore": 81,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/visions-of-a-life/wolf-alice",
			"year": "Sep 29, 2017"
		},
		{
			"title": "Younger Now",
			"metascore": 58,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/younger-now/miley-cyrus",
			"year": "Sep 29, 2017"
		},
		{
			"title": "Concrete and Gold",
			"metascore": 72,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/concrete-and-gold/foo-fighters",
			"year": "Sep 15, 2017"
		},
		{
			"title": "Still Striving [Mixtape]",
			"metascore": 65,
			"userscore": 6.9,
			"url": "https://www.metacritic.com/music/still-striving-mixtape/aap-ferg",
			"year": "Aug 25, 2017"
		},
		{
			"title": "Cozy Tapes, Vol. 2: Too Cozy",
			"metascore": 70,
			"userscore": 5.8,
			"url": "https://www.metacritic.com/music/cozy-tapes-vol-2-too-cozy/aap-mob",
			"year": "Aug 25, 2017"
		},
		{
			"title": "Painted Ruins",
			"metascore": 82,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/painted-ruins/grizzly-bear",
			"year": "Aug 18, 2017"
		},
		{
			"title": "Rainbow",
			"metascore": 81,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/rainbow/kesha",
			"year": "Aug 11, 2017"
		},
		{
			"title": "A Boy From Tupelo: The Complete 1953-1955 Recordings [Box Set]",
			"metascore": 95,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/a-boy-from-tupelo-the-complete-1953-1955-recordings-box-set/elvis-presley",
			"year": "Jul 28, 2017"
		},
		{
			"title": "Unpeeled [Live]",
			"metascore": 72,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/unpeeled-live/cage-the-elephant",
			"year": "Jul 28, 2017"
		},
		{
			"title": "CTRL",
			"metascore": 86,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/ctrl/sza",
			"year": "Jun 9, 2017"
		},
		{
			"title": "Gone Now",
			"metascore": 71,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/gone-now/bleachers",
			"year": "Jun 2, 2017"
		},
		{
			"title": "True to Self",
			"metascore": 63,
			"userscore": 6.3,
			"url": "https://www.metacritic.com/music/true-to-self/bryson-tiller",
			"year": "May 26, 2017"
		},
		{
			"title": "At What Cost",
			"metascore": 71,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/at-what-cost/goldlink",
			"year": "Mar 24, 2017"
		},
		{
			"title": "Climate Change",
			"metascore": 64,
			"userscore": 4.4,
			"url": "https://www.metacritic.com/music/climate-change/pitbull",
			"year": "Mar 17, 2017"
		},
		{
			"title": "Here",
			"metascore": 76,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/here/alicia-keys",
			"year": "Nov 4, 2016"
		},
		{
			"title": "Nightride [Mixtape]",
			"metascore": 75,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/nightride-mixtape/tinashe",
			"year": "Nov 4, 2016"
		},
		{
			"title": "Cozy Tapes, Vol. 1: Friends",
			"metascore": 78,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/cozy-tapes-vol-1-friends/aap-mob",
			"year": "Oct 31, 2016"
		},
		{
			"title": "Integrity Blues",
			"metascore": 76,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/integrity-blues/jimmy-eat-world",
			"year": "Oct 21, 2016"
		},
		{
			"title": "Walls",
			"metascore": 62,
			"userscore": 6.7,
			"url": "https://www.metacritic.com/music/walls/kings-of-leon",
			"year": "Oct 14, 2016"
		},
		{
			"title": "Hard II Love",
			"metascore": 74,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/hard-ii-love/usher",
			"year": "Sep 16, 2016"
		},
		{
			"title": "Glory",
			"metascore": 71,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/glory/britney-spears",
			"year": "Aug 26, 2016"
		},
		{
			"title": "For All We Know",
			"metascore": 82,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/for-all-we-know/nao",
			"year": "Jul 29, 2016"
		},
		{
			"title": "The Dreaming Room",
			"metascore": 82,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/the-dreaming-room/laura-mvula",
			"year": "Jun 17, 2016"
		},
		{
			"title": "Wrong Crowd",
			"metascore": 72,
			"userscore": 8.8,
			"url": "https://www.metacritic.com/music/wrong-crowd/tom-odell",
			"year": "Jun 10, 2016"
		},
		{
			"title": "Mind of Mine",
			"metascore": 69,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/mind-of-mine/zayn",
			"year": "Mar 25, 2016"
		},
		{
			"title": "Ouroboros",
			"metascore": 80,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/ouroboros/ray-lamontagne",
			"year": "Mar 4, 2016"
		},
		{
			"title": "This Is Acting",
			"metascore": 67,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/this-is-acting/sia",
			"year": "Jan 29, 2016"
		},
		{
			"title": "Wildfire",
			"metascore": 52,
			"userscore": 5.6,
			"url": "https://www.metacritic.com/music/wildfire/rachel-platten",
			"year": "Jan 1, 2016"
		},
		{
			"title": "Tell Me I'm Pretty",
			"metascore": 73,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/tell-me-im-pretty/cage-the-elephant",
			"year": "Dec 18, 2015"
		},
		{
			"title": "Royalty",
			"metascore": 59,
			"userscore": 6.7,
			"url": "https://www.metacritic.com/music/royalty/chris-brown",
			"year": "Dec 18, 2015"
		},
		{
			"title": "The Buffet",
			"metascore": 60,
			"userscore": 5.3,
			"url": "https://www.metacritic.com/music/the-buffet/r-kelly",
			"year": "Dec 11, 2015"
		},
		{
			"title": "When It's Dark Out",
			"metascore": 74,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/when-its-dark-out/g-eazy",
			"year": "Dec 4, 2015"
		},
		{
			"title": "Saint Cecilia EP",
			"metascore": 76,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/saint-cecilia-ep/foo-fighters",
			"year": "Nov 23, 2015"
		},
		{
			"title": "Alone in the Universe",
			"metascore": 75,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/alone-in-the-universe/jeff-lynnes-elo",
			"year": "Nov 13, 2015"
		},
		{
			"title": "Electronica, Vol. 1: The Time Machine",
			"metascore": 63,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/electronica-vol-1-the-time-machine/jean-michel-jarre",
			"year": "Oct 16, 2015"
		},
		{
			"title": "Mothers",
			"metascore": 79,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/mothers/swim-deep",
			"year": "Sep 18, 2015"
		},
		{
			"title": "That's the Spirit",
			"metascore": 88,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/thats-the-spirit/bring-me-the-horizon",
			"year": "Sep 11, 2015"
		},
		{
			"title": "Venom",
			"metascore": 58,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/venom/bullet-for-my-valentine",
			"year": "Aug 14, 2015"
		},
		{
			"title": "Born to Play Guitar",
			"metascore": 76,
			"userscore": "",
			"url": "https://www.metacritic.com/music/born-to-play-guitar/buddy-guy",
			"year": "Jul 31, 2015"
		},
		{
			"title": "Double Vision",
			"metascore": 71,
			"userscore": 6.2,
			"url": "https://www.metacritic.com/music/double-vision/prince-royce",
			"year": "Jul 24, 2015"
		},
		{
			"title": "How Does It Feel",
			"metascore": 62,
			"userscore": 7.1,
			"url": "https://www.metacritic.com/music/how-does-it-feel/ms-mr",
			"year": "Jul 17, 2015"
		},
		{
			"title": "Nina Revisited: A Tribute to Nina Simone",
			"metascore": 70,
			"userscore": "",
			"url": "https://www.metacritic.com/music/nina-revisited-a-tribute-to-nina-simone/various-artists",
			"year": "Jul 10, 2015"
		},
		{
			"title": "Wildheart",
			"metascore": 84,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/wildheart/miguel",
			"year": "Jun 29, 2015"
		},
		{
			"title": "My Love Is Cool",
			"metascore": 78,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/my-love-is-cool/wolf-alice",
			"year": "Jun 23, 2015"
		},
		{
			"title": "Get to Heaven",
			"metascore": 80,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/get-to-heaven/everything-everything",
			"year": "Jun 22, 2015"
		},
		{
			"title": "Déjà-Vu",
			"metascore": 54,
			"userscore": 6.2,
			"url": "https://www.metacritic.com/music/dejs-vu/giorgio-moroder",
			"year": "Jun 12, 2015"
		},
		{
			"title": "At.Long.Last.A$AP",
			"metascore": 76,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/atlonglastaap/aap-rocky",
			"year": "May 26, 2015"
		},
		{
			"title": "Hollywood: A Story of a Dozen Roses",
			"metascore": 53,
			"userscore": 7,
			"url": "https://www.metacritic.com/music/hollywood-a-story-of-a-dozen-roses/jamie-foxx",
			"year": "May 18, 2015"
		},
		{
			"title": "Bush",
			"metascore": 69,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/bush/snoop-dogg",
			"year": "May 12, 2015"
		},
		{
			"title": "The  Past, The Present, The Future",
			"metascore": 69,
			"userscore": "",
			"url": "https://www.metacritic.com/music/the-past-the-present-the-future/jodeci",
			"year": "Mar 31, 2015"
		},
		{
			"title": "Coming Up for Air",
			"metascore": 51,
			"userscore": 3.9,
			"url": "https://www.metacritic.com/music/coming-up-for-air/kodaline",
			"year": "Mar 24, 2015"
		},
		{
			"title": "Duets: Re-Working the Catalogue",
			"metascore": 65,
			"userscore": "",
			"url": "https://www.metacritic.com/music/duets-re-working-the-catalogue/van-morrison",
			"year": "Mar 23, 2015"
		},
		{
			"title": "Piece by Piece",
			"metascore": 63,
			"userscore": 5.6,
			"url": "https://www.metacritic.com/music/piece-by-piece/kelly-clarkson",
			"year": "Mar 3, 2015"
		},
		{
			"title": "Fan of a Fan: The Album",
			"metascore": 46,
			"userscore": 4.6,
			"url": "https://www.metacritic.com/music/fan-of-a-fan-the-album/chris-brown",
			"year": "Feb 24, 2015"
		},
		{
			"title": "Full Speed",
			"metascore": 55,
			"userscore": 4.8,
			"url": "https://www.metacritic.com/music/full-speed/kid-ink",
			"year": "Feb 3, 2015"
		},
		{
			"title": "Time",
			"metascore": 59,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/time/mikky-ekko",
			"year": "Jan 20, 2015"
		},
		{
			"title": "Uptown Special",
			"metascore": 73,
			"userscore": 6.4,
			"url": "https://www.metacritic.com/music/uptown-special/mark-ronson",
			"year": "Jan 13, 2015"
		},
		{
			"title": "Reality Show",
			"metascore": 85,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/reality-show/jazmine-sullivan",
			"year": "Jan 13, 2015"
		},
		{
			"title": "Black Messiah",
			"metascore": 95,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/black-messiah/dangelo",
			"year": "Dec 15, 2014"
		},
		{
			"title": "Man Against Machine",
			"metascore": 68,
			"userscore": 6.6,
			"url": "https://www.metacritic.com/music/man-against-machine/garth-brooks",
			"year": "Nov 10, 2014"
		},
		{
			"title": "Sings the Great Diva Classics",
			"metascore": 66,
			"userscore": 6.6,
			"url": "https://www.metacritic.com/music/sings-the-great-diva-classics/aretha-franklin",
			"year": "Oct 21, 2014"
		},
		{
			"title": "Aquarius",
			"metascore": 80,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/aquarius/tinashe",
			"year": "Oct 7, 2014"
		},
		{
			"title": "JHUD",
			"metascore": 68,
			"userscore": 6.3,
			"url": "https://www.metacritic.com/music/jhud/jennifer-hudson",
			"year": "Sep 23, 2014"
		},
		{
			"title": "X",
			"metascore": 63,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/x/chris-brown",
			"year": "Sep 16, 2014"
		},
		{
			"title": "Sparks",
			"metascore": 70,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/sparks/imogen-heap",
			"year": "Aug 19, 2014"
		},
		{
			"title": "Strange Desire",
			"metascore": 68,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/strange-desire/bleachers",
			"year": "Jul 15, 2014"
		},
		{
			"title": "Mandatory Fun",
			"metascore": 77,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/mandatory-fun/weird-al-yankovic",
			"year": "Jul 15, 2014"
		},
		{
			"title": "1000 Forms of Fear",
			"metascore": 76,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/1000-forms-of-fear/sia",
			"year": "Jul 8, 2014"
		},
		{
			"title": "Platinum",
			"metascore": 86,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/platinum/miranda-lambert",
			"year": "Jun 3, 2014"
		},
		{
			"title": "Corazón",
			"metascore": 60,
			"userscore": 2.3,
			"url": "https://www.metacritic.com/music/corazon/santana",
			"year": "May 6, 2014"
		},
		{
			"title": "Supernova",
			"metascore": 78,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/supernova/ray-lamontagne",
			"year": "Apr 29, 2014"
		},
		{
			"title": "Shakira",
			"metascore": 69,
			"userscore": 6,
			"url": "https://www.metacritic.com/music/shakira/shakira",
			"year": "Mar 25, 2014"
		},
		{
			"title": "About Last Night",
			"metascore": 70,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/about-last-night/sleeper-agent",
			"year": "Mar 25, 2014"
		},
		{
			"title": "No Mythologies to Follow",
			"metascore": 76,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/no-mythologies-to-follow/m",
			"year": "Mar 11, 2014"
		},
		{
			"title": "Slow Me Down",
			"metascore": 87,
			"userscore": 7.1,
			"url": "https://www.metacritic.com/music/slow-me-down/sara-evans",
			"year": "Mar 11, 2014"
		},
		{
			"title": "A Perfect Contradiction",
			"metascore": 66,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/a-perfect-contradiction/paloma-faith",
			"year": "Mar 10, 2014"
		},
		{
			"title": "My Own Lane",
			"metascore": 65,
			"userscore": 6,
			"url": "https://www.metacritic.com/music/my-own-lane/kid-ink",
			"year": "Jan 7, 2014"
		},
		{
			"title": "Black Panties",
			"metascore": 61,
			"userscore": 4.1,
			"url": "https://www.metacritic.com/music/black-panties/r-kelly",
			"year": "Dec 10, 2013"
		},
		{
			"title": "Britney Jean",
			"metascore": 50,
			"userscore": 6,
			"url": "https://www.metacritic.com/music/britney-jean/britney-spears",
			"year": "Dec 3, 2013"
		},
		{
			"title": "Days of Gold",
			"metascore": 71,
			"userscore": "",
			"url": "https://www.metacritic.com/music/days-of-gold/jake-owen",
			"year": "Dec 3, 2013"
		},
		{
			"title": "Baptized",
			"metascore": 53,
			"userscore": 2.6,
			"url": "https://www.metacritic.com/music/baptized/daughtry",
			"year": "Nov 19, 2013"
		},
		{
			"title": "Wrapped in Red",
			"metascore": 73,
			"userscore": 5.8,
			"url": "https://www.metacritic.com/music/wrapped-in-red/kelly-clarkson",
			"year": "Oct 29, 2013"
		},
		{
			"title": "In a Perfect World",
			"metascore": 47,
			"userscore": 6.8,
			"url": "https://www.metacritic.com/music/in-a-perfect-world/kodaline",
			"year": "Oct 8, 2013"
		},
		{
			"title": "Bangerz",
			"metascore": 61,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/bangerz/miley-cyrus",
			"year": "Oct 8, 2013"
		},
		{
			"title": "Melophobia",
			"metascore": 73,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/melophobia/cage-the-elephant",
			"year": "Oct 8, 2013"
		},
		{
			"title": "The 20/20 Experience 2 of 2",
			"metascore": 60,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/the-2020-experience-2-of-2/justin-timberlake",
			"year": "Sep 30, 2013"
		},
		{
			"title": "Mechanical Bull",
			"metascore": 70,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/mechanical-bull/kings-of-leon",
			"year": "Sep 24, 2013"
		},
		{
			"title": "A.M.",
			"metascore": 79,
			"userscore": "",
			"url": "https://www.metacritic.com/music/am/chris-young",
			"year": "Sep 17, 2013"
		},
		{
			"title": "Trap Lord",
			"metascore": 72,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/trap-lord/aap-ferg",
			"year": "Aug 20, 2013"
		},
		{
			"title": "Elvis at Stax",
			"metascore": 79,
			"userscore": 7,
			"url": "https://www.metacritic.com/music/elvis-at-stax/elvis-presley",
			"year": "Aug 6, 2013"
		},
		{
			"title": "Where the Heaven Are We",
			"metascore": 72,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/where-the-heaven-are-we/swim-deep",
			"year": "Aug 5, 2013"
		},
		{
			"title": "Rhythm & Blues",
			"metascore": 72,
			"userscore": "",
			"url": "https://www.metacritic.com/music/rhythm-blues/buddy-guy",
			"year": "Jul 30, 2013"
		},
		{
			"title": "The RCA Albums Collection",
			"metascore": 87,
			"userscore": "",
			"url": "https://www.metacritic.com/music/the-rca-albums-collection/harry-nilsson",
			"year": "Jul 30, 2013"
		},
		{
			"title": "Born Sinner",
			"metascore": 71,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/born-sinner/j-cole",
			"year": "Jun 18, 2013"
		},
		{
			"title": "Damage",
			"metascore": 71,
			"userscore": 6.3,
			"url": "https://www.metacritic.com/music/damage/jimmy-eat-world",
			"year": "Jun 11, 2013"
		},
		{
			"title": "Secondhand Rapture",
			"metascore": 60,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/secondhand-rapture/ms-mr",
			"year": "May 14, 2013"
		},
		{
			"title": "Annie Up",
			"metascore": 87,
			"userscore": 5.1,
			"url": "https://www.metacritic.com/music/annie-up/pistol-annies",
			"year": "May 7, 2013"
		},
		{
			"title": "Reincarnated",
			"metascore": 53,
			"userscore": 5.4,
			"url": "https://www.metacritic.com/music/reincarnated/snoop-lion",
			"year": "Apr 23, 2013"
		},
		{
			"title": "Girl Who Got Away",
			"metascore": 59,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/girl-who-got-away/dido",
			"year": "Mar 26, 2013"
		},
		{
			"title": "Comedown Machine",
			"metascore": 68,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/comedown-machine/the-strokes",
			"year": "Mar 26, 2013"
		},
		{
			"title": "The 20/20 Experience",
			"metascore": 75,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/the-2020-experience/justin-timberlake",
			"year": "Mar 19, 2013"
		},
		{
			"title": "Sound City: Real to Reel",
			"metascore": 65,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/sound-city-real-to-reel/original-soundtrack",
			"year": "Mar 12, 2013"
		},
		{
			"title": "Temper Temper",
			"metascore": 60,
			"userscore": 5.8,
			"url": "https://www.metacritic.com/music/temper-temper/bullet-for-my-valentine",
			"year": "Feb 12, 2013"
		},
		{
			"title": "Long.Live.A$AP",
			"metascore": 75,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/longliveaap/aap-rocky",
			"year": "Jan 15, 2013"
		},
		{
			"title": "Arc",
			"metascore": 79,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/arc/everything-everything",
			"year": "Jan 14, 2013"
		},
		{
			"title": "Warrior",
			"metascore": 71,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/warrior/keha",
			"year": "Dec 4, 2012"
		},
		{
			"title": "Fall to Grace",
			"metascore": 62,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/fall-to-grace/paloma-faith",
			"year": "Dec 4, 2012"
		},
		{
			"title": "Girl on Fire",
			"metascore": 69,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/girl-on-fire/alicia-keys",
			"year": "Nov 27, 2012"
		},
		{
			"title": "Global Warming",
			"metascore": 63,
			"userscore": 4.2,
			"url": "https://www.metacritic.com/music/global-warming/pitbull",
			"year": "Nov 19, 2012"
		},
		{
			"title": "Lotus",
			"metascore": 56,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/lotus/christina-aguilera",
			"year": "Nov 13, 2012"
		},
		{
			"title": "Two Eleven",
			"metascore": 77,
			"userscore": 5.1,
			"url": "https://www.metacritic.com/music/two-eleven/brandy",
			"year": "Oct 16, 2012"
		},
		{
			"title": "Kaleidoscope Dream",
			"metascore": 86,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/kaleidoscope-dream/miguel",
			"year": "Oct 2, 2012"
		},
		{
			"title": "The  Truth About Love",
			"metascore": 77,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/the-truth-about-love/p!nk",
			"year": "Sep 18, 2012"
		},
		{
			"title": "Away from the World",
			"metascore": 77,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/away-from-the-world/dave-matthews-band",
			"year": "Sep 11, 2012"
		},
		{
			"title": "Fortune",
			"metascore": 38,
			"userscore": 3.4,
			"url": "https://www.metacritic.com/music/fortune/chris-brown",
			"year": "Jul 3, 2012"
		},
		{
			"title": "Write Me Back",
			"metascore": 73,
			"userscore": 7.2,
			"url": "https://www.metacritic.com/music/write-me-back/r-kelly",
			"year": "Jun 26, 2012"
		},
		{
			"title": "Walk the Moon",
			"metascore": 67,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/walk-the-moon/walk-the-moon",
			"year": "Jun 19, 2012"
		},
		{
			"title": "Looking 4 Myself",
			"metascore": 75,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/looking-4-myself/usher",
			"year": "Jun 12, 2012"
		},
		{
			"title": "Trespassing",
			"metascore": 66,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/trespassing/adam-lambert",
			"year": "May 15, 2012"
		},
		{
			"title": "Back to Love",
			"metascore": 82,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/back-to-love/anthony-hamilton",
			"year": "Dec 13, 2011"
		},
		{
			"title": "rEvolver",
			"metascore": 56,
			"userscore": 3.9,
			"url": "https://www.metacritic.com/music/revolver/t-pain",
			"year": "Dec 6, 2011"
		},
		{
			"title": "Whatever",
			"metascore": 62,
			"userscore": 5.1,
			"url": "https://www.metacritic.com/music/whatever-2011/hot-chelle-rae",
			"year": "Nov 29, 2011"
		},
		{
			"title": "Break the Spell",
			"metascore": 61,
			"userscore": 3.8,
			"url": "https://www.metacritic.com/music/break-the-spell/daughtry",
			"year": "Nov 21, 2011"
		},
		{
			"title": "Stronger",
			"metascore": 62,
			"userscore": 6.1,
			"url": "https://www.metacritic.com/music/stronger-2011/kelly-clarkson",
			"year": "Oct 24, 2011"
		},
		{
			"title": "Cole World: The Sideline Story",
			"metascore": 75,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/cole-world-the-sideline-story/j-cole",
			"year": "Sep 27, 2011"
		},
		{
			"title": "Sweeter",
			"metascore": 64,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/sweeter/gavin-degraw",
			"year": "Sep 20, 2011"
		},
		{
			"title": "Neon",
			"metascore": 78,
			"userscore": "",
			"url": "https://www.metacritic.com/music/neon/chris-young",
			"year": "Jul 12, 2011"
		},
		{
			"title": "This Loud Morning",
			"metascore": "",
			"userscore": 5.8,
			"url": "https://www.metacritic.com/music/this-loud-morning/david-cook",
			"year": "Jun 28, 2011"
		},
		{
			"title": "Planet Pit",
			"metascore": 70,
			"userscore": 4.3,
			"url": "https://www.metacritic.com/music/planet-pit/pitbull",
			"year": "Jun 21, 2011"
		},
		{
			"title": "This Is Country Music",
			"metascore": 82,
			"userscore": 8.5,
			"url": "https://www.metacritic.com/music/this-is-country-music/brad-paisley",
			"year": "May 23, 2011"
		},
		{
			"title": "Wasting Light",
			"metascore": 78,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/wasting-light/foo-fighters",
			"year": "Apr 12, 2011"
		},
		{
			"title": "The Golden Age of Knowhere",
			"metascore": 65,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/the-golden-age-of-knowhere/funeral-party",
			"year": "Mar 29, 2011"
		},
		{
			"title": "Femme Fatale",
			"metascore": 67,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/femme-fatale/britney-spears",
			"year": "Mar 29, 2011"
		},
		{
			"title": "Angles",
			"metascore": 71,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/angles/the-strokes",
			"year": "Mar 22, 2011"
		},
		{
			"title": "Glam Nation Live",
			"metascore": "",
			"userscore": 7,
			"url": "https://www.metacritic.com/music/glam-nation-live/adam-lambert",
			"year": "Mar 22, 2011"
		},
		{
			"title": "I Remember Me",
			"metascore": 68,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/i-remember-me/jennifer-hudson",
			"year": "Mar 22, 2011"
		},
		{
			"title": "Stronger",
			"metascore": 74,
			"userscore": "",
			"url": "https://www.metacritic.com/music/stronger/sara-evans",
			"year": "Mar 8, 2011"
		},
		{
			"title": "Goodbye Lullaby",
			"metascore": 58,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/goodbye-lullaby/avril-lavigne",
			"year": "Mar 8, 2011"
		},
		{
			"title": "Love Me Back",
			"metascore": 82,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/love-me-back/jazmine-sullivan",
			"year": "Nov 30, 2010"
		},
		{
			"title": "Cannibal",
			"metascore": 73,
			"userscore": 7.4,
			"url": "https://www.metacritic.com/music/cannibal/keha",
			"year": "Nov 22, 2010"
		},
		{
			"title": "Live It Up",
			"metascore": 45,
			"userscore": 5.9,
			"url": "https://www.metacritic.com/music/live-it-up/lee-dewyze",
			"year": "Nov 16, 2010"
		},
		{
			"title": "Come Around Sundown",
			"metascore": 64,
			"userscore": 6.9,
			"url": "https://www.metacritic.com/music/come-around-sundown/kings-of-leon",
			"year": "Oct 19, 2010"
		},
		{
			"title": "Happiness",
			"metascore": 58,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/happiness/hurts",
			"year": "Sep 6, 2010"
		},
		{
			"title": "God Willin' & the Creek Don't Rise",
			"metascore": 72,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/god-willin-the-creek-dont-rise/ray-lamontagne",
			"year": "Aug 17, 2010"
		},
		{
			"title": "We Are Born",
			"metascore": 68,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/we-are-born/sia",
			"year": "Jun 22, 2010"
		},
		{
			"title": "Bionic",
			"metascore": 56,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/bionic/christina-aguilera",
			"year": "Jun 8, 2010"
		},
		{
			"title": "Bionic",
			"metascore": 56,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/bionic/christina-aguilera",
			"year": "Jun 8, 2010"
		},
		{
			"title": "Animal",
			"metascore": 54,
			"userscore": 6.2,
			"url": "https://www.metacritic.com/music/animal/keha",
			"year": "Jan 5, 2010"
		},
		{
			"title": "Phrazes For The Young",
			"metascore": 72,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/phrazes-for-the-young/julian-casablancas",
			"year": "Nov 3, 2009"
		},
		{
			"title": "Say Anything",
			"metascore": 76,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/say-anything/say-anything",
			"year": "Nov 3, 2009"
		},
		{
			"title": "The Greatest Hits",
			"metascore": 85,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/the-greatest-hits/foo-fighters",
			"year": "Nov 3, 2009"
		},
		{
			"title": "Ellipse",
			"metascore": 68,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/ellipse/imogen-heap",
			"year": "Aug 25, 2009"
		},
		{
			"title": "Leave This Town",
			"metascore": 59,
			"userscore": 4.2,
			"url": "https://www.metacritic.com/music/leave-this-town/daughtry",
			"year": "Jul 14, 2009"
		},
		{
			"title": "Big Whiskey And The GrooGrux King",
			"metascore": 67,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/big-whiskey-and-the-groogrux-king/dave-matthews-band",
			"year": "Jun 2, 2009"
		},
		{
			"title": "Shine",
			"metascore": 67,
			"userscore": "",
			"url": "https://www.metacritic.com/music/shine/martina-mcbride",
			"year": "Mar 24, 2009"
		},
		{
			"title": "Easy Does It",
			"metascore": 66,
			"userscore": "",
			"url": "https://www.metacritic.com/music/easy-does-it/jake-owen",
			"year": "Feb 24, 2009"
		},
		{
			"title": "David Cook",
			"metascore": 61,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/david-cook/david-cook",
			"year": "Nov 18, 2008"
		},
		{
			"title": "Play",
			"metascore": 70,
			"userscore": 8.4,
			"url": "https://www.metacritic.com/music/play/brad-paisley",
			"year": "Nov 4, 2008"
		},
		{
			"title": "Only By The Night",
			"metascore": 63,
			"userscore": 7,
			"url": "https://www.metacritic.com/music/only-by-the-night/kings-of-leon",
			"year": "Sep 23, 2008"
		},
		{
			"title": "The Bright Lights Of America",
			"metascore": 63,
			"userscore": 6.5,
			"url": "https://www.metacritic.com/music/the-bright-lights-of-america/anti-flag",
			"year": "Apr 1, 2008"
		},
		{
			"title": "Echoes, Silence, Patience & Grace",
			"metascore": 71,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/echoes-silence-patience-grace/foo-fighters",
			"year": "Sep 25, 2007"
		},
		{
			"title": "Just Who I Am: Poets & Pirates",
			"metascore": 70,
			"userscore": 6.6,
			"url": "https://www.metacritic.com/music/just-who-i-am-poets-pirates/kenny-chesney",
			"year": "Sep 11, 2007"
		},
		{
			"title": "Libertad",
			"metascore": 68,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/libertad/velvet-revolver",
			"year": "Jul 3, 2007"
		},
		{
			"title": "My December",
			"metascore": 64,
			"userscore": 6.9,
			"url": "https://www.metacritic.com/music/my-december/kelly-clarkson",
			"year": "Jun 26, 2007"
		},
		{
			"title": "Version",
			"metascore": 63,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/version/mark-ronson",
			"year": "Jun 12, 2007"
		},
		{
			"title": "The Best Damn Thing",
			"metascore": 66,
			"userscore": 7.3,
			"url": "https://www.metacritic.com/music/the-best-damn-thing/avril-lavigne",
			"year": "Apr 17, 2007"
		},
		{
			"title": "Because Of The Times",
			"metascore": 79,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/because-of-the-times/kings-of-leon",
			"year": "Apr 3, 2007"
		},
		{
			"title": "Empire",
			"metascore": 65,
			"userscore": 7.1,
			"url": "https://www.metacritic.com/music/empire/kasabian",
			"year": "Sep 19, 2006"
		},
		{
			"title": "Back To Basics",
			"metascore": 69,
			"userscore": 8.8,
			"url": "https://www.metacritic.com/music/back-to-basics/christina-aguilera",
			"year": "Aug 15, 2006"
		},
		{
			"title": "First Impressions Of Earth",
			"metascore": 69,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/first-impressions-of-earth/the-strokes",
			"year": "Jan 3, 2006"
		},
		{
			"title": "Harmonies For The Haunted",
			"metascore": 58,
			"userscore": 8.2,
			"url": "https://www.metacritic.com/music/harmonies-for-the-haunted/stellastarr",
			"year": "Sep 13, 2005"
		},
		{
			"title": "In Your Honor",
			"metascore": 70,
			"userscore": 8.1,
			"url": "https://www.metacritic.com/music/in-your-honor/foo-fighters",
			"year": "Jun 14, 2005"
		},
		{
			"title": "Stand Up",
			"metascore": 63,
			"userscore": 6.6,
			"url": "https://www.metacritic.com/music/stand-up/dave-matthews-band",
			"year": "May 10, 2005"
		},
		{
			"title": "Kiss & Tell",
			"metascore": 65,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/kiss-tell/sahara-hotnights",
			"year": "Jul 27, 2004"
		},
		{
			"title": "Happenstance",
			"metascore": 74,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/happenstance/rachael-yamagata",
			"year": "Jun 8, 2004"
		},
		{
			"title": "Contraband",
			"metascore": 65,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/contraband/velvet-revolver",
			"year": "Jun 8, 2004"
		},
		{
			"title": "Room On Fire",
			"metascore": 77,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/room-on-fire/the-strokes",
			"year": "Oct 28, 2003"
		},
		{
			"title": "Some Devil",
			"metascore": 61,
			"userscore": 8.6,
			"url": "https://www.metacritic.com/music/some-devil/dave-matthews",
			"year": "Sep 23, 2003"
		},
		{
			"title": "stellastarr*",
			"metascore": 78,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/stellastarr/stellastarr",
			"year": "Sep 23, 2003"
		},
		{
			"title": "Youth & Young Manhood",
			"metascore": 79,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/youth-young-manhood/kings-of-leon",
			"year": "Aug 19, 2003"
		},
		{
			"title": "It's All In Your Head",
			"metascore": 58,
			"userscore": 8.7,
			"url": "https://www.metacritic.com/music/its-all-in-your-head/eve-6",
			"year": "Jul 22, 2003"
		},
		{
			"title": "Thankful",
			"metascore": 62,
			"userscore": 5.3,
			"url": "https://www.metacritic.com/music/thankful/kelly-clarkson",
			"year": "Apr 15, 2003"
		},
		{
			"title": "Strangest Things",
			"metascore": 63,
			"userscore": 7.8,
			"url": "https://www.metacritic.com/music/strangest-things/longwave",
			"year": "Mar 18, 2003"
		},
		{
			"title": "Antenna",
			"metascore": 78,
			"userscore": 8,
			"url": "https://www.metacritic.com/music/antenna/cave-in",
			"year": "Mar 18, 2003"
		},
		{
			"title": "A New Day At Midnight",
			"metascore": 71,
			"userscore": 7.6,
			"url": "https://www.metacritic.com/music/a-new-day-at-midnight/david-gray",
			"year": "Nov 5, 2002"
		},
		{
			"title": "Stripped",
			"metascore": 55,
			"userscore": 8.9,
			"url": "https://www.metacritic.com/music/stripped/christina-aguilera",
			"year": "Oct 29, 2002"
		},
		{
			"title": "One By One",
			"metascore": 75,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/one-by-one/foo-fighters",
			"year": "Oct 22, 2002"
		},
		{
			"title": "Busted Stuff",
			"metascore": 78,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/busted-stuff/dave-matthews-band",
			"year": "Jul 16, 2002"
		},
		{
			"title": "Atomic",
			"metascore": 61,
			"userscore": 7,
			"url": "https://www.metacritic.com/music/atomic/lit",
			"year": "Oct 16, 2001"
		},
		{
			"title": "Underneath",
			"metascore": 63,
			"userscore": 7.9,
			"url": "https://www.metacritic.com/music/underneath/the-verve-pipe",
			"year": "Sep 25, 2001"
		},
		{
			"title": "2000 Watts",
			"metascore": 70,
			"userscore": "",
			"url": "https://www.metacritic.com/music/2000-watts/tyrese",
			"year": "May 22, 2001"
		},
		{
			"title": "Everyday",
			"metascore": 67,
			"userscore": 7.7,
			"url": "https://www.metacritic.com/music/everyday/dave-matthews-band",
			"year": "Feb 27, 2001"
		},
		{
			"title": "When It All Goes South",
			"metascore": 48,
			"userscore": "",
			"url": "https://www.metacritic.com/music/when-it-all-goes-south/alabama",
			"year": "Jan 16, 2001"
		},
		{
			"title": "Peggy's Blue Skylight",
			"metascore": "",
			"userscore": "",
			"url": "https://www.metacritic.com/music/peggys-blue-skylight/andy-summers",
			"year": "Sep 26, 2000"
		},
		{
			"title": "Mi Reflejo",
			"metascore": 56,
			"userscore": 8.3,
			"url": "https://www.metacritic.com/music/mi-reflejo/christina-aguilera",
			"year": "Sep 12, 2000"
		},
		{
			"title": "Horrorscope",
			"metascore": 53,
			"userscore": 7.5,
			"url": "https://www.metacritic.com/music/horrorscope/eve-6",
			"year": "Jul 25, 2000"
		}
	]
}
```

### Music Detail

```json
{
	"type": "music",
	"url": "https://www.metacritic.com/music/sos/sza",
	"title": "S.O.S.",
	"musician": "SZA",
	"musicianUrl": "https://www.metacritic.com/person/sza",
	"companyName": "RCA",
	"companyUrl": "https://www.metacritic.com/company/rca",
	"summary": "The second full-length studio release for R&B artist SZA features guest appearances from Phoebe Bridgers, Ol' Dirty Bastard, Travis Scott, and Don Toliver.",
	"metascore": 90,
	"userscore": 8.6,
	"genres": [
		"R&B"
	],
	"buyLink": "https://www.amazon.com/dp/B0BNXZPL4G%3Ftag%3Dmetacritic-musiccat-20%26linkCode%3Dosi%26th%3D1%26psc%3D1"
}
```

### With Reviews
```json
{
	"type": "music",
	"url": "https://www.metacritic.com/music/cacti/billy-nomates",
	"title": "Cacti",
	"musician": "Billy Nomates",
	"musicianUrl": "https://www.metacritic.com/person/billy-nomates",
	"companyName": "Invada",
	"companyUrl": "https://www.metacritic.com/company/invada",
	"summary": "The second full-length release for British singer-songwriter Billy Nomates was produced with James Trevascus.",
	"metascore": 85,
	"userscore": null,
	"genres": [
		"Pop/Rock"
	],
	"buyLink": "https://www.amazon.com/dp/B0BJTZT1HZ%3Ftag%3Dmetacritic-musiccat-20%26linkCode%3Dosi%26th%3D1%26psc%3D1",
	"userReviewsSummary": {
		"positive": 0,
		"mixed": 1,
		"negative": 0
	},
	"userReviews": [
		{
			"score": 5,
			"date": "Jan 13, 2023",
			"review": "Nach der Scheiße, freut sich jeder Mensch auf „Every Loser“ von Iggy, bitte als Kompliment auffassen.",
			"source": "jens76"
		}
	],
	"criticReviewsSummary": {
		"positive": 10,
		"mixed": 1,
		"negative": 0
	},
	"criticReviews": [
		{
			"score": 90,
			"date": "Jan 13, 2023",
			"review": "Despite all the changes she introduces on Cacti, the honesty of Maries' music remains paramount, and the savvy and polish she brings to the album confirm she's an excitingly hard-to-pin-down artist.",
			"source": "AllMusic"
		},
		{
			"score": 90,
			"date": "Jan 12, 2023",
			"review": "It’s a statement of intent from Billy Nomates, unbalancing sonic scales and weaving this into a force to be reckoned with.",
			"source": "Clash Music"
		},
		{
			"score": 90,
			"date": "Jan 11, 2023",
			"review": "Cacti is relentless, laser-focused and irresistible. [Feb 2023, p.32]",
			"source": "Uncut"
		},
		{
			"score": 80,
			"date": "Jan 17, 2023",
			"review": "Best described as a punk with a keyboard and tunes to burn, Nomates has dug even deeper for Cacti, her songwriting broadening its reach. Her deadpan takedowns remain heroic.",
			"source": "The Observer (UK)"
		},
		{
			"score": 80,
			"date": "Jan 13, 2023",
			"review": "This is a softer, more introspective approach than her barn-storming debut, but this 12-track album doesn’t lack the punch and bite of its debut in spite of this.",
			"source": "The Telegraph (UK)"
		},
		{
			"score": 80,
			"date": "Jan 11, 2023",
			"review": "A seething but persevering energy flows intensely CACTI.",
			"source": "Exclaim"
		},
		{
			"score": 80,
			"date": "Jan 11, 2023",
			"review": "The narrative lines are fractured, the satire removed; these songs play out like stress responses, fight-or-flight impulses, each one a little panic room. ... There’s not a lot of feeling OK on CACTI, but for once, it feels like exactly the right place for Billy Nomates. She’s brought herself, entirely. [Feb 2023, p.86]",
			"source": "Mojo"
		},
		{
			"score": 80,
			"date": "Jan 11, 2023",
			"review": "Cacti might show Maries in survival mode, but revealing vulnerability has seen her songwriting soften and come into its own.",
			"source": "Record Collector"
		},
		{
			"score": 70,
			"date": "Jan 13, 2023",
			"review": "Bottom line: if you like diva pop with a little edge, have at it. But if you got into Billy Nomates because she reminded you of the Sleaford Mods, maybe sit CACTI out.",
			"source": "Dusted Magazine"
		},
		{
			"score": 70,
			"date": "Jan 11, 2023",
			"review": "There’s still that personable rawness to her production – the synthetic drums and often sparse arrangement mirroring her frequently despondent lyrical themes (“The death of everything real has happened…” begins ‘apathy is wild’). But her vocal offers warmth.",
			"source": "DIY Magazine"
		},
		{
			"score": 60,
			"date": "Jan 11, 2023",
			"review": "CACTI is understandably more subdued than her self-titled debut, but the boisterous numbers it does contain, like spite, might feel more dynamic played live by humans – it feels like the energy that makes her such a captivating performer is being restricted by her drum machine.",
			"source": "The Skinny"
		}
	]
}
```
