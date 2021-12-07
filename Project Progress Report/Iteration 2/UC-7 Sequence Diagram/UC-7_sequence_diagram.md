# UC-7: Ticket Selection
The UML sequence diagram shown in the diagram below shows the system and payment components satisfying UC-7 (Ticket Selection) where the User interacts with the system to select the type of ticket they want (Regular, 3D, D-Box, IMAX, Atmos). The User is asked to GetRegistered() if they are not registered and  already do not have a Login(). After the user has selected their movie and seats approved by the administrator through the **System**, they then proceed to **Payment** where they MakePayment() and then Logout() once everything is approved.

![UC-7 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-7-Sequence-Diagram.png)

From the interactions identified in diagram above, methods for the interfaces of the interacting elements are identified in the following table:

<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>System</td>
        <td>
            void Login(String username, String password)
            <br><br>
            void GetRegistered(String username, String password, String email)
            <br><br>
            void Logout()
        </td>
        <td>
            Logs users into the system allowing them access to book movies.
            <br><br>
            If the user is trying to book a ticket and is not already registered into the system they are prompted to register by entering their desired username, password, and email.
            <br><br>
            Logs out the user denying them access to book tickets.
        </td>
    </tr>
    <tr>
        <td>Payment</td>
        <td>
            boolean MakePayment(String paymentType, int cardNo, int cvv)
        </td>
        <td>
            For the user to make a payment they must enter the type of payment they’d like to make the payment with plus they must also enter their card number and cvv. This function returns a confirmation status upon verifying the payment.
        </td>
    </tr>
</table>