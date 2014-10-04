#Software Engineering
    
# 1. AllSeeingEye 

Software Engineering TJ00AA65-3005 Final Project: Analysis and Requirements Practice

Title: AllSeeingEye: Requirements Of The System"
Class: Software Engineering TJ00AA65-3005
Team Name: The Illuminati
Team Members: Ville Kemppainen, Marina Asia, Miguel Bejarano
Date: 5.10.2014
Version History: [Available via GitHub](https://github.com/miguelbe/AllSeeingEye/commits/master/FinalProject.md)

# 2. Introduction

Visitors to college campuses often have difficulty finding their way around based on room codes or maps. Our software solution would allow users to use a phone or tablet to get directions to wherever they need to go, using an interactive real-time map with step-by-step directions. They would type in a room code or class name and our software would give them directions. This system uses a combination of wifi triangulation and thermal cameras to find and track the users and their devices and requires an active wifi connection on the device. Then, we can use a website/application to guide this user to their desired location. There is also schedule integration that allows you to type in a class name and it will automatically find the room code and guide you there. Additional information such as “free rooms” or “computer lab” or “printer” would take you to the closest option, if it is encoded into the room’s metadata. 

# 3. Use cases

1. Open app / identify
2. Search for room by code
3. Search for room by name
4. Search for room by status
5. Search for class (student/registered user)
6. Open room info
7. Close room info
8. Browse map
9. Change floor

## Use case diagram

![Use cases](http://i.imgur.com/LSUttw5.png)

## User Groups

1. Students, regular users of the system
2. Administrators, superusers in charge of updating the system and keeping it running

## Use Case Scenarios

### 2. Search for room by code
Description: The user searches for directions to a room by a room code
Precondition: The user has opened the application and is in the map or extended search view.
Postcondition: The user has a route generated on the map
Main flow:
 1. User enters and submits a room code in the search box
 2. The system handles the search input
 3. Upon a successful match, a route is generated and drawn on the map

Alternate flows:
 1. No search match
   1. User enters and submits a room code in the search box
   2. The system handles the search input but finds no room to match the given code
   3. User is notified

### 6. Open room info
Description: The user opens a room information window from the map
Precondition: The user has opened the application and is in the map view.
Postcondition: The user is in the room info view
Main flow:
 1. User taps a room on the map
 2. A room info window opens

 
### 10. Return to location
Description: The user has drifted off the map and wants to see her own position again
Precondition: The user has opened the application and is in the map view.
Postcondition: The map view is aligned to the user's position
Main flow:
 1. User taps "Return to location" button
 2. The map view moves to user's position
Alternate flows:
 1. User is in a different floor from the viewed one
   1. User taps "Return to location" button
   2. The map view changes floor and goes to user's position

# 4. System Architecture

## High-level overview

The All Seeing Eye system is a complicated navigation system, but it can be broken up into three interconnected modules. The tracking system uses a combination of wifi and thermal cameras to find users on demand and to follow them on their rute to make sure they're headed in the right direction. On the back end, there's a pathfinding system that will take real-time information of the student's location and match it to the static information of the building's layout. The client-facing system has shows a simplified version of the building layout, the student's current location, and requires two-way communication to and from the back-end server.

A normal connection would work like this:

1. A student inside the building joins the wifi provided by the campus, logging in using their own credentials (username and password).
2. They launch the AllSeeingEye application, downloading it first if they don't have it already.
3. The application establishes a connection with the AllSeeingEye server
4. The application then provides the wifi IP and MAC addresses of the device
5. The AllSeeingEye server finds the closest wifi Access Points to the device, including the one it is actually connected to
6. The server also finds the username associated with the device's IP address
7. The system then gets the student's schedule and uses the wifi location to find the student through the more-accurate thermal cameras.
8. The server automatically finds and suggests a path from the student's current location to their next class
9. The server stops tracking once the student arrives in the classroom and the application on their device gives a success message.

## Main modules and their functions

![UML Diagram](http://www.gliffy.com/go/publish/image/6260002/L.png)

 * AllSeeingEye: Main class that the entire system depends on. This is the central part of the server.
 * AppInterface: In charge of communicating with the application. This would be listening using a TCP socket for incoming connections.
 * WifiFinder: In charge of first finding the student, works before knowing the student's username or room-specific location. This would interface with the AllSeeingEye directly.
 * Student: Main class for user information. Exposes the location information to the AllSeeingEye without showing implementation details. Has a schedule.
 * Campus: Main class for the building information. Specifies a physical boundry for the tracking to be functional, contains a schedule that is a superset of what any individual Student would have.
 * Room: A physical subdivision of the Campus. Physical boundries specified by x/y/z coordinates. Contains data such as the room code, computers available, maximum occupancy. Also has its own schedule.
 * Event: Container for what would be a regular school class, something composed of a start time, end time, name, teaching instructor, and possibly other kinds of metadata. A Student, Campus or Room could have its own schedule, stored as an array of Events or interfaced through a Database, for example.
 * TrackingService: Abstracts the functions for tracking Students. This would coordinate the passing back-and-forth between the thermal cameras and the Wifi Access Points in case either one gets lost temporarily. It would also be responsible for decision-making if the Thermal and Wifi tracking systems start giving contradicting information
 * WifiTracker: in charge of tracking the Student's device using Wifi APs
 * ThermalTracker: in charge of tracking the Student using Thermal cameras
 

# 5. Requirements

## Functional Requirements





Modules
 * User: position, floor, room/part of building
 * Room: code, name, reserved or not, 
 * Route: start, destination (room id), vertices, user's position

## Non-Functional Requirements

## Usability

The application will utilize a simple user interface which offers all the basic functionalities (basic search, map, room info by clicking rooms on the map) in a single view. It will also use innovative interaction design and automated functionalities, such as offering the route immediately if a search is successful and adjusting the route if needed. The map view will use color codes to quickly see available/unavailable rooms and the map in general will be designed using familiar, simple symbolics and smooth visual design to ensure ease of use.

Tests will be conducted and 90% of users will not have difficulty figuring out the functionalities of the application. This means that 90% of users will immediately after opening the application and locating be able to use a functionality such as getting the directions to a room by code, browsing the map for a nearby available room or otherwise viewing the room info.


## Capacity & Performance

The application will be designed to be able to handle up to 1000 users at a time without exceeding the server computer's computation power. This will be achieved by taking database consistency into account, normalizing databases and optimizing queries and requests.

The positioning system in collaboration with the server will function so that the user's location will be updated once every second with the accuracy of half a meter.

It will be ensured that any user at any given time submitting any search, if successful, will have their route generated and drawn in 3 seconds, with an average reliability of 95%, however with 100% of successful searches returning the route within 10 seconds. Same applies to readjusting the route.

Any other communication with the server will update the view within a second.

Upon opening the application, the latest and most accurate room info data will be loaded from the database that other school systems use. Every 5 minutes the application will query for updates in room info data.

The RAM usage of the application will not exceed 50MB.

## Security

The application will integrate with a user's university credentials if the user is logged in through the student wi-fi. The session data used by the application cannot be accessed by a third party through a flaw in the AllSeeingEye system, as application security will be implemented at all stages of development and tested thoroughly.

## Robustness

The application will handle all possible errors and exceptions to serve the user. Possible system failures and how they will be handled:
 * Search is not successful => notify user and ask to search again
 * Internet connection is interrupted while going to destination => notify user and carry on without location data (route saved on the phone)
 * Positioning system connection to user failed/lost => notify user and ask to relocate/reidentify inside the building
 * Application's connection to server failed/lost => notify user about downtime and notify maintenance about failure
 * Some crucial part of the system is down (e.g. communication between server and positioning hardware) => notify user about downtime and notify maintenance about failure

## Cross-Platform

The application will be implemented for devices with all screen sizes running iOS version X or newer, Android version X or newer or Windows Phone version X or newer.

## Users And Use Cases

The user groups are 1. Normal user and 2. Registered user / student. The registered user will have some extra functionalities but mostly they are identical.

# 6. User Interface

![mapview](http://i.imgur.com/hKzOwIw.jpg)
![mapview](http://i.imgur.com/NjXNxiw.jpg)
![mapview](http://i.imgur.com/PzB2cpW.jpg)

# 7. Project Management And Self Reflection





