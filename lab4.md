## Software engineering 

###lab 4: modelling software requirements

#### A. Get familiar with software requirements specification (SRS) documentation

**1. Find existing requirements documentation** e.g. by querying
 * requirements specification
 * requirements specification example pdf
 * srs pdf
 * or [here](https://gist.github.com/OAlm/f1d18c17687ba28d4b5b)
 * (Maybe too big for today; but could be interesting to check for your project: http://www.i-locate.eu/public-deliverables/)

**AVOID DUPLICATE**. Check if the SRS you found has not been already taken: https://docs.google.com/document/d/1e2hjG9Fs-gl-k7V5mrX6Fz_oTahO69wWQVh2VYzFB0Q/edit And add yourself there. First come, first served. 

**2. Report the following things related to the document you found:**
 
  **(Introduction)**
* What is the project?
  * It's a drone-aided system for monitoring the health of crops with an infrared camera and a web interface.
* Overall description of the product (=what is it? can you understand it?)
  * The system has a UAV flying over a field of crops and capturing infrared images of the crops
  * The crops are then uploaded to a server and processed
  * The user can then view the images through a web interface
* Target audience (of the document)?
  * The document is targeted towards the school personnel that are a part of the course the project is a part of, and whoever needs a detailed specification of the system
  * It also serves as a tool to explain the system to a collaborator development team
* The situation? Motivation?
  * Farmers need a simple system to see what's going on in the different parts of a large field and a drone will aid in that
* Structure
  * Compare the structure of the document with the template provided for the course group work. How does it differ? Is there more? Less? (check also the contents and structure of SRS provided in Wikipedia:   http://en.wikipedia.org/wiki/Software_requirements_specification).
    * Overall it's similar, some differences: 
      * It has a very elaborative introduction with parts like Document conventions and a list of Definitions and abbreviations
      * There's no UML or class diagrams
      * There is a list of vaguely defined quality attributes

**(Use cases)**
* What the system (will) do?
  * The system allows farmers to plan drone flights, then process images taken by the drones to point out problem areas. This will all be done through a web interface.
* Use case diagram?
  * [Use case diagram.](http://i.imgur.com/N9JHDpY.png)
* Actors?
  * Users, logged in/privileged users, Administrators
* How cases are described, how much details?
  * Cases are described as one image with the basic user interface, as well as a list of options and functions available on the home page. Fairly detailed but not organized very well.


**(General structure of the system)**
* What chart techniques are used? Why?
  * Use case diagrams and a table of requirements

**(Functional & non-functional requirements)**
* Listed?
  * Yes
* Measurable/traceability? (is it possible to check from the upcoming end product if a feature / requirement is implemented or not?)
  * Yes

**(How does (will) it look?)**
* UI examples / views?
* Are the pictures mockups or screenshots from existing system?
* Transitions between views

**(Process model? [might not exist, some times in a separate document called â€˜project planâ€™])**
* Allocation of resources / budget?
* Risk Analysis?

**(Your point of view)**
* Is it a good/bad document? Why?
* Consider also the quality of diagrams / illustrations
* Do you think there would be enough information for you to build that system?
* Etc.

##### Return a link of your github repo to Tuubi. Don't forget to put a link to the document you analyzed. 

After the deadline, the tuubi assignment will be made public, so everyone could benefit from your analysis.

##### You will do a small (5min) group presentation for the class of your analysis.

### B. Start your project :)

The idea is to benefit from your (and/or other group) analysis:
* Do you get an idea how and what to write?
* At the content level, is there parts that you would simplify or go into more details?
* Do you think that you are able to list functional requirements? Non-functional requirements (and make them measurable)?
* What is the importance of the illustrations/diagrams/mock-ups?
* How much "technical" vocabulary should be?
* Etc.
