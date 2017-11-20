# SI 364 - Final Project questions

## Overall

* **What's a one-two sentence description of what your app will do?**
* An app that will allow you and others to sign in and build up a pokemon team of your own.

## The Data

* **What data will your app use? From where will you get it? (e.g. scraping a site? what site? -- careful not to run it too much. An API? Which API?)**
* The app will use data from the Pokeapi API to get data about pokemon.

* **What data will a user need to enter into a form?**
* When a user is creating their account, they'll need to add a username, a pokemon region, and optionally a photo to have as a 'user profile image'.
* an additional form can be used to help build up your pokemon team, where you provide a name or ask for a certain type of pokemon (like grass type) and then results will be sent back to the user which they can add to their team.

* **How many fields will your form have? What's an example of some data user might enter into it?**
* the first form for creating a provile will need 3 forms, 2 required and 1 optional. The username will need to be a text field, the region can be a dropdown menu to make sure that it's spelt correctly, and the third will be a file upload field (not including the submit field).
* the second form will need likely 2 fields, where at least one is required, but the first would be a specific name, the second would be a type, so that you can choose to 'search' by one or the other.

* **After a user enters data into the form, what happens? Does that data help a user search for more data? Does that data get saved in a database? Does that determine what already-saved data the user should see?**
* The first form saves the data into a database. The second form helps the user search, so it won't necessarily get data from a database or save it into one, but it does determine what the user should see next.

* **What models will you have in your application?**
* I'll need a model for the user, a model for pokemon, a relational database to connect users to pokemon, a model for regions, a model for towns, a relational database between regions and towns, and a relational database between towns and pokemon (potentially a relational database between regions and pokemon, if I want to build up that functionality).

* **What fields will each model have?**
* the user model will need a username, a userid, a pokemonteamid, and a picturelocation.
* the pokemon model will need a pokemonid, a type, a typeid, a trainerid, and fields for stats (such as strength or hp, if I want to display information about how strong a team of pokemon is.)
* the region will need a name, regionid, and townids
* the towns will need a townname, townid, and pokemonids

* **What uniqueness constraints will there be on each table? (e.g. can't add a song with the same title as an existing song)**
* Usernames need to be unique and each pokemon needs to be unique on a team (so you can't make up a team of only pikachu for example). 

* **What relationships will exist between the tables? What's a 1:many relationship between? What about a many:many relationship?**
* A 1:many relationship relationship between regions and towns, regions and trainers, and a many:many relationship between trainers and pokemon as well as towns and pokemon (since towns can spawn pokemon so you can show trainers where they can find pokemon).

* **How many get_or_create functions will you need? In what order will you invoke them? Which one will need to invoke at least one of the others?**
* I'll need one for each database that's not an association table(so about 4). I'll invoke the user one first, then region, then pokemon, then towns. user will need to invoke the region one, which will also need to invoke the pokemon one. The town will need to invoke the region and the pokemon databases.

## The Pages

* **How many pages (routes) will your application have?**
* 1 for the intial page, 1 for the form to make a user, 1 for logging in (could be the initial page), 1 for looking at user information, 1 for looking up information, 1 for listing pokemon to choose from, 1 for a speific pokemon, 1 for region information, 1 for town information. 1 to switch users or log out. Looks like 10 without counting error pages.

* **How many different views will a user be able to see, NOT counting errors?**
* 10, not including error pages.

* **Basically, what will a user see on each page / at each route? Will it change depending on something else -- e.g. they see a form if they haven't submitted anything, but they see a list of things if they have?**
* see above answer for each page/route. The option to add a pokemon to one's team is only viewable if the user is logged in.

## Extras

* **Why might your application send email?**
* It's possible that I'll want emails so that I'm updated when a new user is added.

* **If you plan to have user accounts, what information will be specific to a user account? What can you only see if you're logged in? What will you see if you're not logged in -- anything?**
* particular teams of pokemon will be specific to a user account. You can only look at user specific information if you're logged in, and you can only add pokemon to your team if you're logged in. Otherwise you can look up pokemon, region, and town information without being logged in.
* **What are your biggest concerns about the process of building this application?**
I suppose my biggest concerns will be creating the get_or_create function since so many of the databases rely on each other and getting the user authentication right, since we haven't learned it quite yet.
