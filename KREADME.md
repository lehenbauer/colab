

The whole time you've got a colab session in existence, whether you're doing anything with it or not, you're paying a per-hour fee in compute units.   Or if you're on the free tier, you're using up your compute units.

So when you've got one running, it's a good idea to be doing work, and when you're done, to delete and release the session.  If you are upsampling a composition and the upsampling completes, the python code in the Jupyter notebook will automatically disconnect and delete the session.

## Use Co-compose with Jukebox notebook

the principle is to click the play button on all the notebook code sections.

Think of a Jupyter notebook as an Excel spreadsheet but with only one column and really big rows.  The rows can be text in markdown format or Python code.

Python doesn't do machine learning stuff directly but it orchestrates it.

### Check the GPU

first check the GPU by clicking the play icon.  Colab'll get an environment going for you and then after a few seconds or more will tell you what GPU you've got. You need Nvidia A100 or better to use 5b_lyrics model i.e. the best model.

And you've now got a Linux VM to run Python in.

### Connect to Google Drive

You need to mount your google drive so you can give the notebook files and get files from it.

Hit play on this and then go through the dialogs to allow it.

### Project directory on Google Drive

A directory that will contain your seed file plus whatever the software makes.

Go to your Google Drive and create a directory called like music_co_compose_3

Put the name into the notebook location there and hit play.

### Setup your project

You need to upload a WAV file to your project directory.  At WAV put in the name of your wave file without the .wav extension.

NOTE - You'll get better results if you conform the WAV file to mono.

* Artist - Enter an artist from the hyperlinked list documented just above the *setup your project* cell.  There are thousands.  By name not number.
* Genre - optionally enter one to four genres from the hyperlinked list.
* Prompt length - the length of your wav file that it should use as a prompt, 25 seconds is the max I believe.
* Initial song length - the number of seconds to generate.  i like 4.
* Total song length - the number of seconds for the whole song.  maybe it will make an ending?  if you want a two minute song and have a 24 second prompt then enter 144.
* Lyrics - put in lyrics here or it will make up gibberish for lyrics not that that's a problem lol.
* Note - notes you can put in that'll get inserted into your project directory.

### Set the number of clips

If using the 5b or 5b_lyrics models, set to 3.  Else I guess if you're on a T4 GPU, 2.  It might be possible to do more than 3 on an A100 GPU, I'm not sure.  A different notebook seems to indicate this.  That would be cool.

Anyway this means it'll make three four-second samples to choose from and guide the software every iteration.

### Setup and install Jukebox

Hit play to install jukebox.  This takes a while.

### Generate the beginning of your song

This starts the thing off by ingesting your clip up to 25 seconds and your parameters and generating the first three four-second samples.

### Open Clips

This is how you go about listening to the clips.

Note - the sound quality will be terrible.  The music has been downsampled to tokens and the wound will be noisy and have a lot of artifacts.  With practice you kind of get used to it.

### Make a branch for later use

You get to a decision point and more than one of the three clips sounds really good.  You want the option to go back to this point.  That's what this does.  That part works but I don't know how to select it to restart or have the workflow.

### Input song continuation options

Hitting play on this sets the variables for the next contiuation.  You pick which sample you want and then the next addition length (i just set it to 4 seconds) and playback_start, which I push by 4 seconds every continuation so that i listen to about 16 seconds when auditioning new potential four-second clips.

### Continue generating the song

### Open clips

Hit play on Open clips.  Within not too long, audio players should appear for your three clips or however many you're doing.

Audition each one.  When you decide the one you think is best, go back up to *input song contuation options* and enter the number in the CHOICE field.

I like an addition length of four seconds.  Long enough to tell the difference.  Short enough that it doesn't go totally into the weeds.

You can start pushing your playback start time up.  I like to have about 16 seconds or so to listen to.

If you don't like any of the continuations you can click the run_again checkbox in *Input song continuation options*.  Remember though to clear the checkbox after you have found something you like or it won't move forward.

### Upsampling settings

The stuff you're generating is at level 2 and sounds lousy.  You can upsample to level 1 and it sounds a lot better but to get it to sound as good as possible you want to upsample to level 0.

Upsampling takes about an hour of GPU time per minute being upsampled.

You pick your choice in upsampling settings and hit play and that configures the upsampler, which is next.

### Upsample your favorite clip

Hit play and if everything's good then eventually a level_0 folder will be created in your project folder and inside that an item folder like item_0 or whatever and inside that an item_0.wav or something.


