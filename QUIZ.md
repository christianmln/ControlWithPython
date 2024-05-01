### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
It handles it through interrupts, which is an event driven signal that runs code, in this case the event is if our led is high or low.
A naive approach would be to run code automatically without having an event to trigger it.

### What does `detached_callback` do? What would happen if it wasn't used?
Detached_calllback helps to ensure that functions such as connect and disconnect do not run 
simultaneously as this would make the GUI unresponsive.
If it wasn't used, the GUI may become unresponsive as running connect and disconnect simultaneously
would block the main thread.

### What does `LockedSerial` do? Why is it _necessary_?
LockedSerial ensures that only a single thread may access the serial port at a time. 
It is necessary because without it, multiple threads could access the serial port simultaneously
and result in an error.