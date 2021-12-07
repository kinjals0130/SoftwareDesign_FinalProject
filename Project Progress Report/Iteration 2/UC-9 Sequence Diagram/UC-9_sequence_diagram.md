# UC-9: Payment Option
The UML sequence diagram shown in the diagram below shows the system, payment & credit card company components satisfying UC-9 (Payment Options) where the developer must be able to create a system that can manage several payments being made at checkout from various users at the same time. Once the User selects the payment type and inputs the payment information through the **System**, the info is transferred to the **Payment** component where it is then verified with the **Credit Card Company**. Once the payment information is verified, the User is sent back a confirmation email.

![UC-9 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-9-Sequence-Diagram.PNG)

From the interactions identified in daigram above, methods for the interfaces of the interacting elements are identified in the following table: 
<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>System</td>
        <td>
            void choosePaymentMethod(String paymentType)
            <br><br>
            boolean cardInfo(int cardNo, int cvv)
        </td>
        <td>
            The user must select their specific payment method in order to purchase tickets to the movie of their choice. Once this selection is made, the user will be prompted to enter their card information.
            <br><br>
            The user must enter their credit card/debit card information such as the card number and CVV in order to make a payment.
        </td>
    </tr>
    <tr>
        <td>Payment</td>
        <td>
            boolean MakePayment(String paymentType, int cardNo, int cvv)
        </td>
        <td>
            For the user to make a payment they must enter their preferred payment method, as well as their card number and cvv. This function returns a confirmation email to the user upon a successful payment.
        </td>
    </tr>
    <tr>
        <td>Credit Card Company</td>
        <td>
            boolean verifyTransaction()
            <br>
            void sendConfirmationEmail()
        </td>
        <td>
            Once the user makes a payment, their credit card company will be alerted of the transaction and will have to verify it. This function returns a confirmation upon verification of payment to the system.
            <br>
            After the transaction has been confirmed/approved a confirmation will be sent to the credit card company indicating that the confirmation email has been sent successfully to the user.
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