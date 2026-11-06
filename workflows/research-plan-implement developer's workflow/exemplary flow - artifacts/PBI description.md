Product Backlog Item: Order Cancellation Feature
ID: ORD-247
Title: Enable customers to cancel orders before shipment

Description
Currently, customers have no way to cancel an order once it's been placed. Our customer service team receives multiple requests daily asking to cancel orders that haven't shipped yet, and we have to manually intervene in the database or contact the warehouse. This creates delays and frustration for both customers and support staff.

We need to implement an order cancellation feature that allows canceling orders that are still in the system but haven't been shipped yet.

Current State
Orders can be created and moved through various statuses (Submitted, AwaitingValidation, StockConfirmed, Paid, Shipped)
Once an order is placed, there's no built-in way to cancel it
The Order aggregate has methods for status transitions but nothing for cancellation
Expected Behavior
Users should be able to cancel orders that haven't been shipped
Orders that are already shipped cannot be cancelled
When an order is successfully cancelled, it should transition to a "Cancelled" status
Attempting to cancel a shipped order should return an appropriate error message
The system should raise a domain event when an order is cancelled so other parts of the system can react (e.g., release reserved stock, notify payment processing)
Acceptance Criteria
 Order can be transitioned to Cancelled status if current status is before Shipped
 Attempting to cancel a shipped order throws a domain exception
 OrderCancelledDomainEvent is raised when cancellation succeeds
 Command handler processes cancellation requests through the application layer
 Unit tests verify both successful and failed cancellation scenarios
Notes
This should follow the existing patterns in the codebase - similar to how order status changes are handled now (e.g., SetPaidStatus, SetAwaitingValidationStatus). Don't reinvent the wheel; just extend what's already there.