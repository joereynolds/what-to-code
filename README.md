# what-to-code

## Index

1. [Command line](#command-line)
2. [Local, non-interactive tools](#non-interactive)
3. [Desktop apps](#desktop)
3. [Games](#games)
4. [Improvements/Features](#improvements) - Most of these are pull requests that could be made to improve various thing I like
5. [Re-implementations](#reimplementation)- These ideas already exist but they're fun anyway
6. [ViM](#vim) - Various functions I would quite like to have in ViM
7. [Websites](#websites) - Original website ideas that I'll never get around to doing :(
8. [Service](#service) - ???

If you make any of these, let me know!
If you make them and they're not FOSS, don't let me know.

<a name="command-line"></a>
### Command line

- A command line music theory program 

- `where-is` a program that helps you find config files etc...
  i.e.
  ```
  where-is grub config
  ```
  Should output a possible list of locations
  ```
  /boot/default/grub.d
  /etc/grub.d
  ```
- An SQL parser to report better error messages than the god awful MySQL ones. Ideally build it using Bison and Flex so we don't have a bad time reinventing the wheel. 

- A program that can split one file into many. For example, I had a csv file that was 300mb and could not do any processing with it because it was so big. All the other alternatives that I checked out were either slow or not very user friendly. It should work on any file type, not just csv's. There is a good one [here](https://github.com/imartingraham/csv-split) but I feel it could be made faster in C or Rust.

- A front end to gtags-cscope

- A better `cd`. You just type `cd Directory` and then it will try and go to the directory called `Directory`. If multiple results are found, it populates a list for you to choose from.

- A command-line utility that gets the extension of a file (Write it in scheme?)
  i.e.
  ```
  ext hello.jpg
  ext myfile.test.php
  ```
  Would output
  ```
  jpg
  php
  ```

- A command-line program that generates a random string that is N characters long.
  i.e.
  ```
  chars 10
  gwrtp+5gl~
  ```


- (Could also be a webpage) A password hasher. You give it a string and the type of hashing algorithm (SHA-1, MD5, Bcrypt etc...) and it returns the encrypted string.

- An endpoint tester/fuzzer, i.e. if you have the following endpoint

  `http://services/preferences?customerid=23543&group_id=1`

  You could feed it to the program like this

  `fuzz http://services/preferences?customerid={{INT}}&group_id={{INT}}`


  Note that we've specified the data types of the parameters. This is so that we can fuzz appropriately.
  Now, the `fuzz` program will attempt various different datasets on it, for example it would call these (through curl probably)

  `http://services/preferences?customerid=-23&group_id=3` (negative number)

  `http://services/preferences?customerid=000001&group_id=5` (leading zeroes)

  `http://services/preferences?customerid=5&group_id=9999999999999999999999999999999999999999` (large number)

  `http://services/preferences?customerid=7&group_id=-9999999999999999999999999999999999999999` (large negative number)

  `http://services/preferences?customerid=&group_id=` (empty parameters)


  Any that produce an error, would report back to you through the CLI with the error message and the url that caused the error.

- A MIDI drum track linter.
  i.e.
  ```midi-lint drum-track.mid```
  outputs
  ```
  bar 4 : Drum is hitting 3 things at once. Drummers don't have 3 arms.
  bar 1 - 56 : hi-hat hits are too consistent. hits are usually strong on the first and 3rd beat and weak on 2nd and 4th
  bar 78 : Drumspeed is probably not possible with a human drummer, too fast.
  bar 98 : Machine-gun snare. Vary the velocities of the snare drum.
  etc...
  ```

- A command-line utility to grep through SQL.
i.e.:
  ```grepsql "sarah"  --db="people" ```

- A regression testing CLI for CSS/HTML. On building a release it would take a screenshot of the current branch, and the master (or a specified image?) and if they did not match, it would warn of it and display the diffed image. You can use `ImageMagick` to diff images. See here: http://stackoverflow.com/questions/5132749/diff-an-image-using-imagemagick
  `PhantomCSS` is a thing, but I was thinking of something less Node and more gnarly...
  Steps would include
  - Visits the webpage on your branch
  - Screenshots it
  - Visits the webpage on the master branch
  - Screenshots it
  - Diffs them with imageMagick
  - If there are differences, tells you about them

- A design linter for css files. Given a css file it highlights the bad aspects of it.
  i.e.
  ```css-lint style.css```
  Would output
  - found 12 font sizes, more than 3 is overkill
  - found multiple font families used, 2 is recommended
  - found multiple different colours used. Recommend no more than 5
  - found large amount of differing values for margins
  - found large amount of differing values for paddings
  - found non standard media query sizes...why?
  <a name="non-interactive"></a>
  
### Local, non-interactive (command-line / daemon)

  - A program that goes on a usb stick. When the usb stick is attached, it moves a file from the USB stick to the pc (ideally without triggering any 'potentially harmful' warnings)

  - A 'level' generator for DND. Generates a maze, treasure, and enemies. You get to choose the level and it generates creatures/treasure suitable for that character level.

  - Interactive Apache - Learn apache configuration from the command line. It should be similar to [githug](https://github.com/Gazler/githug) in the way it works.

  - MySQL linter - Given a file, it'll show you where the errors are, what possible caused those errors (instead of the god awful mysql error reporting) etc...

  - OCR. Submit an image and it tries to read the text of the image.

  - A log parser for HOMMV log files. Must be realtime (I.E. ```tail -f```). Use electron.

  - A glyph generator. It creates a glyph for each letter of the alphabet and saves it in a font file.


  - A bash shell script/program that logs all the files you've written to (and maybe there line numbers) for x amount of time. (preferably 1 year). That way, when someone asks you 'You know that change for the PEAR email library, what was it?' you can come back with an answer.
  The log might look like
  ```
[23-02-2015] my/php/file.php [opened]
[24-02-2015] my/php/file.php [opened]
[24-02-2015] my/php/file.php [deleted]
```

- A program that creates a LERP between two images. maybe specify the amount of frames you want for the lerp?
i.e.
  ```
  tween_images(from_image, to_image, frames=5)
  ```
  Would create 5 tween images.

- A program that finds dead functions (ones not used).  
  It finds all functions in a file, greps through each function name.
  If that grep brings back nothing, then it's not used (provided it's
  only used in one codebase that is..)
  Here's my attempt https://gist.github.com/joereynolds/1cdc040605d7751714b7ef66e77d4795

  This is a very naive way of looking at it but it will work for most cases where people aren't doing devilish things with eval or 'variable variables'

- word ladder that goes from one word to another ideally in the shortest amount of steps as possible
  e.g. Dog to Fig = Dog -> Dig -> Fig
  or
  Dog -> Fog -> Fig

- A soundex-ifier for songs, it changes the lyrics of the song to words that sound like that word.
  i.e.
  'Will the real slim shady please stand up' -> 'Bill the seal tin baby please stand up'.
  It should have an API similar  to this
  `soundex_song('slim-shady.txt', amount=0.75)`

  The amount parameter should be how 'soundexed' the song is on a scale between 0 - 1. 1 would be every word, 0 would be no words.

- Some sort of program that finds potentially hard-coded things to make us aware of them,
  i.e.

  This string `'You can register by 30th of June'` in a HTML template is a nono.

  It should warn/flag it up and output something like 'You can register by REGISTRATION_DATE'

- Given an image, you should convert it into a text-based equivalent. For example: https://github.com/joereynolds/Image-to-Ascii

- Given an audio file of someone dialling a number, approximate the number dialled from the frequency of each tone. See http://en.wikipedia.org/wiki/Telephone_keypad for details.

- Just like "inotify" tracks creation/modification of files, create something that allows one to track modification of individual  **blocks** of specific files.  This probably needs to be a kernel module.

- A graph-based single-file compression algorithm with the name `jan`, so that we can have file with a [`.tar.jan`](https://en.wikipedia.org/wiki/Robert_Tarjan#Algorithms_and_data_structures).  (If you don't want to click the link: Robert Tarjan developed a bunch of cool algorithms and data structures regarding graphs.)

<a name="desktop"></a>
### Desktop apps

- An apache access log file viewer. Should show things by column, handle regex etc...
  Things like Graylog are a bit too overkill for this and there are no simple alternatives for linux.

- A basic video editor. It should handle the bare minimum (yet useful features)
  - Merge two videos together
  
- A cross platform podcast manager, (see gpodder). Build on Electron? You should be able to:
  - Add/Remove podcast subscriptions
  - Tag subscriptions (Programming, Music, Creative etc...)
  - Search by tag
  - View by tag
  - etc...

- A gui to manage various apache things and that's not based around cPanel (eww). You should be able to
  - Manage subdomains (create, remove etc...)
  - Manage document roots
  - Other stuff...?
  
- A desktop app that is basically just an input box where you enter a JIRA ticket and it'll open up the URL for you. If it's a project ticket, it'll open up the pull request page instead.

- A desktop app which logs the time of each application that you view. i.e. it'll give you a breakdown of the total time spent on each program.

- A desktop app that parses Risk of Rain log files (if they have any) and does something interesting with them.

- A desktop app that shows system information. Similar to conky but less shit. The markup would be in HTML (not a made up format like conky) and it could be styled with CSS (not a made up style format like conky).
  Use electron.
  Here's one idea of how it would look
  ```
  <main>
    <div class="cpu-usage">
      <div data-format="percent" class="bar"></div>
    </div>
  </main>
  ```
  That'd spit out a CPU-usage bar showing usage in percent.

**Created** https://github.com/joereynolds/fanbox


- A desktop app. A metronome a decent one. One that can handle complex time signatures and handle bars too. i.e. 1 bar of 7/8 and then the next bar is 5/4. Should also be able to handle multiple tempos across bars

- A desktop app that profiles code. i.e. runs a function 100 times and outputs a csv/txt file of the results.

- Porn keyboard
  Get samples of women's moans from the low E to the 12th fret on the high e. Map these to a MIDI keyboard in kontakt.
  Try and get multiple samples per note to allow for variety.

- A GUI for partitioning USB's/disks.
  Use electron and the style of form in the codepen.
  should be able to do http://superuser.com/questions/878108/8gb-memory-stick-only-showing-49mb
  without using a cmdline.

- A GUI to easily manage adding/removing context menu entries.
  Built using electron. also using that codepen form style.

- A desktop app that uses the notifications api to push any PHP errors to it.
  (If errors are too frequent, think of a better way)

- A desktop mailing list manager.

<a name="games"></a>
### Games

- A tamagotchi.

- An alchemy kinda game - Grow a garden of different plants that need certain conditions. when plants have grown, mush em up and make potions

- Defend your castle game

- The jetpack game: You're a stickman who needs to get to the other side of the map in his jetpack without hitting any obstacles.
 
- Melvin and Waldorf: A couch-co-op platformer.(vague, I know)


<a name="vim"></a>
### ViM

- (Created here https://github.com/joereynolds/place.vim) Vim Plugin `appendAt`. The mapping would be `ga` (this shadows the normal vim functionality of showing an ascii value under the cursor, which I have seen precisely 0 people ever use).

It would take a motion and a character to append at. Here's some examples to clarify

```
ga^var "At the beginning of the line, append var
ga$; "At the end of the line append ;
gab$ "At the beginning of <cword> append $
ga}. "At the end of the paragraph, append a .
gagg<?php "At the start of the file add <?php
etc...
```

- A ViM function that unit tests the current function your cursor is in.
  i.e. If you're cursor is in an 'getPriceForTravel' function, then executing the vim function would do something like
  `phpunit path/to/file functionName` under the hood
  
- (Created here https://github.com/joereynolds/SQHell.vim) A modern version of the dbext plugin. It would be able to use mysql, postgres etc... but also able to set up a connection through a docker container (or any other thing really). Features in mind
  - Run current line as SQL statement
  - Run file as SQL statement
  - SELECTing should bring back the results in a buffer which can then have buffer local remappings such as
    - `dd` would delete the record you're under
    - Changing any records (apart from pk) and then `:wq`ing would update the records.
      - There should be a config option to prompt for confirmation beforehand (default is on)
      - Autocompletion should NOT be baked in. It should be a separate source for the completion manager of choice.
       
      - When we do SHOW TABLES, it'd be good to have some more shortcuts in the buffer such as
        - `D`: Pressing this over the table in the result would Describe it
        - `S`: Pressive this over the table in the result would select from it (perhaps with a limit)
        - `dd`: Drop the table

      - When we do SHOW DATABASES, the following would be good:
        - `S`: Show the tables in this database
        - `dd`: Drop the database
           
  
- A function/plugin that moves a visual selection into its own file. Useful for refactoring large files into smaller ones.
It would only create files, not append to pre-existing files

- Function to turn a camelCase name into dash-separated for css files

- A function that removes all trailing whitespace

- A plugin that correctly infers databases, tables and columns through autocompletion. One way of doing this would be to hold an in-memory dictionary of mappings of the form db->table->column
The structure may look like this
```
db_mappings = [
    'customer_portal':
        customer:
            account:
                id,
                first_name,
                last_name,
                created_at,
        transactions:
            id,
            created_at,
            type,
            request
        logs:
            id,
            action,
            updated_at
     ,
     more dbs here...
     ...
]
```
In the above, `customer_portal` is the db, `customer`, `transactions`, and `logs` are the related tables and then nested inside them are their columns. Typing in an sql file should first look in the database for a matching word, if none found, check the tables, and then finally, columns.

- A plugin that adds more command line replacements. For example `%` already stands for the current file, it'd be good if we could do `c` for the current class we're in, or `f` for function (use different letters as they're too generic)

- A better version of search (`/`). It would behave exactly the same except it would say how many matches there were and how far through you were i.e. '20/60 matches' means you're on the 20th out of 60 matches. Ideally this would be in the bottom right of the status bar.

- A plugin that shows the valuable of a variable (if defined) on hovering over that text. For example
  If my cursor is on any letter in `self::NEW_TASK_ID` then above it I should see the omnicomplete box thing with
  `43000` in it for example.

- A re-mapping of some of PHPStorm's cool features. For instance ctrl+alt+shift+n searches for a function with that name in that file. This could be remapped by doing /n searchTerm

<a name="websites"></a>
### Websites

- A website(?) that tries to standardise hotkeys across programs. i.e. ctrl+p in chrome opens up a file explorer but on most desktop apps it opens up the preferences. Fix this. Could maybe just be a github repo?

- An online app where a user can organise their thoughts. The nav would be on the side and would have entries such as (maybe base it around Ben Elijah's principles)
  - Todo : Organise your stuff to do here 
  - Notes : Basic rambling page
    
- An online calendar that doesn't require login or auth. You create a calendar and get a permalink. Anyone with that permalink is free to add events etc...

- A web utility that generates an image either of a specified dimension size, or, filesize.

- A website that shows a listing of work that charities/free people need. Devs then pick a project and get to work on (hopefully) doing something good for free. Something similar exists but doesn't just focus on software https://www.volunteermatch.org/

- OpenGameMusic - A website for musicians to submit their music (to public domain or CC) and have it used by video game developers. This is largely based on [opengameart](opengameart.org) but focused entirely around music and with a better search.

- Online version of snake with cool powerups.

- A website that shows a listing of programs and its hotkeys.

- A webpage for steam games. Enter the game and it'll show you (or take you to) the person that has the most playtime for that game and their review. Only scrapes reviews.

- A website that is a database of bird calls. Would have a table format like this
  Bird Picture | Bird name | play button to listen to call | read more button  
  Could be scraped from [xeno-canto.org](http://www.xeno-canto.org/)

- A jra util that shows a raw string. i.e '1 2 3 4 5' would return '1SPACE2SPACE3' or whatever the space code is...
**Created** http://util.joereynoldsaudio.com/util/rawtext

- A website which contains a database of instrumentation for songs. You can search for a song that has 2 violins and a piano and then it shows the matches. This is a huge project.

<a name="service"></a>
### Service

- A program that orders stuff of ebay. You pump it with £365 and everyday it'll order one new item and have it delivered to work with that persons name, then, it's their lucky day!

- An internal-style webpage manager thingy for bands. Audio clips would automatically loaded in (use audiojs?), videos would be a 4x4 grid, photos etc... 
  Basically somewhere to manage all the ideas, videos of jam sessions etc...

- A bot to farm neocoins from neopets

- A CSS framework that's based on flex and has good out of the box styling with minimal HTML boilerplate (opposite of bootstrap.).. You'll need to get clever with selectors for this one.

- A page to dump laravel queries and have them transformed into raw sql. For example
  ```
     $this->db->table('customers.person')
         ->select(
             $this->db->raw(
                  "IF(
                         email REGEXP '.+@.+\..+', email, IF (email2 REGEXP '.+@.+\..+', email2, NULL)
                     ) AS email"
                 )
             )
         ->where('personId', $personId)
         ->first()->email;
  ```

  Should be transformed into the SQL equivalent.


- An online bot that listens on ebay for a product and when it goes to the price threshold you set, it buys it for you. iMacros + PHP?

- MusiCSS. A CSS library based around music notation

- A JRA util that allows users to see and mess around with CSS filters. **Created** http://util.joereynoldsaudio.com/snippets/filters

- A free SMS service for farmers in 3rd world countries so they don't get scammed by traders on their product. They text the service something like 'Wheat' (would have to be fuzzy because they're probably shit at spelling...) and it replies with the price you should expect to gain from it.

- An amazon monitoring program that monitors whatever products you tell it to and it'll tell you when it's
  a) dropped in price
  b) a new marketplace seller has added the item and is lower than the previous one
  Alternatively, you can give it a price and if it ever reaches that price, it'll email you.

- A site generator based on markdown files and no setup.
  You send the file over to the server and it renders it for you, that's it!

- A better version of the Nicepage chrome extension I made

- An open source, free hostel booking program similar to dorm booker, but free and more featureful

- Pokemon cry analyser - given a pokemons cry, analyse the waveform and return back the pokemon it came from.

- A RaspberryPi controlled, voice recognition software, which tracks the WTF / minutes in the office and outputs a nice chart of employee productivity. Reference: https://i.imgur.com/J1svNp7.jpg

<a name="improvements"></a>
### Improvements / features

- Make a PR to ajenti that prettifies PHP log files when you choose one.

- Make a PR to Rich's node-notifier.

- A tagpro add-on that shows the entire map and the location of all the players

- Get openRA, find some problems, submit a PR

- Make a PR to chrome's devtools. When you ctrl+p in a CSS file, the matches are badly prioritised.

- xscreensaver plugins:
    - Uplink [ARC login screen](https://www.dropbox.com/s/1aaubt6iiqft5kw/ARC%20login.png?dl=0) (or Arunmore if you must). Note that the visible input fields don't need to actually work, as xscreensaver doesn't support that.
    - cellular automata?  (not only game of life!)
    - "5000 dots" http://www.scp-wiki.net/scp-1336

<a name="reimplementation"></a>
### Re-implementations

- A port of [Faker](https://github.com/fzaninotto/Faker) to Scheme

- A keylogger built using electron.

- A bitcoin miner.

-  Zip / Postal Code Lookup – Enter a zip or postal code and have it return which city/cities that are in that zip code.

- Fetch Current Weather – Get the current weather for a given zip/postal code.

- Something to draw (and maybe interact with) [Apollonian Gaskets](https://en.wikipedia.org/wiki/Apollonian_gasket) (a kind of fractal)
