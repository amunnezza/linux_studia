Alcuni dettagli importanti
shebang 
comments 
shell built ins variables 
more 

For class make a new directory that's going to house our project 
So we'll get into the show class director here we'll create local users make sure local users will change
into that directory.
The reason why I'm calling this directory local users is that we're building toward creating a script
that is going to create local users or users that are local to a system.
Later on in the course we'll be creating a script that will add remote users or users to systems other
than the one that your script is executing on.
But for now we're focusing on local users.
Now let's create the vagrant file with vagrant Annette and we'll specify the class image that we're
using
in order to run and execute the shell scripts that you and I are going to be creating we need to be
inside the virtual machine in side the Linux system that we've created.
So we'll get in there by connecting over SSA to a run vagrant SS age and that will connect us to the
virtual machine that we just created.
Let's change into the forward slash vagrant rectory with seedy forward slash vagrant and press enter.
I'm going to run LSA dash l here and that is a long listing format of the Ellis command the dash L and
it just displays the files that are in the directory.
Now it's important to note that we have the vagrant file so on our current system in forward slash vagrant.
It's the same as our local system.
As in your home directory shall class local users.
So as you can see here this is my home directory.
It mounted slash vagrant to this local system.
So whatever we create inside the VM and the vagrant directory ends up on our local machine in that local
user's directory and vice versa.
So here you really have a choice to make.
You can either edit your scripts inside the virtual machine using nano emacs or vim or you can use the
editor on your local system.
So for me I'm going to use vim because that's my favorite editor.
I've done a class on it.
I could talk hours and hours about them.
I totally love it.
So that's what I'm going to do.
But I will demonstrate what it looks like from the other side here so I'm going to go ahead and start
creating the script.
I'm going to use my vim command vim and I'm going to name the script L user dash demo 0 one dot S H.
Now I want to point out here that file names with shell scripts really don't matter.
We'll get into what does matter in just a second.
So by convention shell scripts can end in dot s h but they're not significant.
The file extension is not significant like it is for example on windows when something has a dot exec
file extension.
That's not the case on Linux.
We could name this anything we could just name it our user test demo or one or DSH or Bob or Fred or
any name that is a valid file name and that will work as a shell script.
So let me edit this file real quick and I'm just going to put a little bit of information in here.
A pound sign an exclamation mark Ford slash been 4 slash bash and I'm going to save my changes here
and what I'm going to do to show you what happens with the file sharing I'm just going to do an Alice
in this directory.
You can see that the El user Desdemona Wanda s each file was created.
But I'm going to open up that file in an editor on my local MAC system and so I'm going to use Adam
in my case.
So here I have that same file open in the Adam Ed but as you can see it's in the shell class.
Local users.
So that's where it's at.
On your local system.
I'm just gonna add another line of text here.
I'll say hello from the main O S and I'm going to save my changes now if I go back to the terminal where
I'm logged into the virtual machine and look at this file those changes will be there.
Let me go ahead and just close up this file to make sure nothing is going to interfere with that will
go back to our terminal and if we display the contents of that file El user demo one that S H.
You can see that this new line of text has been added so that's what I'm talking about your decision
of whether to edit from your local machine or whether to edit inside the virtual machine.
Again I'm going to primarily edit inside the virtual machine here and I'm going to get back into that
file vim El user dash demo 0 1 and by the way El user is just my personal shorthand for local user.
So that's what that's about.
Now let's talk about this very first line in this shell script.
It's a pound sign followed by an exclamation point and then a path to bash which is forward slash Ben
or slash bash.
This is called a shebang.
The reason why it's called a shebang is the pound sign is sometimes called a sharp.
If you've ever played music or read music you'll know that the pound sign looks very very similar to
a sharp sign of music.
So a lot of people call the hash mark or hash symbol or pound sign.
Sharp as far as the exclamation point.
Slang for that is bang.
So we have sharp bang but an inexact contraction of those two words is shebang.
So that's where shebang comes from.
And you want to start out each shell script with the shebang.
Sharp bang and then a path to the interpreter.
So what will happen when you execute this script is that the commands inside the script will be interpreted
by 4D slash band forward slash Bash.
Now if you had put in another interpreter for example let's say user bean Python or band Ruby or whatever.
Now that's a ruby script but we're doing shell so we'll keep it as bash.
So really what happens is when you execute this script Ben Bash we'll get executed and the file name
actually gets passed to that script and what happens is bash then executes everything in this file.
I'll demonstrate that later in the course by showing the process table and so on.
But for now just know that the first line the shebang determines what is going to execute the commands
listed in the file that you're creating.
If you do not supply a shebang and specify an interpreter on the first line of the script the commands
in the script will be executed using your current shell.
And that may not be what you want.
For example if you have some bash specific items in your shell script and you happen to be using the
CSA each shell when you execute it then you're gonna end up with some errors.
And this is really important especially if you're working with the team you're writing a shell script
and you have no idea what Shell the other person will be using when they execute this.
So you want to be very explicit use the shebang and make sure you specify which interpreter that you
want to use for the script.
So I want to remove this line we added in the other editor and what I like to do at the top of my shell
scripts is to give a goal or comment about what's going to happen when the shell script is executed.
So when you start a line with a pound sign it's actually a comment.
Comments are not executed.
They're just simply there for us humans only with the exception of course of the first line which is
a special line.
But in all other cases that information there is just for us humans.
So we can put anything after the pound sign after the comment and it's not going to affect the functioning
of our program.
And so here at the very top of the script I'm going to tell what it does
so this script just displays various information to the screen.
That's all this script does.
And so that's what I'm going to put at the top of the file.
Now when you start making very long and complex scripts and you come back to it a year later or someone
else looks at it and they're not sure what it does.
Just having a few notes at the top of the script can really help someone out there.
I'm going to add another comment.
We're going to say what we want to do is display the text.
Hello and we're going to use a command called Echo and then supply the text we want to display to the
screen which is helo and we'll put that in single quotes.
I'm going to save my changes and then I'm going to exit out of the editor.
So just a minute ago I talked about file extensions and how they weren't relevant.
Now what is relevant is an execute bet on the script.
Now hopefully by the time you've got to this course you understand file permissions but very quickly
I'm going to do a quick review of them.
We'll just take a look at our previous LSA output here as a demonstration.
So these are w characters are stands for read W stands for right and what goes here is X for executable
and there will be three sets of these three permissions.
So we have RW dash our dash dash dash dash.
So the first three characters here represents the permissions of the owner of the file.
The next three characters represents the permissions that are granted to the group in the file.
In the last three characters here represent the permissions that everyone else on the system has to
this file.
So in this case the vagrant user.
This is the user as read write permissions.
The vagrant group has read permissions and then everyone else who is not the vagrant user or in the
vagrant group has read permissions to this file.
What we want to do is add execute permissions so that I you and anyone else can actually execute this
file and how we do that is with command.
So due to mod 7 5 5 0 user demo or 1 And now let's look at the permissions now they are RW X which is
read write execute read execute for the group read execute for everyone else that's not user or the
owner of the file and in the vagrant group.
So what this does is if you have read permission obviously you can look at the contents of the file
if you have right permission that means you can change the contents of the file and if you have X permission
that means you can execute the file.
Typically we want to rewrite and execute for ourselves and read and execute for other people.
By the way if you can't read the file then you can execute it because you can't see the contents that
are going to be read in by the interpreter and execute it and so on.
So typically the default permission you want to put on your shell scripts is 7 5 5.
So really quickly review where does this 7 5 5 come from.
Well read you can think of as 4 right as 2 and execute as one and you add those together.
So 7 is four plus two plus one which is read plus write posts execute so 4 to one is 7 and that is for
the owner of the file 5 is read which is 4 plus 1 execute.
So that's 5.
And that is for the group.
So this corresponds to this middle set here.
5 again is the same thing 4 plus 1 is 5 and that is for everyone else.
So if this is a little bit confusing for you or you don't want to remember the specifics.
Just remember that the default permission we're going to be using is to mod seven fifty five on the
name of your script.
Okay.
So now we have a script.
It's executed.
Also how do we execute that script.
Well the first thing you want to do is type in period forward slash and the name of the script and then
press enter.
So the output of this script is simply the word hello.
And that is because of the command echo Hello that we placed in the script.
Now I want to point out here that dot represents this directory.
So for example if we did seed space dot we wouldn't go anywhere we would still be in the same directory.
Dot dot represents the parent directory.
So if we did see dot dot we move to the directory above the directory we were in.
Let me go back in the vagrant directory so dot is this directory.
And as you can see the forward slash is the directory separator so dot forward slash means this directory
is dot forward slash is a directory separator and then the name of the script is the file.
So that's how you execute a file in your current directory.
Dot forward slash and then the name of the file.
This is equivalent to the full path.
So we could actually run or slash vagrant l user demo 0 1 and hit enter as well.
And again the reason why this dot slash works is because dot represents the current directory which
is a Ford slash vagrant.
And then we specify a Ford slash which is the same as this Ford slash and then the name of the file
which is the same as the name of this file.
So that's why that works so that's how you do it.
So just remember tomorrow some 55 dot Ford slash and then the name of the file by the way we could have
named this file anything again dot DSH doesn't matter as a matter of fact I'm going to rename the file
really quick l user demo I want to Jason it's a matter of fact that's a typo I even misspelled my own
name incorrectly but it doesn't matter I'm an executed anyway dot org slash J a o s n and we get the
same results I'm going to move that back
let me show you what it looks like when you don't have the execute bit set let's just use the touch
command to create an empty file that's what touch does touch either creates an empty file if one doesn't
exist or it updates the lacks access timestamp of a file do an Alice here in this directory.
So we have blood out S H There is no executable bit set on it so if we do dot forward slash Blau S H
and hit enter we get permission denied because we do not have execute permission on that file so that
is what's gonna happen when you don't have the proper permissions set so again make sure you do trim
on seven fifty five in your file and you'll be good to go let's continue working on our script we'll
use vim and edited our file here.
So let's look at this echo command I kind of glossed over it to just get it started here and show the
execute permissions and talk about file extensions and that sort of thing.
So the echo command just displays whatever is passed to it.
Well where does echo come from.
Well let's check it out back on the command line Echo is actually a shell built in.
That means it's a command that's built within the shell it doesn't require any external programs to
execute it's really just part of bash.
So how do we know it's a shell built in.
Well you can use that type command which is also a shell built in to show you if it's a shell built
in or not.
So if you do type space the command you're interested about which we are interested in echo it says
Echo is a shell built in.
So if you want to see all instances of Echo on your system you do type dash a for all and then type
echo.
And so it listen in the order that they will execute.
Echo is a shell built in.
So really that's what's going to execute when you type echo we'll just type echo now on the command
line echo Hello.
Just like we had on our script and press enter and the shell built in is what is executed.
Now we can force the execution of this by using the full path user bean echo and then pass something
to it to display what you want to do is actually anytime there is a shell built in to use the shell
built in.
So don't specify the full path.
Just use echo and it's a little more efficient because again it's built into the shell the shell doesn't
have to request an external program to do some extra processing and what have you.
So just use the shell built in when it's available.
Another advantage of using shell built ins is that it's a more portable for example if the echo command
is on Ben echo and some systems and it's on user been in another system then you might run into some
issues there.
But if you use the shell built in you avoid all of that so you can kind of think of these built ins
as free stuff you get by using bash and there's more than just these built in commands and functions.
There are built in variables and all sorts of things which we'll be getting into soon enough.
By the way if you want to get help on a shell built in use the help command so we'll do help echo and
a lot of that information scrolled off our screen quickly someone to pipe it to less it's a pager so
we can page up and down to this output I'm going to pipe it to less it enter and it says echo rights
arguments to standard output display the arguments on the standard output followed by a new line.
So that's what the echo built in does.
Let's look at an example of a command that is not a shell built in one command that comes to mind as
uptime so uptime just displays how long this system that you're logged into has been up will do type
dash a pass and uptime to that.
This is uptime is actually user been uptime that's what it gets executed when you run uptime.
So if you run help uptime you're not gonna get any help because it's not a shell built in.
However if you wanted to get help on uptime you would use the man command which is short for man pages.
So man or manual man uptime and press enter.
So that's how you get information on how to use commands that are not part of shell built ends and we'll
be looking at man pages along the way as well as help or built in Shell commands.
By the way to exit out of man type Q And it's the same way with less if I didn't mention that as well
you just type Q to exit that page nation system there as well remembered that a shell script just executes
ever command inside that script just as if you were typing it on the command line.
So if we look at the contents of our script here if we were to do this pound space display low and press
enter nothing happens because the pound sign is a comment and comments aren't executed and if we type
in the next line in the script echo hello and press enter.
Then we get Hello displayed to the screen.
And that's exactly what happens when we execute the script.
By the way this simple echo command can come in really handy when you're debugging or writing scripts.
You can use it to show exactly what is going on inside the script along the way.
Now let's get back to editing the script let's assign a value to a variable
let's call this variable word.
We'll follow that with an equal sign.
A single quote script and end it with a single quote.
I'm going to save my changes now variables are simply storage locations that have a name.
In this example the name is word you can think of variables as name value pairs.
So if we were to access the variable of word the value that would be returned would be script.
Unlike some other programming languages when you're creating variables you don't have to specify its
type whether it's a string or an integer or anything like that you just assign it a value.
By the way I want to point out that it's very important that there is no space in between the equal
sign.
So it's the variable name followed by an equal sign without any space.
Again without any space then the assignment in this case we're assigning a string and strings are enclosed
in quotation marks either a single quotation marks or double quotation marks.
By the way I recommend that you use a descriptive name for your variables although it's not required.
This simply just makes the script easier to read.
Now think about someone else who's going to be reading the script or maybe even yourself if it's a year
later or a long time after you've originally written the script.
It would be easier for you to tell what's going on if the variables had meaningful names.
Now as a quick aside I want to tell you about someone I worked with whose last name started with Z and
so everything he created contained a Z.
If you looked at his home directory he had a bunch of shell scripts one shell script was name Z.
The next shell script was named Z.
The next shell script was named Z and there was a shell script.
Ze one one name ze to one name.
Xie xie xie xie 1 1 2 etc. just went crazy like he had no imagination other than the letter Z.
And then when you opened up one of his scripts and looked in them all the variables were the same.
Z equals blah ze 1 equals blah Z was blah.
He was the only person that had any kind of clue of what was going on when his scripts because they
were almost impossible to read.
So again using something like that works it's just not recommended by the way there are some rules around
variable names variable names can contain letters digits and underscores and they can start with letters
or underscores but they can not start with a digit.
So for example word is a valid variable name.
Word 1 is a valid variable name underscore word is a valid variable name.
However 3 word is not a valid variable name.
Also you cannot use dashes so something like this a dash word is not a valid variable name it's invalid
you can't use that.
One more example would be an at sign you can't use that as well.
E at male equals something is not going to work.
Let me get rid of these example names here.
Now that we've assigned a value to our variable let's go ahead and use that variable
so we'll just to echo space.
Double quotation marks.
Dollar sign.
The variable name which is a word in end it with a double quotation mark so when you reference the variable
by name you get its value back.
Now to do that you have to proceed.
The variable name with a dollar sign.
So when we want the value of word we use dollar sign word.
Now you may have noticed that in the previous echo statement I used single quotes but in this echo statement
I use double quotes single quotes prevent the expansion of variables.
So if you want echo to display exactly what you specify put it in single quotes if you want variables
to be interpreted make sure that you use double quotes.
By the way we're just using the echo shell built in for now.
But this concept of single quotes and double quotes apply to other commands as well to say that another
way it's not because we're using echo that this expansion happens with double quotes and it doesn't
with single quotes it's the quote to themselves that is causing this expansion or not.
And then you can use this functionality with other commands not just with Echo.
So let's execute the script and see what happens okay.
We get Hello which is from Echo Hello.
Then we set the word variable to equal script and then we displayed that word variable which actually
in turn displays the word script by the way you can do what I'm doing here.
As far as your workflow goes which is to open your editor edit the file exit your editor and then execute
the script.
Another thing you could do is actually open up a new terminal window connect to the vagrant system get
into that directory and then execute that script with the other terminal so you just switch back and
forth between terminals versus entering and exiting your editor all the time.
Just use whatever method works best for you.
For now for the rest of this lesson I'm just going to edit the script exit out execute the script and
so on.
So let's return to editing our script add a comment here of what we're about to do
okay we're putting dollar word which is our variable inside single quotes.
Now let's see what effect that has.
So as you can see using Siegel quotes displays exactly what is in the single quotes it doesn't do any
expanding or interpreting of the variables.
It's exactly what you specify.
So just keep that in mind if you're using variables.
Use double quotes if you want to be very specific and make sure that nothing gets changed use single
quotes.
Okay let's do some more editing here
so you can use variables with hard coded text.
So here we have some text that we just manually typed in.
This is a shell and then we use a variable which has dollar words so we want the value of that variable
to be returned.
Let's exit out and execute the script and see what happens
so it gets interpreted and the output is this is a shell script.
You can also enclose the variable name in curly braces and perceive the opening brace with a dollar
sign.
So the syntax is dollar sign.
Opening curly brace in the variable name followed by a closing curly brace.
By the way when you're reading scripts written by others you'll see both types of syntax being used.
You'll see the dollar sign with a variable name as well as the dollar sign including the braces in the
variable name.
Now let's execute our script and see what happens so we get the same exact output as the preceding echo
command.
It's we're just using the different syntax.
Now if we want to append text to the variable we have to use this dollar sign.
Brace syntax.
Let me show an example.
So if we want to append AMG directly after the output of the variable we have to use the curly braces.
Otherwise bash doesn't know that the variable is actually word W O R D and that the part that's not
the variable is I N G.
It has no way of knowing that unless you use the braces to separate the variable from the preceding
or following text.
Now let's execute this.
Says scripting is fun again.
Script is what was stored and the word variable i n g is what we card coded in the echo statement there.
So let's demonstrate how not to append text to a variable I was just talking about this.
Let's do this.
So this is not gonna work echo dollar sign a word IAG is a fine again.
BASH doesn't know that high energy is not part of the variable name by the way I didn't necessarily
mention this but by convention not by rule or syntax variables are in all uppercase.
That's why you used uppercase word as a variable name.
And that way you can typically easily spot what is a variable and what is not.
However since that's only a convention or a best practice and it's not enforceable by syntax then bash
isn't going oh I N G is lowercase so therefore it's not part of the variable name.
No that's not how it works you can actually use lower case variables and some people do so this will
not work.
Let's prove it here.
You get blank is fun for the last bit of output.
That's because dollar word IAG that variable doesn't exist so it doesn't expand to anything so there's
nothing there.
And it displays nothing.
And that was followed by a space is space fun exclamation point.
So that is what it gets displayed on the screen.
Space is space fun.
Exclamation point.
Now let's create another variable for a script here.
We're going to name this variable ending.
Again we're going to use all uppercase letters because that is the convention or best practice not required
but that's how we're going to do it.
We're not going to use spaces because that will cause an error.
So we want to make sure there are no spaces here.
We're going to use single quotes and type in E D and close it was single quotes because we're not doing
any variable expansion here.
We're just doing a strict assignment of E D to this variable.
Now let's combine these two variables that we've created
so as you can see we use this dollar sign brace syntax.
So this variable of word will get interpreted and then dollar sign ending here will get interpreted
as well.
So we'll get this is script and this should expand to add E.D. here.
So let's prove this by executing it on the command line.
Sure enough we get this is scripted because the word variable contains the value of script and the ending
variable contains the value of E D.
Now let's change the value that stored in the ending variable.
This is called reassignment by the way.
Now we're going to change the value that stored an ending to AI in G.
By the way you can overwrite the contents of the variables just using assignments or these reassignments.
So the first time ending is specified it's equal to E.D. when you access the ending variable.
That's what gets displayed.
But since the scripts are read from the top down just as if you were typing them in at the command line
when you changed the value of ending then anything that follows that will use that new value.
And let's prove that here we'll do echo dollar sign a word dollar sign ending is fun see where our changes
and execute our script so we have scripting is fun.
So word expanded to script the ending since we changed it to i n g span into AMG so scripting is what
you get when you combine word and ending together.
Again we use that special brace syntax so that that's cartel where one variable started and ended as
well as the other variable where it started and ended.
Let's do one more reassignment
will assign s to ending
hey let's save our changes and execute our script.
You were going to write many scripts in this class all right.
This brings us to the end of this lesson in this lesson you've learned a lot you've learned about file
naming file naming conventions how file names don't determine if something is a script or executable
or not.
It's actually the execute bit on the file itself that determines if you can execute it as a script or
not.
You also learned about beings you learned how to use comments effectively create a header in your file
and comment.
The script along the way you learned about the difference between a shell built in versus a normal command
on the system.
How to get help with shell built ends which is to specify the word help followed by the name of the
shell built in.
You also learn that you can get help about general commands on the system using man pages.
So man followed by the command again man and a shell built in will not provide any help but you can
get help from man bash or help and the shell built in.
Finally we talked about variables how to assign them not to reassign them.
We talked about single quotes and how nothing inside single quotes gets expanded or interpreted and
how things since I double quotes to get expanded interpreted such as variables we talked about the two
different syntax as you can use with variables one is just pre spending a dollar assigned to the variable
name and the other is pre printing a dollar sign and surrounding the variable in braces you learned
that that second syntax is required if you want to immediately precede or immediately follow that variable
with some additional data even though using the dollar sign and brace encapsulation method is a best
practice when working with variables.
I showed you the other method so that if you see other people's scripts you know what they're doing
and it doesn't come as a surprise to you.
Okay that wraps it up for this lesson.

