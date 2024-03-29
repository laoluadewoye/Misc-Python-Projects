Created by laoluadewoye@gmail.com

Version Number: 1.1.0

All copyright information on the GitHub page. 

If there are any questions on the usage of this program, please feel free to 
email me.

# Hello, Welcome To SKLOverlay

## BACKGROUND

I wanted to create this after taking a few classes that utilized some network
analysis concepts. I found that in alot of classes, I would create Python 
executables with the same structure.

Import data.

Preprocess it. 

Run the model, get results.

And, if I could ever figure it out, paste it in a Matplotlib.

I quickly grew good at it, but over the Summer of 2023 I started to wonder if
I could ever figure out how to automate this.

And automate it I did. 

To a degree, this should be able to enable the batch testing of several 
algorithms on one dataset with some basic configurations. More importantly,
this should be able to happen with little more than pressing the numbers near
the top of your keyboard. And maybe copy-paste the path of the folder you want 
to export your results to.

As a bonus, I wanted this program to be as modular as possible for quick
debugging and modification. You may find that it isn't suited to your needs,
and in that case, it should be self-explanatory to plug your own code in 
somewhere.

## FILE INFORMATION

This instruction manual assumes that I haven't figured out a way to turn this
into an executable yet, meaning you, the user, have either gotten this from
GitHub or directly from me.

In the main folder of the program, are several Python files and at least one
folder named "SKLOCCustom". In order of filetype, then name-

SKLOCCustom - Contains all Python files for classification algorithms and
		classifier setup functionality.

SKLOCDataMods - Contains functionality for modifying your chosen dataset.

SKLOCDataset - Contains functionality for creating or importing a dataset.

SKLOClassMenu - The root of the entire program, contains the branches for all
		user functionality. Essentially software navigation.

SKLOCMainOps - Contains several functions that ClassMenu calls to. Keeping
		all the scripts in SKLOClassMenu made the file too long. 

SKLOCMetrics - Contains functionality for generating results, graphs, and
		spreadsheets

SKLOCRun - Contains functionality for Preprocessing, Model Fitting, and Model
		testing

SKLOverlay - The program used for running the entire application.

## PREREQUISITES

As implied, to start the program, you must run SKLOverlay.py using the Python
interpreter. Before you begin, however, have the following libraries
installed.

1. Python 3 
2. Python libraries
   1. os
   2. textwrap
   3. copy
   4. ast
   5. random
   6. time
3. Scikit Learn/SKlearn
4. Pandas
5. Numpy
6. Matplotlib
7. Openpyxl

You may already have these libraries installed, especially if you utilize
suites like Anaconda. Always good to check, however.

## STARTING THE PROGRAM

To start, run SKLOverlay.py. You should be greeted with a welcome box and
your first selection. You will be asked to enter 1 to proceed. Once you
enter 1 and press enter, you will see all the functions of the program.
Selecting options will be how you will navigate through the program as a
whole.

After leaving the introduction box, the Classification menu box will be
generated. This is the main menu of the program and is where all major 
classifiers and datasets are managed. Each option will be labeled with a
number preceding it. All menus and options came across in the program will
have this structure, with 0 being used to go back a menu or exit an activity.

Below is a short description of each main option.

0 - enter this number to exit the program

1 - enter this number to display a list of classifiers you made. You can 
	choose to edit one.

2 - enter this number to create a new classifier inside the program.

3 - enter this number to choose an "active" classifier.

4 - enter this number to delete a classifier. 

5 - enter this number to display a list of datasets you made. You can choose
	to edit one.

6 - enter this number to create a new dataset inside the program.

7 - enter this number to choose an "active" dataset.

8 - enter this number to delete a dataset.

9 - enter this number to fit and test one model.

10 - enter this number to batch fit/test multiple models at once.

## ACTIVE STATUSES

Typical activities within this program are-

1. Creating a classifier object
2. Creating a dataset object
3. Fitting and testing how well a classifier can correctly classify data.

Step 3 can be done through options 9 or 10. However, entering into these 
options prematurely could cause confusion, and even crash the program. Thus, 
active statuses are at the top of the menu display. 

You must use options 3 and 7 to select an active classifier and dataset. 
When both are chosen, options 9 and 10 will start working. 

First though, a classifier and dataset must be created.

## CLASSIFICATION ALGORITHMS

This program is made to make classification through SKlearn easy. Thus, all 
algorithms within this program are 1) in SKlearn and 2) specifically for 
classification. In the future, regression can be built into the program. 

In the program, the words "algorithm" and "classifier" are used 
interchangeably.

You can edit a classifier (option 1), create a classifier (option 2), 
select an active classifier (option 3), or delete a classifier (option 4).

First, choose option 2 to create a classifier.

### ALGORITHM CREATION

When choosing an algorithm, you will see a list of different models. Like the
previous menu, use the numbers to select which one you want. However, 
something interesting happens if you change your mind at this point.

In the program, you don't just create an algorithm. You also nickname it and
customize its parameters, which are stored as a dictionary. This allows-

1. To edit your algorithm's configuration after the fact as all old parameters
	can just be added back in.
2. The above then means remembering the algorithm object can be completely
	disregarded. All that is needed is what algorithm and what edits. 
	remembering the object in storage isn't necessarily required.

However, this also means that each modification results in a completely new
algorithm being remembered in storage before old edits are applied back. 
This whole process starts with choosing your algorithm which means if you 
change your mind, something needs to be sent back. I decided the best way to 
handle this conundrum was to just send a default Random Forest classifier back 
as the choice. 

You will be warned about this when it happens. This is the only option where
this will ever happen.

