#Software Engineering
    
#AllSeeingEye 

Visitors to college campuses often have difficulty finding their way around based on room codes or maps. Our software solution would allow users to use a phone or tablet to get directions to wherever they need to go, using an interactive real-time map with step-by-step directions. They would type in a room code or class name and our software would give them directions. This system uses a combination of wifi triangulation and thermal cameras to find and track the users and their devices and requires an active wifi connection on the device. Then, we can use a website/application to guide this user to their desired location. There is also schedule integration that allows you to type in a class name and it will automatically find the room code and guide you there. Additional information such as “free rooms” or “computer lab” or “printer” would take you to the closest option, if it is encoded into the room’s metadata. 


#Non-functional requirements

##Usability

The application will utilize a simple user interface which offers all the basic functionalities (basic search, map, room info by clicking rooms on the map) in a single view. It will also use innovative interaction design and automated functionalities, such as offering the route immediately if a search is successful and adjusting the route if needed. The map view will use color codes to quickly see available/unavailable rooms and the map in general will be designed using familiar, simple symbolics and smooth visual design to ensure ease of use.

Tests will be conducted and 90% of users will not have difficulty figuring out the functionalities of the application. This means that 90% of users will immediately after opening the application and locating be able to use a functionality such as getting the directions to a room by code, browsing the map for a nearby available room or otherwise viewing the room info.


##Capacity & Performance

The application will be designed to be able to handle up to 1000 users at a time without exceeding the server computer's computation power. This will be achieved by taking database consistency into account, normalizing databases and optimizing queries and requests.

The positioning system in collaboration with the server will function so that the user's location will be updated once every second with the accuracy of half a meter.

It will be ensured that any user at any given time submitting any search, if successful, will have their route generated and drawn in 3 seconds, with an average reliability of 95%, however with 100% of successful searches returning the route within 10 seconds. Same applies to readjusting the route.

Any other communication with the server will update the view within a second.

Upon opening the application, the latest and most accurate room info data will be loaded from the database that other school systems use. Every 5 minutes the application will query for updates in room info data.

The RAM usage of the application will not exceed 50MB.

##Security

The application will integrate with a user's university credentials if the user is logged in through the student wi-fi. The session data used by the application cannot be accessed by a third party through a flaw in the AllSeeingEye system, as application security will be implemented at all stages of development and tested thoroughly.


##Robustness

The application will handle all possible errors and exceptions to serve the user. Possible system failures and how they will be handled:
 * Search is not successful => notify user and ask to search again
 * Internet connection is interrupted while going to destination => notify user and carry on without location data (route saved on the phone)
 * Positioning system connection to user failed/lost => notify user and ask to relocate/reidentify inside the building
 * Application's connection to server failed/lost => notify user about downtime and notify maintenance about failure

##Cross-platform

The application will be implemented for devices with all screen sizes running iOS version X or newer, Android version X or newer or Windows Phone version X or newer.

#Users and use cases

The user groups are 1. Normal user and 2. Registered user / student. The registered user will have some extra functionalities but mostly they are identical.

##Use cases
1. Open app / identify
2. Search for room by code
3. Search for room by name
4. Search for room by status
5. Search for class (student/registered user)
6. Open room info
7. Close room info
8. Browse map
9. Change floor
10. Return to location

##Use case diagram
![Use cases](http://i.imgur.com/LSUttw5.png)



#Architecture stuff

The AllSeeingEye is an indoor positioning/navigating tool to help visitors of a building find rooms through a graphical user interface on a mobile application. It will position the user using (???) and let her know her location on the map and on the correct floor. The user can search for rooms and the application will point out the fastest route to the destination inside the building complex. The user can also navigate freely on the map, looking at the status of rooms to e.g. find a computer lab which is not currently in use.


Modules
 * User: position, floor, room/part of building
 * Room: code, name, reserved or not, 
 * Route: start, destination (room id), vertices, user's position

#User interface
 * Map view
   * search input
   * browse the map around
   * locate yourself
   * view route
   * open room info
 * Extended search
   * search by different room info
 * Room info view
   * name, info, type







