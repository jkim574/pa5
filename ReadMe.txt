Description

Many schools and other groups host events where they need to have volunteers help with a variety of the tasks from setup to serving to clean up.  In this program, you will create a solution to the organizers' problem of matching volunteers with events. The input will be a list of events and a list of volunteers and the program's output will be in multiple forms, a list of volunteers for each event and a list of events for each volunteer.  Read on for more information.

At the program's start there are no volunteers or events.  The user must read in events from a data file (option 1).  The data file may also include volunteer information.  The user may also manually add and remove volunteers.  Once the events have been loaded and volunteers are available, the user will create "matches".   A match means that a particular volunteer is assigned to a particular event.  However, there are restrictions.  The event must not be at its max volunteer limit, and the volunteer must have reported the event's date as "available".   Dates are indicated with integer values in the range, 1-30, inclusive.

A benefit to this approach is that the output from one run of the program, can be used as input.  However, duplicate event names and duplicate volunteer names are not allowed.  



Class Specifications p5.zip
Resource DO NOT EDIT OR SUBMIT THIS FILE
Resources contains several string constants to help students match the prompts and required output.

GraphNode DO NOT EDIT OR SUBMIT THIS FILE
GraphNode is an abstract class that defines functionality that is needed by both of the Event and Volunteer classes. Thus, it is the super type of Volunteer and of Event.. Each GraphNode has a case insensitive name and an adjacency list that maintains references to other graphnodes.  Not all methods are defined, thus it is an abstract class.

Event DO NOT EDIT OR SUBMIT THIS FILE
Event  is a sub-type of GraphNode.  Event's have volunteers as its adjacent nodes.

Each event will have following information:

Event Name (String; Case Insensitive, no duplicates allowed)
Date (Single Integer value between 1 to 30, both inclusive)
Number of Volunteers (Upper limit) (Integer, greater than 0)
Matched volunteers in the adjacent node list.
You will need to read event information from an input file. Event information will be in the format:

e; Event Name; Date; Number of Volunteers Limit;volunteer1 name, volunteer2 name


Ignore the spaces before and after the delimiters.  An event may or may not have volunteers already assigned.

For Example, a museum field trip with no matched volunteer could be entered with either of these lines:

e;Museum FieldTrip;12;40; 
E; Museum FieldTrip; 12; 40;
In the above example, Name of the event is "Museum FieldTrip" without the quotes, event date is 12 and the limit of the number of volunteers needed is 40.

After reading and parsing (interpreting) the event information from the file, add this event to the list of events in the event manager.

For adding the event to the list of events, check if this event already exists. Duplicate event names are not allowed.

If event name already exists: skip this event and continue to the next line in the file.
If event name doesn't exist, then add this event to the event list (Only if all the matching conditions are satisfied i.e., you are able to create all the matches between this event and this event's volunteers; otherwise skip this line). Sort the event list by event's name after adding the event. Also, create matches between the given event and volunteers. Hint: add volunteer to event node and add event to volunteer node.  Check "Events" specification for how to create a match (edge) between given event and its matched volunteers.
Volunteer DO NOT EDIT OR SUBMIT THIS FILE
Volunteer  is a sub-type of GraphNode.  Volunteers have events as its adjacent nodes.

Each Volunteer will have following information:

Volunteer Name (String, Case Insensitive)
Dates available (list of integers, between 1 to 30, both inclusive; number of dates could be zero or more than zero)
You will need to read volunteer information either from the file or via the main menu options for adding and removing volunteers.

When reading volunteer information from the input data file:

Volunteer information will be in the format:

v;Vounteer Name;date1,date2
Ignore the spaces before and after the delimiters.

For Example, these two represent the same volunteer and duplicates are not allowed:

v;Jim;12,2,15
V; JIm; 1, 2,30
In the first example, Name of the volunteer is "Jim" without the quotes and volunteer is available on dates 12, 2 and 15. Not that dates need not be in sorted order. The second line would be ignored and would not change the information for "Jim".

After reading the volunteer information from the file, you need to add this volunteer to the list of volunteers in the event manager.

For adding the volunteer to the list of volunteers, check if this volunteer already exists in the list.

If volunteer already exists: skip this volunteer and continue to the next line in the file.
If volunteer doesn't exist, then add this volunteer to the volunteer list. Sort the volunteer list by volunteer's name after adding the volunteer. 
Ignore the line if there are duplicate dates or one of the dates are invalid.
 Note: Check if volunteer exists with volunteer name only i.e. there should be only one volunteer with a given name.

Matching

When a volunteer is matched with an event, it means that the volunteer is on the event's volunteer list and the event is on the volunteer's list.  See GraphNode class for how each type maintains its list of adjacent vertices (nodes).

For each event, you will need to create matches between the event and each of the volunteers with the given names.

Event Name (String; Case Insensitive)
Volunteer Name (String, Case Insensitive)
Additionally, the user can select "add a match", and the main program will prompt them for the event name and volunteer name.

You can think of matching between event and volunteer as adding an undirected edge to a graph. To create a match between an event and a volunteer, you need to add the node corresponding to the volunteer to the adjacency list of the event and you need to add the node corresponding to the event to the adjacency lists of the volunteer node.

After adding the node to adjacency list, sort the nodes adjacency list in ascending order by the node's name. 

