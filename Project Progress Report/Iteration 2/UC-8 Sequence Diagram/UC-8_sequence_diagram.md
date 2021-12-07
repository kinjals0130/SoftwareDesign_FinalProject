# UC-8: Seat Selection 
The UML sequence diagram shown in diagram below shows the exchange of messages between the elements to support UC-8 (Seat Selection), which is associated with QA-7 (Usability). The purpose of this diagram is to illustrate the communication that occurs between the physical nodes. Here, the user reserves their preferred seat location in the movie theatre through the Select Movie, Select Movie Experience & Seat Booking components respectively.

![UC-8 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-8-Sequence-Diagram.jpg)

From the interactions identified in diagram above, methods for the interfaces of the interacting elements are identified in the following table: 

<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>Select Movie</td>
        <td>
            String SelectMovie(String movie, Date date, String Location)
        </td>
        <td>
            The user has the choice of what movie they want to reserve the seats for and according to the date, location and movie they will be shown the appropriate seats to reserve. The function returns the status of the movie selected to ensure the movie is available. 
        </td>
    </tr>
    <tr>
        <td>Select Movie Experience</td>
        <td>
            String SelectExperience(String movieExperience)
        </td>
        <td>
            The user must select the type of movie experience they want to book seats for, this could include regular, 3D, DBox, etc., depending on the location of the movie. The function returns the status to confirm the movie experience was selected. 
        </td>
    </tr>
    <tr>
        <td>Seat Booking</td>
        <td>
           boolean updateSeatReservation()
            <br><br>
            String getUserReservation(String seatNo)
        </td>
        <td>
            The administrator must update the seat reservation page every time a user wants to reserve a seat. The function returns a status update back to the administrator. 
            <br><br>
            The user must select a seat number to reserve the respective seat for the movie of their choosing. The function returns confirmation to the user with the seat number. 
        </td>
    </tr>
</table>