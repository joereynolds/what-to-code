# what-to-code

You probably find yourself unable to thing of **what** to program.
So, I took the liberty of putting my big list of ideas on Github :D

## Note

These are the ideas that I thought of. As such, there are things in here specific to me
that I don't expect you to understand or want to implement.

A few entries have been removed as they were ideas for work.

## On with the show!

1. A desktop app that is basically just an input box where you enter a JIRA ticket and it'll open up the URL for you. If it's a project ticket, it'll open up the pull request page instead.

2. An online app where a user can organise their thoughts. The nav would be on the side and would have entries such as
- Todo : Organise your stuff to do here
- Notes : Basic rambling page

3. Make a PR to ajenti that prettifies PHP log files when you choose one.

4. A web page with lots of tools to help make work easier.

5. A desktop app which logs the time of each application that you view. i.e. it'll give you a breakdown of the total time spent on each program.

6. A desktop app that parses Risk of Rain log files (if they have any) and does something interesting with them.

7. Make a PR to Rich's node-notifier.

8. A web utility that generates an image either of a specified dimension size, or, filesize.

9. A keylogger built using electron.

10. A desktop app that shows system information. Similar to conky but less shit. The markup would be in HTML (not a made up format like conky) and it could be styled with CSS (not a made up style format~~ ~~like conky).
(built using electron)
Here's one idea of how it would look
```
<main>
  <div class="cpu-usage">
    <div data-format="percent" class="bar"></div>
  </div>
</main>
``` 
That'd spit out a CPU-usage bar showing usage in percent.
**Created**
https://github.com/joereynolds/fanbox 11. A website that shows a listing of work that charities/free people need. Devs then pick a project and get to work on (hopefully) doing something good for free.

12. A program that goes on a usb stick. When the usb stick is attached, it moves a file from the USB stick to the pc (ideally without triggering any 'potentially harmful' warnings)

13. [Removed]

14. Online version of snake with cool powerups.

15. [Removed]

16. A 'level' generator for DND. Generates a maze, treasure, and enemies. You get to choose the level and it generates creatures/treasure suitable for that character level.

17. OCR. Submit an image and it tries to read the text of the image.

18. A log parser for HOMMV log files. Must be realtime (I.E. ```tail -f```). Use electron.

19. A tamagotchi.

20. Melvin and Waldorf.

21. A website that shows a listing of programs and its hotkeys.

22. A bot to farm neocoins from neopets

23. A bitcoin miner.

24. A webpage for steam games. Enter the game and it'll show you (or take you to) the person that has the most playtime for that game and their review. Only scrapes reviews.

25. A CSS framework that's based on flex and has good out of the box styling with minimal HTML boilerplate (opposite of bootstrap.).. You'll need to get clever with selectors for this one. 

26. A tagpro add-on that shows the entire map and the location of all the players

27. Get openRA, find some problems, submit a PR

28. A website that is a database of bird calls. Would have a table format like this
Bird Picture | Bird name | play button to listen to call | read more button

29. A desktop app that profiles code. i.e. runs a function 100 times and outputs a csv/txt file of the results.

30. A desktop/web mailing list manager.

31. A glyph generator. It creates a glyph for each letter of the alphabet and saves it in a font file.

32. An alchemy kinda game - Grow a garden of different plants that need certain conditions. when plants have grown, mush em up and make potions

33. Defend your castle game

34. Porn keyboard
Get samples of womens moans from the low E to the 12th fret on the high e. Map these to a MIDI keyboard in kontakt.
Try and get multiple samples per note to allow for variety.

35. The jetpack game

36. A desktop app. A metronome a decent one. One that can handle complex time signatures and handle bars too. i.e. 1 bar of 7/8 and then the next bar is 5/4. Should also be able to handle multiple tempos across bars

37. A to-do list app based around Ben Elijah's principles.

38. A command line music theory program (this is already planned out just not built)

### WIP
https://github.com/joereynolds/cmaj

39. An online bot that listens on ebay for a product and when it goes to the price threshold you set, it buys it for you. iMarcos + PHP?

40. MusiCSS. A CSS library based around music notation

41. A JRA util that allows users to see and mess around with CSS filters

### Created
http://util.joereynoldsaudio.com/snippets/filters

