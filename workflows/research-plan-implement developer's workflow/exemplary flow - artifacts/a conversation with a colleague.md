John: Hey, I'm starting to work on the order cancellation feature. Seems straightforward enough – just add a cancel method to the Order aggregate and wire up a command handler, right?

Mark: Yeah, mostly. But there's one thing I'd flag – when we cancel an order, we need to think about what happens with the payment status. Right now we have orders that are Paid, and if a customer cancels after payment has already gone through, that's a different scenario than canceling a Submitted order that's just waiting for validation.

John: Oh, good point. So we shouldn't allow cancellation of Paid orders?

Mark: Well, not necessarily "shouldn't" – but it's a different business decision than just "no shipped orders." I'd say we should at least allow canceling Paid orders since the customer is entitled to a refund, but we need to make sure we raise an event that the payment service can listen to. Otherwise the payment won't get reversed and accounting will be a mess.

John: Ah, so the domain logic needs to be a bit more nuanced. It's not just "can only cancel if status < Shipped", it's more like "can cancel any order that hasn't shipped, but if it's already Paid, make sure we signal that a refund is needed."

Mark: Exactly. And that's really where the complexity comes in – the cancellation logic itself in the domain is simple, but the event that gets raised might need to include some context about the payment status so the payment handler knows whether to process a refund or just release a pending authorization.

John: Got it. So when I'm building the domain method, I should make sure the OrderCancelledDomainEvent includes the payment information, or should that be handled in the command handler?

Mark: I'd keep it in the domain event – let the event carry all the information someone downstream might need. The command handler is just an orchestrator at that point.