Once you have decided on which model you want to use, you will then be asked 
to nickname your program. Here, you can type any character you want. This
also is good for needing to know which algorithm is represented in charts
later on.

Lastly, you will be asked to edit the parameters of the algorithm one by one.
If you choose to do no edits, enter 0 and the default configuration of that
classifier is used. This menu assumes you know what each of these parameters
means, so look up the classifier on Sci-Kit's API documentation if you don't.

### EDITING THE ALGORITHM.

If you believe you made a mistake in your algorithm, or wish to change it, 
choose option 1. This will display a menu that lists all nicknames of the 
models you created, along with their dictionary of the modifications
previously made. 

Choosing one of these options will take you back to the customization menu
from before. Make the modifications you need and then press 0 to exit and 
save.

### SELECTING AN ACTIVE ALGORITHM

To establish one classifier as the "active" classifier, use option 3. In the
same way you choose a classifier to edit, choose a classifier to activate.
Back in the main menu, you will now see the nickname of your classifier
along with its index number beside "Active Classifier".

### DELETING AN ALGORITHM

Deleting an algorithm uses the same mechanics as choosing an active algorithm.
The algorithm you select will end up being deleted from your list of models.
There will be no warning to confirm your deletion, so be sure and be careful.
You do not need to remove the active status to delete your model, but you will
notice the "Active Classifier" status turns back into None and needs to be 
reselected.

## DATASET CREATION

After you finish preparing your algorithms, next is time to prepare your
datasets. Or prepare your datasets first. Whichever way you prefer.

Use the 6th option to create a new dataset. The first option you will be given
is whether you wish to use a sample dataset already prepared, or a dataset of
you're own choosing. Use 1 or 2 to decide.

If you make a sample dataset, you will first be asked to nickname your
dataset. Then you will be asked to choose which sample dataset you want to
use. Half are actually samples prepared, while the rest are ways to generate
data provided by SKLearn.

If you are providing your own dataset, you will first be asked to provide 
the path to your dataset file. Below is a list of ways to provide data.

1. Excel / LibreOffice spreadsheets.
2. Comma-Seperated Value (CSV) files.
3. JSON files
4. TXT files (this is more general, know how your file is organized before
		choosing this option as it may not work)

Note, both local files, server files, and web links to data can work. As long
As the actual file can be reached and parsed, it is viable.

Another note, the ways you can modify your dataset within this program are
limited and can be tedious. Major modifications to your dataset should be 
done before even running this program.

After choosing your dataset, you next are instructed to make modifications to
your dataset. You are able to remove columns, assign a Y column, assign a
train-testing method, and choose one preprocessing option (at the moment). You
can also reset your edits if you made a mistake you wish to take back.

You are required to assign a Y (class) column and establish a training split
before you are allowed to exit this menu. This is to enforce a complete
setup for preprocessing.

### EDITING THE DATASET

After you have created a dataset, you can use option 5 to edit your dataset. 
You will be taken straight to the menu to modify your preprocessing options.
Nothing is required this time, so you are also able to immediately return
back to the main menu. 

### SELECTING AN ACTIVE DATASET

Like selecting an active classifier, you can select an active dataset. It is
a similar process, choosing option 7 and choosing the name of your desired 
dataset.

### REMOVE A DATASET

Lastly, removing a dataset is like choosing the active dataset. If you remove
a dataset that is currently active, the active status will reset to None and
you will have to make another selection. 

## ALGORITHM FITTING AND TESTING

Finally, once you have both an active classifier and an active dataset, you 
are ready to perform fitting and testing. The actual process, as promised, 
is reduced to as little button presses as possible while the program itself
handles preprocessing, fitting, and test results. 

### SINGLE CLASSIFER TESTING

With the nine option, you are able to do a single test with one classifier
on a dataset. You will have three options, all of which you will have to
do in order. Availability status will be shown to guide you on which options
are available. 

In order, the options are Fitting --> Testing --> Results.

Fitting trains the model on the training portions of the data.
Testing pits the model against unfamiliar data to see how much it is able to
correctly classify. The model's predictions are returned from this.
Results compare the predictions with the answers and develop a list of
statistics based on the findings. 

From there, you can use the results menu to generate a Confusion Matrix and an
Excel spreadsheet.

### BATCH TESTING

The ten option allows you to batch-test multiple models on a single dataset. 
You will first be asked for the folder you wish to place your results in. If 
you do not answer, or provide a location that the program is unable to find, 
it will default to the folder the program is running from. 

Next, you will be asked whether you wish to batch-test different algorithms or
if you wish to batch-test one algorithm multiple times. 

If you wish to use multiple algorithms, choose the first option. From there, 
you will be asked to select as many different classifiers as you want 
(including dupes) until you enter 0 to end selection.

If you wish to use the same algorithm multiple times, you can choose the 
second option (you can also choose the first and spam that option multiple
times for the same outcome). When choosing option 2, you will be asked whether
you wish for there to be a shifting parameter, or everything staying the same.
This gives the opportunity to see what configuration of any given classifier
works best for the data at hand. You will then be asked how many times you
wish to run this model for data.

Configuring your shifting parameter will be similar to initially customizing 
your classifier, except you will also be asked to set an interval that will
increase or decrease the value you're changing. To decrease your value, add
a "-" right before your number (i.e. -50). As with customization, check
SKLearn's documentation so you know what you are changing.

Once complete, there is nothing further needed to do. If all is properly 
configured, several bar graphs and an Excel spreadsheet with data should be
exported to your desired folder. 

## ERRORS OR SUGGESTIONS

If you have anything you wish to see in this program, send questions to 
laoluadewoye@gmail.com.









