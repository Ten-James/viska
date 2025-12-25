> A type that acts as the supertype for all types in its layer. 
> 
> It's not uncommon for all the objects in a layer to have methods you don't want to have duplicated throughout the system. You can move all of this behavior into a common Layer Supertype.

například [[Identity field]]

### Value Object, eg., Money
A small simple object, like money or a date range, whose equality isn’t based on identity. • Represents a monetary value
![[Pasted image 20251225091545.png]]


### Special Case (e.g., Null Object)
A subclass that provides special behavior for particular cases.
![[Pasted image 20251225091605.png]]

### Service Stub (Mock Object)
Removes dependence upon problematic services during testing.
![[Pasted image 20251225091643.png]]