42. A website that tries to standardise hotkeys across programs. i.e. ctrl+p in chrome opens up a file explorer but on most desktop apps it opens up the preferences. Fix this. Could maybe just be a github repo?

43. A desktop app that uses the notifications api to push any PHP errors to it.
(If errors are too frequent, think of a better way)

44. A bash shell script/program that logs all the files you've written to (and maybe there line numbers) for x amount of time. (preferably 1 year). That way, when someone asks you 'You know that change for the PEAR email library, what was it?' you can come back with an answer.
The log might look like
```
[23-02-2015] my/php/file.php [opened]
[24-02-2015] my/php/file.php [opened]
[24-02-2015] my/php/file.php [deleted]
```
45. A free SMS service for farmers in 3rd world countries so they don't get scammed by traders on their product. They text the service something like 'Wheat' (would have to be fuzzy because they're probably shit at spelling...) and it replies with the price you should expect to gain from it.

46. AN amazon monitoring program that monitors whatever products you tell it to and it'll tell you when it's 
a) dropped in price
b)a new marketplace seller has added the item and is lower than the previous one
Alternatively, you can give it a price and if it ever reaches that price, it'll email you.

47. A site generator based on markdown files and no setup.
You send the file over to the server and it renders it for you, that's it!

48. A better version of the Nicepage chrome extension I made

49. A program that creates a LERP between two images. maybe specify the amount of frames you want for the lerp?
i.e.
```
tween_images(from_image, to_image, frames=5)
```
Would create 5 tween images.

50. A program that finds dead functions (ones not used).
It finds all functions in a file, greps through each function name. If that grep brings back nothing, then it's not used (provided it's only used in one codebase that is..)

51. An open source, free hostel booking program similar to dorm booker, but free and more featureful

52. AHK script. Add an item to the context menu that says 'move to VST directory?'. Clicking that will move the selected file to your VST directory

53. ```where-is``` a program that helps you find config files etc...
i.e.
```where-is grub config```
Should output a possible list of locations
```/boot/default/grub.d```
```/etc/grub.d```

54. A MIDI drum track linter.
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

55. A command-line utility to grep through sql. 
i.e. ```grepsql "sarah"  --db="people" ```

56. A design linter for css files. Given a css file it highlights the bad aspects of it. 
I.e.
```css-lint style.css```
Would output
```
- found 12 font sizes, more than 3 is overkill
- found multiple font families used, 2 is recommended
- found multiple different colours used. Recommend no more than 5
- found large amount of differing values for margins 
- found large amount of differing values for paddings
- found non standard media query sizes...why?
```

57. A gui for partitioning USB's/disks.
Use electron and the style of form in the codepen.
should be able to do http://superuser.com/questions/878108/8gb-memory-stick-only-showing-49mb
without using a cmdline.

58. A GUI to easily manage adding/removing context menu entries.
Built using electron. also using that codepen form style.

59. Make a PR to chrome's devtools. When you ctrl+p in a CSS file, the matches are badly prioritised.

60. A jra util that shows a raw string. i.e '1 2 3 4 5' would return '1SPACE2SPACE3' or whatever the space code is...

### Created
http://util.joereynoldsaudio.com/util/rawtext

61. A joke searcher. Given a JSON file of jokes and their category, it'll dynamically load them in.

62. A command-line utility that gets the extension of a file (Write it in scheme?)
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

63.  Zip / Postal Code Lookup – Enter a zip or postal code and have it return which city/cities that are in that zip code.

64. Fetch Current Weather – Get the current weather for a given zip/postal code.

65. A website which contains a database of instrumentation for songs. You can seearch for a song that a 2 violins and a piano and then it shows the matches. This is a huge project.

66. Pokemon cry analyser - given a pokemons cry, analyse the waveform and return back the pokemon it came from. 

67. word ladder that goes from one word to another ideally in the shortest amount of steps as possible
e.g. Dog to Fig = Dog -> Dig -> Fig
or
Dog -> Fog -> Fig

68. A soundex-ifier for songs, it changes the lyrics of the song to words that sound like that word. 
i.e.
'Will the real slim shady please stand up' -> 'Bill the seal tin baby please stand up'.
It should have an API similar  to this
`soundex_song('slim-shady.txt', amount=0.75)`

The amount parameter should be how 'soundexed' the song is on a scale between 0 - 1. 1 would be every word, 0 would be no words.
