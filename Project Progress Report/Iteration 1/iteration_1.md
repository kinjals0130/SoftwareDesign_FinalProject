# Iteration 1: Establishing Overall System Structure
This iteration presents the results of the activities that are performed in each step of the ADD design process, in relation to the Theatre Ticket Booking System.

## Step 1: Review Inputs
Step 1 of the ADD process iteration 1 involves reviewing the inputs and identifying the requirements which will be considered as drivers for the system. The table below summarizes the inputs:
<table>
    <tr>
        <td>Category</td>
        <td> Details </td>
    </tr>
    <tr>
        <td>Design Purpose</td>
        <td>This is a Theatre Ticket Booking System which allows users to book tickets and seats for their preferred movie.</td>
    </tr>
    <tr>
        <td>Primary Functional Requirements</td>
        <td> 
            From the use cases provided in the project progress report, we determined the primary ones to be:
            <br>
            <b> UC-1: </b> Directly Supports Core Business <br>
            <b> UC-6: </b> Directly Supports Core Business <br>
            <b> UC-7: </b> Directly Supports Core Business <br>
            <b> UC-8: </b> Directly Supports Core Business <br>
            <b> UC-9: </b> Directly Supports Core Business
        </td>
    </tr>
    <tr>
        <td>Quality Attribute Scenarios</td>
        <td> 
            <table>
                <tr>
                    <td><b>Scenario ID</b></td>
                    <td><b>Importance to the Customer</b></td>
                    <td><b>Difficulty of Implementation According to the Architect</b></td>
                </tr>
                <tr>
                    <td>QA-1</td>
                    <td>High</td>
                    <td>High</td>
                </tr>
                <tr>
                    <td>QA-2</td>
                    <td>High</td>
                    <td>Medium</td>
                </tr>
                <tr>
                    <td>QA-3</td>
                    <td>Medium</td>
                    <td>Medium</td>
                </tr>
                <tr>
                    <td>QA-4</td>
                    <td>High</td>
                    <td>High</td>
                </tr>
                <tr>
                    <td>QA-5</td>
                    <td>High</td>
                    <td>Low</td>
                </tr>
                <tr>
                    <td>QA-6</td>
                    <td>Medium</td>
                    <td>Low</td>
                </tr>
                <tr>
                    <td>QA-7</td>
                    <td>High</td>
                    <td>Medium</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td>Constraints</td>
        <td>All of the constraints will be added as drivers.</td>
    </tr>
    <tr>
        <td>Architectural concerns</td>
        <td> 
            All architectural concerns below are included as drivers:
            <br>
            <b> CRN-1: </b> Establishing an overall system structure <br>
            <b> CRN-2: </b> Leverage team’s knowledge about the WAMP stack including its integration with Javascript, HTML and CSS. <br>
            <b> CRN-3: </b> Allocate work to members of the development team
        </td>
    </tr>
</table>

## Step 2: Establish Iteration Goal by Selecting Drivers
Step 2 focuses on the iteration goal which is to achieve the architectural concern CRN-1 - establishing an overall system structure. The drivers that the architect must be mindful of for the first iteration are:
* **QA-1**: Availability
* **QA-2**: Interoperability
* **QA-4**: Performance
* **QA-5**: Security
* **QA-7**: Usability
* **CON-2**: Developer and Technician communication relationship
* **CON-4**: System accessibility and availability 
* **CON-5**: Untreated faults leading to compromisation of system security 
* **CRN-2**: Use the teams knowledge of Web Programming

## Step 3: Choose One or More Elements of the System to Refine
The element chosen to be refined for this Theatre Ticket Booking effort is the entire system (shown in the diagram below). The refinement will be done through decomposition. <br>
![Context Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/FCAPS-System-Context-Diagram.PNG)

## Step 4: Choose One or More Design Concepts That Satisfy the Selected Drivers
The table below summarizes the selection of design decisions for the system.