A match will be created only if following conditions are satisfied:

If Volunteer is available in volunteer list.
If Event is available in event list.
If Volunteer is available on the date of the event.
Volunteer has not been matched to any other event on the same date.
Event has not reached its volunteer limit.  
 

EventManager DO COMPLETE and SUBMIT THIS FILE
EventManager provides the backend storage of the event list and volunteer list.

You must implement all operations of this class. 

VolunteerMatch DO COMPLETE and SUBMIT THIS FILE
VolunteerMatch is the main class.  It also provides the read from file and write to file methods needed by the program.  The main menu loop is provided for you, but you must implement the file access oprations.

Main Menu (Supported Operations)

Your program needs to be able to perform following operations:  

Load EVM from a file: If users enter '1', prompt user for a file name.
If file doesn't exist, display error message and go back to the main menu loop.
If file exists in the directory, you should read and process (parse) events and volunteers from the file.
Check if each line corresponds to an event or volunteer. Add it according to the description above. (Steps have also been provided in the skeleton file)
If there is a bad line or a line in any format other than the ones specified above, skip this line and go to the next line.
Save EVM to a file: If users enter '2', they should be prompted to enter a filename.
Display error message in case of FileNotFoundException exception.  Note: FileNotFound when writing a file means that you do not have permission to write to that folder or there are invalid characters in the file name.
If the file can be written
write the list of volunteers
write the list of events along with their volunteer matches to the file.
Format of the output is the same as in the input file. All the volunteers should be written first to the file, followed by events.
Display all events and corresponding matches: If user enters '3'; 
If event list is empty, display default message and go back to the main menu loop.
If event list is not empty: Display all the events along with their volunteer matches (adjacent Nodes) as they appear in the event list and event's corresponding adjacency lists. Note that they should be in sorted order by names.
For exact format of the output, check the sample inputs and outputs.
Display all volunteers and corresponding matches: If user enters '4'; 
If volunteer list is empty, display default message and go back to the main menu loop.
If volunteer list is not empty: Display each volunteer along with their event matches (adjacent Nodes) as they appear in the volunteer list and volunteer's corresponding adjacency lists. Note that they would be in sorted order by names.
For exact format of the output, check the sample inputs and outputs.
Create a match: This method is used to create a match between event and volunteer. If users enter '5':
Prompt user to enter event name.
Prompt user to enter volunteer name.
Create a match if all conditions are satisfied. (described above)
Else display error message and go back to the main menu loop.
Remove a match: This method is used to remove a match between event and volunteer using command prompt. If users enter '6':
Prompt user to enter event name.
Prompt user to enter volunteer name 
Remove the match if volunteer and event exist and there is a match between them.
Else display error message and go back to the main menu loop.
Add a volunteer: If users enter '7',
Prompt user to enter volunteer's name.
Prompt user to enter volunteer's available dates.
Add the volunteer if users' inputs are valid and add volunteer is successful.
Else display error message and go back to the main menu loop.
Conditions for failure: (volunteer already exists; duplicate date; invalid date)
Remove a volunteer: If users enter '8', prompt user to enter volunteer's name. 
If volunteer doesn't exist,  display error message and go back to the main menu loop.
If volunteer exists, remove the volunteer from the list and remove this volunteer from the adjacency lists of all events the volunteer was matched with.
Quit: quit the program.
program ends without output
Note: Check sample runs, resource class, javadocs for type of error messages to be displayed in different cases. All the error message to be displayed has been defined in the resource class. Do not define any new error message.

 

Summary

The program displays a welcome message and enters a menu loop with the following options: 

Main Menu

Load EVM from a file
Save EVM to a file
Display all events and corresponding matches
Display all volunteers and corresponding matches
Create a match
Remove a match
Add a volunteer
Remove a volunteer
Quit
Users need to enter 1-9 to execute respective commands.

Input/Output

This program doesn't expect command line arguments. Once executed, your program should create an instance of EventManager and go to the main menu loop directly. 

This program involves a lot of display methods. To help you displaying the outputs in the correct format, we have provided you  "Resource" class, which includes all the error messages and formats for the display. Use them for displaying any output and match your outputs with the sample outputs given to you.

 You can download the SampleRuns.zip file and unzip to see several sample runs of p5.

In summary, the assignment consists of the following files (skeleton files are provided for some classes in p5.zip):

GraphNode.java - GraphNode is the super type of all vertices in p5. This class implements basic get/set for name field, and provides a list of graphnodes that is used to keep track of the adjacent vertices of this node. Members of this class are inherited by the Event and Volunteer classes.
Event.java - A class to store information about the events and it extends GraphNode class. It represents an event with a given name that occurs on a particular date and requires Volunteers. Its adjacent nodes will be GraphNodes for volunteers.
Volunteer.java - A class to store information about the volunteers and it extends GraphNode class.  It represents a volunteer with a given name and their available dates. Its adjacent nodes will be GraphNodes for events.
EventManager.java - An EventManager instance manages the list of events and volunteers and implements several methods to facilitate menu options.
Resource.java - This is similar to the config class provided to you in p2 and stores the program parameters.
VolunteerMatch.java - This contains the main class of the program which provides an interface to the EventManager class. 

you may not add any other public methods that are not listed in the provided files.  

Submit the following files:
VolunteerMatch.java
EventManager.java 



