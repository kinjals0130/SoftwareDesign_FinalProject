# Iteration 2: Identifying Structures to Support Primary Functionality
In this iteration, we will move from generic descriptions of functionality to more detailed decisions by addressing the biggest risks first and moving to finer details. This will eventually impact team formation, interfaces and the development process.

## Step 2: Establish Iteration Goal By Selecting Drivers
The goal of this iteration is to address the general architecture concern of identifying structures to support primary functionality. The architect considers CRN-3 which is the allocation of team members, as well as the following primary use cases:
* UC-1: System Availability
* UC-6: Date Selection
* UC-7: Ticket Selection
* UC-8: Seat Selection
* UC-9: Payment Options

## Step 3: Choose One or More Elements of the System to Refine
The elements to be refined in this iteration are the modules in the reference architecture model from Iteration 1. The modules are located in the different layers and provide support of functionality for the system by collaborating different components associated with the modules.

## Step 4: Choose One or More Design Concepts That Satisfy the Selected Drivers
The table below summarizes the design decisions made for the system.
<table>
    <tr>
        <td><b>Design Decision and Locations</b></td>
        <td><b>Rationale and Assumptions</b></td>
    <tr>
    <tr>
        <td>
            Create a <b>Domain Model</b> for the application  
        </td>
        <td>
            Before starting a functional decomposition, it’s necessary to create an initial Domain Model for the system, identifying relationships and major entities in the domain. There are no good alternatives and the domain model must eventually be created or it will emerge in a suboptimal fashion, this leads to an complex ad hoc architecture that’s hard to understand and maintain. 
        </td>
    <tr>
    <tr>
        <td>
            Identify <b>Layers</b> that map to functional requirements 
        </td>
        <td>
            Each layer of the application needs to have a distinct and specific responsibility. The interactions between all the layers have to be highly constrained with only unidirectional dependencies between them.
            <br>
            One possible alternative is to consider domain objects from the start to eliminate the risk of not considering a requirement.
        </td>
    <tr>
    <tr>
        <td>
            Decompose <b>Layers</b> into general and specialized <b>Components</b>
        </td>
        <td>
            Each self-contained and coherent responsibility within a layer is categorized as a separate domain object (modules that can be developed independently).
            <br>
            These modules are “components” in this pattern. Their specialization is associated with the layers where they are located, such as UI Modules.
        </td>
    <tr>
<table>

## Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces
The instantiation design decisions made in this iteration are summarized in the following table:
<table>
    <tr>
        <td><b>Design Decision and Location</b></td>
        <td><b>Rationale and Assumptions</b></td>
    <tr>
    <tr>
        <td>Create initial domain model</td>
        <td>
            To accelerate this phase of design, only an initial domain model is created using the participating entities in the primary use cases.
        </td>
    <tr>
    <tr>
        <td>System use cases mapped to layers</td>
        <td>
            Analyzing the system use cases to initially identify domain objects.
        </td>
    <tr>
    <tr>
        <td>
            Identify layer-specific modules with an explicit interface by decomposing the domain objects across the layers
        </td>
        <td>
            Ensure that all modules that support the functionalities are identified.
        </td>
    <tr>
    <tr>
        <td>
            Remove the Helpers and Utilities module from the Data Layer
        </td>
        <td>
            Extra functionalities that are common to other modules are not needed in the system.
        </td>
    <tr>
<table>

After identifying the architectural elements and interfaces in this step we can move on to recording design decisions in the next step.

## Step 6: Sketch Views and Record Design Decisions
The diagram below shows an initial domain model for the system as a result of the design decisions made in the previous step. It supports the entities that participate in the primary use cases and their relationships.

![Initial Domain Model](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/domain_model.jpg)

This is the Web Application Model that supports the primary use cases:

![Reference Architecture Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/Reference-Architecture-Diagram-Iteration-2.PNG)

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

<ul>
    <li><a href = "https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%202/UC-1%20Sequence%20Diagram/UC-1_sequence_diagram.md"><b>UC-1:</b> System Availability</a></li>
    <li><a href = "https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%202/UC-6%20Sequence%20Diagram/UC-6_sequence_diagram.md"><b>UC-6:</b> Date Selection</a></li>
    <li><a href = "https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%202/UC-7%20Sequence%20Diagram/UC-7_sequence_diagram.md"><b>UC-7:</b> Ticket Selection</a></li>
    <li><a href = "https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%202/UC-8%20Sequence%20Diagram/UC-8_sequence_diagram.md"><b>UC-8:</b> Seat Selection</a></li>
    <li><a href = "https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/Project%20Progress%20Report/Iteration%202/UC-9%20Sequence%20Diagram/UC-9_sequence_diagram.md"><b>UC-9:</b> Payment Options</a></li>
</ul>

## Step 7: Perform Analysis of Current Design and Review Iteration

The selections taken in this iteration offered a basic grasp of how the system's functionality is supported. The status of the various drivers, as well as the decisions taken throughout the iteration, are summarised in the table below. The table has been cleared of drivers that were fully handled in the previous iteration.

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
            Modules across the layers, supporting this use case have been identified.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-6</td>
        <td></td>
        <td>
            Modules partially support this use case across the layers.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-7</td>
        <td></td>
        <td>
            Modules partially support this use case across the layers.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>UC-8</td>
        <td></td>
        <td>
            Modules partially support this use case across the layers.
        </td>
    </tr>
    <tr>
        <td>UC-9</td>
        <td></td>
        <td></td>
        <td>
            No relative decisions made in this iteration for the use case.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>QA-2</td>
        <td>
            The elements that support the associated use cases have been identified.
        </td>
    </tr>
    <tr>
        <td></td>
        <td>QA-4</td>
        <td></td>
        <td>
            The elements that support the associated use cases have been identified.
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
        <td>CON-1</td>
        <td></td>
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
        <td>CON-3</td>
        <td></td>
        <td></td>
        <td>
            Constraint is referenced by the architecture model although no relative decision has been made.
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
        <td>CRN-2</td>
        <td></td>
        <td>
            Technologies and reference architecture that have been considered up to this point have taken into account the knowledge of the developers.
        </td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>CRN-3</td>
        <td>
            Modules associated with all the use cases have been identified.
        </td>
    </tr>
</table>