Chosen Alternatives: <br>
<table>
    <tr>
        <td><b>Design Decision and Locations</b></td>
        <td><b>Rationale</b></td>
    <tr>
    <tr>
        <td>
            Logically structure the client and server part of the system to use <b>Web Application</b> reference architecture
        </td>
        <td>
            The Web Application reference architecture  supports access to applications though the web browser. Plus this application does not require a rich user interface thus this reference architecture would be perfect to implement with minimal effort. Furthermore, this architecture also facilitates deployment and updating plus it provides high portability of the application. 
        </td>
    <tr>
<table>

Discarded Alternatives:
<table>
    <tr>
        <td><b>Alternatives</b></td>
        <td><b>Reason for Discarding</b></td>
    <tr>
    <tr>
        <td><b>Mobile Applications</b></td>
        <td>
            This reference architecture enables the use of handheld mobile devices, however since our system does not support this type of device, the architecture was not considered for accessing our system. 
        </td>
    <tr>
    <tr>
        <td><b>Rich Client Applications</b></td>
        <td>
            This reference architecture requires the installation of applications on the user’s PC without network connectivity . It also does not run in a web browser, unless an external technology is used. This was not considered for accessing our system since we do not require external applications to be installed and only want web browser capability.
        </td>
    <tr>
    <tr>
        <td><b>Rich Internet Application</b></td>
        <td>
            The RIA reference architecture is oriented towards the implementation of rich user interfaces in web applications that run inside a web browser. The system does not need a rich user interface, plus there is no need to make the architecture more complex than it needs to be.
        </td>
    <tr>
<table>

## Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces
The table below summarizes the instantiation design decisions that were considered and made.
<table>
    <tr>
        <td><b>Design Decision and Location</b></td>
        <td><b>Rationale</b></td>
    <tr>
    <tr>
        <td>Remove Service Agents from the Data Layer</td>
        <td>
            There are no external services being utilized in this system thus there is no need for it.
        </td>
    <tr>
    <tr>
        <td>Create a module dedicated to accessing time servers in the Data Layer</td>
        <td>
        The reference architecture is modified to conceptualize the access to time servers. This further facilitates the achievement of QA-4. The addition of this module also addresses UC-1 to UC-5.
        </td>
    <tr>
<table>

## Step 6: Sketch Views and Record Design Decisions
The diagram below shows the sketch of a module view of the refer-
ence architectures that were selected for the client and server applications. These have now been adapted according to the design decisions we have made. 

![Reference Architecture Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/Reference-Architecture-Diagram-Iteration-1.PNG)

The following table summarizes the information that is captured:

<table>
    <tr>
        <td><b>Layer</b></td>
        <td><b>Module</b></td>
        <td><b>Responsibility</b></td>
    </tr>
    <tr>
        <td>Client</td>
        <td>Web Browser</td>
        <td>Movie Ticket Booking Application runs on the client's web browser.</td>
    </tr>
    <tr>
        <td>Server - Presentation Layer</td>
        <td>User Interface</td>
        <td>Receives user interactions and presents the information to the users. It contains UI elements as buttons and text fields as well as a form in the ticket checkout page.</td>
    </tr>
    <tr>
        <td>Server - Presentation Layer</td>
        <td>UI Process Logic</td>
        <td>Manages the control flow of the application’s use cases and provides data coming from the business layer to the user interface components. It is also responsible for data validation. An example is the Login/Signup Page</td>
    </tr>
    <tr>
        <td>Server - Business layer</td>
        <td>Business Workflow</td>
        <td>Involves the execution of multiple use cases (such as ticket selection and seat selection since seats selected must be equal to number of tickets previously selected)</td>
    </tr>
    <tr>
        <td>Server - Business Layer</td>
        <td>Business Logic</td>
        <td>Retrieves and processes application data and applies business rules on the data (such as seat booking page and checkout page).</td>
    </tr>
    <tr>
        <td>Server - Business Layer</td>
        <td>Business Entities</td>
        <td>Represents the entities from the business domain and the associated business logic.</td>
    </tr>
    <tr>
        <td>Server - Data Layer</td>
        <td>Data Access</td>
        <td>Provides the common components needed to retrieve and store information. It uses the OMDB API for retrieval of movies and movie info, as well as retrieval from the database to verify/check login/signup info.</td>
    </tr>
    <tr>
        <td>Server - Data Layer</td>
        <td>Time Server Access</td>
        <td>This module isolates and abstracts operations to support communication between different types of time servers partially addressing QA-4.</td>
    </tr>
    <tr>
        <td>Server - Cross-Cutting Layer</td>
        <td>
            Security
            <ul>
                <li>User authentication</li>
                <li>Password encryption/decryption</li>
            </ul>
        </td>
        <td>Handles security aspects such as user authorization and authentication, as well as password encryption/decryption</td>
    </tr>
    <tr>
        <td>Server - Cross-Cutting Layer</td>
        <td>Management</td>
        <td>Handles validation, exception management and logging across all layers.</td>
    </tr>
    <tr>
        <td>Server - Cross-Cutting Layer</td>
        <td>Communication</td>
        <td>Handles communication mechanisms across layers and physical tiers</td>
    </tr>
    <tr>
        <td>External Data Sources</td>
        <td>Database</td>
        <td>Stores all data from the system, later accessed by the DataAccess module in the Data Layer (using MySQL to store databases).</td>
    </tr>
