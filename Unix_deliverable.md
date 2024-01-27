# Unix tutorial for Unit 1: Deliverables

[Unix tutorial from Griffith Lab](https://rnabio.org/module-00-setup/0000/08/01/Unix/)

## How to complete the Unix deliverable:

Work through all of the Unix exercises (1 - 28), typing the commands as directed into your terminal. 

Save the session (or multiple sessions, if you don't do it all at once). On MacOS, the Terminal program has an "Export text as . . ." function under "Shell" on the menu at the very top of your computer, and lets you save the session as a .txt file. Windows users might have a slightly different option. Note that the file is saved onto your computer.

When you save your session(s), be sure to name it/them according to the guidelines laid out in "Naming_files.md". 

Log onto the Discovery Cluster (DC). When you first log on, you'll find yourself in your home directory. Use the cd command to change to your directory under the "courses" section by entering: cd /courses/BIOL3411.202430/students

Use the ls command to look at the contents. Now you want to make a directory for your assignments within your folder. You can either stay where you are and enter (ex: I want to make a directory called assignments, and my username is jhenzy):

> mkdir jhenzy/assignments

Or you can cd into your directory and then make the new directory:

> cd jhenzy

> mkdir assignments

Refer to Session_2.pdf on Canvas, slide 18, for instructions on how to transfer your saved session(s) files(s) to your student directory. I'll walk through an example as if I'm a student and I've already created a directory called "assignments" using the steps above. I've saved my session txt file as unix_exer.txt on my Desktop.

From my computer Terminal or Mobaxterm (do not log onto DC):

> rsync -a ~/Desktop/unix_exer.txt jhenzy@xfer.discovery.neu.edu:/courses/BIOL3411.202430/students/jhenzy/assignments

Eh voilà! Try it out and if it works, post a message on the "Yeehaw!" Discussion board! 

![image](https://github.com/jamiehenzy/BIOL3411_Genome-analysis/assets/149628307/382f6efc-c3b5-4f07-9a5b-0aff23471d6f)

