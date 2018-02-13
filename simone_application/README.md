Simone's read-me

To all reading this.  I am sorry that this may be a bit crude--I mean this is why I am taking this class.  The last time I programmed prior to this was prior to obama's inaguration... But I digress.

to run the program basically, do it as you would any other python program:
python ./src/application_project.py ./input/percentile.txt ./input/itcont.txt .\
/output/repeat_donors.txt
This is in the run.sh shell.

My logic was as so:
First, you had to input data and then get rid of all garbled things that didn't make sense and pass them over.  Next, you had to determine if this donor was unique.  Next, you needed to make a dictionary of all donors, as you need to start with a list of all donors to determine if it was unique.  For this I used an if statement, as if the name and zip code combination had not been seen before that was a new contribution and an array for my dictionary was created for this person.  Otherwise, this donor was already in my dictionary, so I appeneded their array and went on to finish the code by grouping by zip code, ensuring it was the calendar year desired (in this case 2018), adding contributions by zip code, determining the percentile as stated on the page, and printing to the output file. With the desired output, the assignment was complete, and being that my original language was c I needed to return or close something at the end of the program, so I closed my output file.  I decided to manually open my output file as opposed to using with statements, as I thought it might run faster, as then I am not constantly opening and closing my output file.  I was also concerned if I used a with file, my previous data would be overwritten, however, I guess I could have always addended lines instead of "writelines".  Also, old habits die hard.

The dependencies are basic python libraries including math, sys, and date all declared at the top.  You also need input files at a reasonable size unless you have a huge cluster.  I actually tested my code using 2017 data, but i could only grab a part of it as the 2017-2018 data page was over a gig of text file.  My measley 10G partition of virtualbox with ubuntu could not handle that.

One deficiency I had in my program was that the date was a constant that you had to write directly into the source code.  If I were to fix something to scale this code up, I would make it so you inputted that constant in the command line with the desired files.  However, by the time I thought about this, it was late, and I didn't want to risk ruining my running code near the button.  In C, occasionally something like this would ruin an otherwise fine code--have to test this out so far in python.  So far, python seems simpler, more robust, and I am not spending half a day defining variables or doing everything the hard way.

This was my code step by step, you can decide to not read as my code was there.
first import libraries
then make sure you can bring in whatever file that you would like as an input from the script.
Then, I set constants for each column of interest as stated in instructions.  This includes a variable for the year, which I set to 2018.  This can be changed at any time by opening my program and going to the variables section and putting in a new year.  
Then I had to declare my dictionaries, and create my percentile variable.
next, I opened my files, both read and write.  For my read files I used with statements so I didn't have to worry about closing them.  However, for my output I wanted to keep the file open the entire time I was writing code and then close it at the end.  Logically this should help the code run faster, but I am not sure if this is the case.
I read in the lines and made an array using the pipes as delimiters.
Then I excluded anything with stuff in other_id, and without stuff in other boxes, or zipcodes that were less than 5 letters.  Without attaching a dictionary of all names and slowing my program down to a crawl, I could not eliminate garbled names (and with some of the names these days... I might eliminate too much).
I then reassigned my array to new variables to make life easier.
I also then turned our date field into a real date and ran over those that don't have a date.
I created a unique ID from name and zip code as desired.
Then I used an if statement to create a new variable/input (not sure of the terminology) if the unique ID had never been seen before, or addend that dictionary if the unique ID had been seen, now grouping our repeat donors together.  The next few steps only happened if it was a second addendum, and thus a repeat donor.  
Next I went towards the desired output for the current calendar year 2018.
I found the repeat donors for 2018.
I then did the percentile math, however, I didn't round up as the python index starts at 0 and the wikipedia index starts at 1.
I then printed the lines to the output file with pipes between desired data.  I printed out all data, as these were all repeat donors as stated above.  You said you wanted the data to be streaming and continuous, so I printed all repeat donors additions as they came in.
Lastly, I closed the output file--I mean since my original language was C, you gotta return something.

