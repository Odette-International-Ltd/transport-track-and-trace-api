# Use Case Transport Capacity Reservation

Use-Case|	Order transport capacity at a specified LSP for a specified contract relation
Proposed by|	VDA PG API
Proposed on|	11.09.2020
Description|	In certain business scenarios it is sufficient to order transport capacity (loading meters, volume, weight) for a transport rather than specify the complete shipment.
Actors|	Ship-from, LSP, optional: copy to ship-to / transport ordering party
Pre-condition|	Contractual relationship between the transport ordering party and identified LSP
Post-condition|	Confirmation
Functions|	Create, Update, Read 
Process|	Sender: ship-from, Receiver: LSP,	Opt. Receiver: ship-to, transport ordering party
Alternative|	VDA 4933 T1 & T2 (transport order & confirmation)  resp. Odette pendants
Motivation / Business Value|	Automated, accelerated communication
Frequency|	As necessary 
