# livesql
A database server which gives a live feed instead of a static result set
I'm doing the first pass of this in python, otherwise I'm tempted to use Free Pascal/Lazarus because Delphi isn't really an option any more for me.

From livesql.org :
  "This is the holding cell on the internet where I intend to store an idea, so that others may copy it, and bring it to life at some point. I ask your indulgence as I will be talking about LiveSQL as if it were an accomplished fact, instead of just an idea.

SQL is a batch mode language for doing queries against databases, and returning a set of results. It also has provisions to update and otherwise modify those databases, in batches.

LiveSQL is a way to extend the familiar and useful abstraction of SQL into real time. The idea being to use a google-wave like set of delta operations to transform a batch mode of database interaction where results are used once, into one where the results are continously updated in accordance with changes in the database.

The closest analogy I know of is that of a "View" in sql, which defines a set of conditions, and allows them to be re-evaluated at a later time. LiveSQL differs from this in that the results are pushed out as they change, instead of having to be polled.

There are many places where the "impedance mismatch" between the need for live updates, and the batch mode of SQL cause big problems. LiveSQL is an attempt to reduce the mismatch, and allow much more efficient access to data.

September 1, 2011 - Mike Warot"

To get anything done in internet culture these days, the belief is to offer a minimum viable product, preferably open source, so that people can play with it, find things to fix or extend, and gain momentum towards a critical mass of community around it. So here we are. a github repository is created, I chose python and GPLv3 open source as my first crack at it... I'm flexible if it needs to change.

In my mind, a minimum viable LiveSQL should be able to contain an orderable list, and be able to match entries in that list against a criteria, returning a result feed, which updates when the conditions or data change...  the data being able to be Created Removed Updated or Deleted  (CRUD in database speak)

Consider a list of events, and a query that shows "upcoming events in the next 2 weeks".... as the clock ticks, certain items will meet the criteria, and then fall out of it as time passes, even though the specification of the query is unchanged... the effective value of the query is continuously changing.

To make this work, we need a way to store a list of things, perhaps just a key/value store, and way to compile an expression into code that can return a binary result for a match against each record. We also need a way to publish/subscribe to allow the results to be a "live" value, instead of having to re-transmit everything.

Miniumum Viable Product   v0.000
12/15/2018 06:32 PM
* Store a list of items
* Display the entire list 
* Save the list to disk
* Load the list from disk
* Create. Read, Update, Delete (CRUD) list entries
* have a protocol for sending deltas in the result set
* have a way to display the results as transfered from a set of deltas
* perhaps use port tcp/33333 to do this stuff?
