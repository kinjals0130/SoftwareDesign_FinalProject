# UC-6: Date Selection
The UML sequence diagram shown in the diagram below illustrates how EnterDate() and SelectMovie() let the user interact with the UI of the system in order to select the date that they want to view movies by asking the user to enter a specific date. The user can then select a movie of interest and proceed forward according to date availability for the selected movie.

![UC-6 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-6-Sequence-Diagram.PNG)

From the interactions identified in diagram above, initial methods for the interfaces of the interacting elements are identified in the following table: 
<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>Movie Information</td>
        <td>
            boolean AddMovieRecords()
            <br><br>
            boolean UpdateMovieRecords()
            <br><br>
            boolean DeleteMovieRecords()
            <br><br>
            boolean UpdateAvailableDates()
        </td>
        <td>
            The admin has authority to add, update and delete movies as well as update the available movie dates from the ticket booking system which returns a boolean status value indicating if their action was successful or not.
        </td>
    </tr>
    <tr>
        <td>System</td>
        <td>
            boolean EnterDate( Date dates)
            <br><br>
            String SelectMovie( String movie)
        </td>
        <td>
            The system allows the user to select the date that they want to view movies by asking the user to enter a specific date.
            <br><br>
            The user can then select a movie of interest and proceed forward according to date availability for the selected movie.
        </td>
    </tr>
</table>