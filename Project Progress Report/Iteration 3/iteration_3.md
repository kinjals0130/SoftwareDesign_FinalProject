# Iteration 3: Addressing Quality Attribute Scenario Driver
This iteration builds on the fundamental structural decisions made in iterations 1 and 2 by focusing on one of the quality attribute scenarios.

## Step 2: Establish Iteration Goal by Selecting Drivers
This iteration will focus on the **QA-4 (Performance)** quality attribute scenario. QA-4 states that the website must be able to produce transactions and display tickets in a timely manner. There should be little delay, <1 minute, when performing these transactions.

## Step 3: Choose One or More Elements of the System to Refine
The elements to be refined in this iteration will be the physical nodes identified in iteration 1, which are the time servers and database servers.  

## Step 4: Choose One or More Design Concepts That Satisfy the Selected Drivers
The design concepts used in this iteration are indicated in the table below:
<table>
    <tr>
        <td><b>Design Decision and Locations</b></td>
        <td><b>Rationale and Assumptions</b></td>
    <tr>
    <tr>
        <td>
            Introducing an element from the <b>message queue</b>.
        </td>
        <td>
            Tickets received from the time servers are placed in the message queue then later retrieved by the application. Use of a queue will guarantee that tickets are processed and delivered in a timely manner. 
        </td>
    <tr>
    <tr>
        <td>
            Introducing the <b>performance</b> tactic by <b>prioritizing events</b>.
        </td>
        <td>
            Prioritizing transactions by importance of events according to the service provided to the user. Ticket booking transactions made first will get processed first (according to the time).
        </td>
    <tr>
<table>

## Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces
The instantiation design decisions made in this iteration are summarized in the following table:
<table>
    <tr>
        <td><b>Design Decision and Locations</b></td>
        <td><b>Rationale and Assumptions</b></td>
    <tr>
    <tr>
        <td>
            Deploy message queue on a separate node
        </td>
        <td>
            Doing so will guarantee that no transaction data will be lost in the case that the time servers are down according to CON-3. 
        </td>
    <tr>
    <tr>
        <td>
            Identifying the events to be prioritized.
        </td>
        <td>
            Create the prioritization scheme to rank the order of services according to importance. 
        </td>
    <tr>
<table>

## Step 6: Sketch Views and Record Design Decisions

The diagram below shows the refined layered architecture model (web application reference architecture).

![Reference Architecture Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/Reference-Architecture-Diagram-Iteration-3.PNG)

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
        <td>
            Business Logic
            <ul>
                <li>Payment</li>
                <li>Ticket Booking</li>
            </ul>
        </td>
        <td>Retrieves and processes application data and applies business rules on the data (such as seat booking page and checkout page).</td>
    </tr>
    <tr>
        <td>Server - Business Layer</td>
        <td>
            Business Entities
            <ul>
                <li>User</li>
                <li>Movie Information</li>
                <li>System</li>
            </ul>
        </td>
        <td>Represents the entities from the business domain and the associated business logic.</td>
    </tr>
    <tr>
        <td>Server - Business Layer</td>
        <td>
            Event Prioritization
            <ul>
                <li>First Come First Serve</li>
            </ul>
        </td>
        <td>Prioritizing the events from level of importance to the user.</td>
    </tr>
    <tr>
        <td>Server - Business Layer</td>
        <td>Message Queues</td>
        <td>Using message queues to prioritize the events to be received by the application and to make sure the system time server does not fail.</td>
    </tr>
    <tr>
        <td>Server - Data Layer</td>
        <td>
            Data Access
            <ul>
                <li>MySQL Database</li>
                <li>OMDB API</li>
            </ul>
        </td>
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
        <td>
            Communication
            <ul>
                <li>Data layer communicates with database</li>
                <li>Time Servers</li>
            </ul>
        </td>
        <td>Handles communication mechanisms across layers and physical tiers</td>
    </tr>
    <tr>
        <td>External Data Sources</td>
        <td>Database</td>
        <td>Stores all data from the system, later accessed by the DataAccess module in the Data Layer (using MySQL to store databases).</td>
    </tr>
</table>

[UC-5: Confirmation Response Time](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%302/UC-5%20Sequence%20Diagram/UC-5_sequence_diagram.md)

## Step 7:  Perform Analysis of Current Design and Review Iteration
The status of the various drivers, as well as the decisions taken throughout the iteration, are summarised in the table below. The table has been cleared of drivers that were fully handled in the previous iteration.

<table>
    <tr>
        <td><b>Not Addressed</b></td>
        <td><b>Partially Addressed</b></td>
        <td><b>Completely Addressed</b></td>
        <td><b>Design Decisions Made During the Iteration</b></td>
    </tr>
    <tr>
        <td></td>
        <td>UC-6</td>
        <td></td>
        <td>
            Partial addressing of this use case in the refined model. 
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-7</td>
        <td>
            The refined modules in the architectural model address this use case.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-8</td>
        <td></td>
        <td>
            Partial addressing of this use case in the refined model. 
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>UC-9</td>
        <td>
            The refined modules in the architectural model address this use case.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>QA-4</td>
        <td>
            This quality attribute is the primary goal for this iteration and has been supported through the refined models. 
        </td>
    </tr>
    <tr>
        <td>QA-5</td>
        <td></td>
        <td></td>
        <td>
            No relative decision has been made for this particular quality attribute.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>CON-1</td>
        <td></td>
        <td>
            Decisions for the work efficiency of the technician have not been made yet.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>CON-2</td>
        <td></td>
        <td>
            Decisions for the communication relationship between the developer and technician have not been made yet. 
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>CON-3</td>
        <td>
            Constraint is referenced by the architecture model that has been refined.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>CON-6</td>
        <td></td>
        <td>
            Constraint has been partially addressed with the introduction of message queues and event prioritization. 
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
</table>