</table>

## Step 7: Perform Analysis of Current Design and Review Iteration
The table below summarizes the design process using the Kanban board technique.
<table>
    <tr>
        <td><b>Not Addressed</b></td>
        <td><b>Partially Addressed</b></td>
        <td><b>Completely Addressed</b></td>
        <td><b>Design Decisions Made During the Iteration</b></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-1</td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-2</td>
        <td></td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-3</td>
        <td></td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-4</td>
        <td></td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-5</td>
        <td></td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-9</td>
        <td></td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-10</td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-11</td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-15</td>
        <td>
            Selected reference architecture establishes the modules that will support this functionality
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>QA-1</td>
        <td>
            Reference of this quality attribute in the selected reference architecture. The application will be available on the internet 24/7 unless there is down time taken.
        </td>
    </tr>
    <tr>
        <td>QA-2</td>
        <td></td>
        <td></td>
        <td>
            No relative decisions made in this iteration for the quality attribute.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>QA-4</td>
        <td></td>
        <td>
            The addition of Time Server Access in the Data Layer partially addresses this QA by establishing communication with Time Servers.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>QA-5</td>
        <td></td>
        <td>
            Reference of this quality attribute in the selected reference architecture.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>QA-7</td>
        <td>
            Selected reference architecture establishes the modules that will support this quality attribute.
        </td>
    </tr>
    <tr>
        <td>CON-1</td>
        <td></td>
        <td></td>
        <td>
            Decisions for the work efficiency of the technician have not been made yet.
        </td>
    </tr>
    <tr>
        <td>CON-2</td>
        <td></td>
        <td></td>
        <td>
            Decisions for the communication relationship between the developer and technician have not been made yet. 
        </td>
    </tr>
    <tr>
        <td></td>
        <td>CON-3</td>
        <td></td>
        <td>
            Constraint is referenced by the architecture model although no relative decision has been made.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>CON-4</td>
        <td>
            Referenced architecture provides the modules that will support this constraint.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>CON-5</td>
        <td>
            Referenced architecture provides the modules that will support this  constraint.
        </td>
    </tr>
    <tr>
        <td>CON-6</td>
        <td></td>
        <td></td>
        <td>
            No relative decision has been made for this constraint.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>CRN-1</td>
        <td>
            Selection of reference architecture and deployment pattern.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>CRN-2</td>
        <td></td>
        <td>
           Technologies and reference architecture that have been considered up to this point have taken into account the knowledge of the developers.
        </td>
    </tr>
    <tr>
        <td>CRN-3</td>
        <td></td>
        <td></td>
        <td>
           No relative decisions have been made for this particular concern. 
        </td>
    </tr>
</table>