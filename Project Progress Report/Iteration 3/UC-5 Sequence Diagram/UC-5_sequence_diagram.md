# UC-5: Confirmation Response Time
The UML sequence diagram shown in diagram below shows the system and Time Servers components satisfying UC-5 (Confirmation Response Time), which is associated with QA-2 (Interoperability), where the time servers must be able to send a confirmation email to the user after booking in <1 minute. The user is sent confirmations for booking and making the payment for the ticket in a timely manner within the restrictions.

![UC-5 Sequence Diagram](https://github.com/rutvishah859/Software-Design-Final-Project/blob/main/images/UC-5-Sequence-Diagram.PNG)

From the interactions identified in the diagram above, methods for the interfaces of the interacting elements are identified in the following table: 
<table>
    <tr>
        <td><b>Element</b></td>
        <td><b>Method Name</b></td>
        <td><b>Description</b></td>
    </tr>
    <tr>
        <td>System</td>
        <td>
            String bookTicket(String movie, String seatNo)
            <br><br>
            String makePayment(String payment Type, int cardNo, int cvv)
        </td>
        <td>
            The user must book the ticket, the function returns a confirmation to the user of the ticket booking with a ticket number. The ticket number gets sent to the Time Servers to be put into a queue. 
            <br><br>
            The user must choose and make a payment, the function returns a confirmation back to the user of payment with the payment number. The payment number gets sent to the Time Servers to be put into a queue. 
        </td>
    </tr>
    <tr>
        <td>Time Servers</td>
        <td>
            String addTicketToQueue(String ticketNo)
            <br><br>
            String addPaymentToQueue(String paymentNo)
        </td>
        <td>
            The Time Servers adds the ticket next in the queue, the function returns an email back to the user in less than a minute with a confirmation that their ticket has been booked.
            <br><br>
            The Time Servers adds the payment next in the queue, the function returns an email back to the user in less than a minute with a confirmation that their payment has been processed.
        </td>
    </tr>
</table>