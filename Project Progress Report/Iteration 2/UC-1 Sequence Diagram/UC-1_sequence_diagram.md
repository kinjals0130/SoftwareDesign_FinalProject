# UC-1: System Availability
The diagram below shows an initial sequence diagram for UC-1 (System Availability). As shown, the technician makes sure the system is available at all times and that the time servers are not running into traps. The interaction  starts with  a  Timeserver  sending  a trap, which  is received  by  the Technician . If TimeServers.trap==true, then the technician initiates downtime for the system.

![UC-1 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-1-Sequence-Diagram.PNG)

From the interactions identified in the diagram above, initial methods for the interfaces of the interacting elements are identified in the following table: 
<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>System</td>
        <td>
            boolean isAvailable()
            <br><br>
            boolean startDownTime()
        </td>
        <td>
            Infinitely checks if all the components of the system are available and returns a status boolean 
            <br><br>
            When called the system in under downtime, is can be due to traps that are addressed immediately by developers 
        </td>
    </tr>
    <tr>
        <td>Time Servers</td>
        <td>
            boolean isTrap()
        </td>
        <td>
            Checks if a trap is detected and return the status as a boolean ‘trap’
        </td>
    </tr>
</table>