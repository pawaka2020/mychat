My ideas for now:
src/models, src/services folder in lib folder
Make a model class User:
string username, string photourl, string id, bool active, datetime lastseen
apart from the usual variables and constructor, add two classes for:
a - writing into JSON (toJSON)
b - getting a User class from a JSON (fromJSON)
create also a placeholder User for testing.

services class UserServices for housing functions related to User:
- create new user in a database.
- clean user from db

https://www.youtube.com/watch?v=AaA-6wU251A&list=PLFhJomvoCKC_mXNBDnpO46Hea_PkCiVWS&index=2

MOST IMPORTANT: test first that you can use rethinkdb (or any other db) before coding out the rest
Consider also using abstract classes if I have to make multiple classes of the same kind

Create separate tables in db for users, messages, and ...?
test users, messages with setUp and tearDown inside the main()

Three other services: 
Message Service
Receipt Service
Typing Notifier Service

a test has a setUp and tearDown, setUP at the start of a test, then tearDown at the end of a test
- we don't want to append a user to the db when we test but do not remove it afterwards.

User Service:
-connect(add to db)
-disconnect(mark a db user as disconnected from chat)
-- set status as offline.(boolean)
-check if anyone online and return a list of users that are.

class Message: 
string id (same as user id), string from, string to, string content, datetime timestamp
the usual toJson and fromJson functions
class MessageService:
Future<bool> send (message)
Stream<Message> messages(user) - opens stream
startreceivingmessages  
dispose() - closes stream
message messagefromfeed(feeddata)
void removedeliveredmessage(message) -delete from db
final connection and Rethinkdb (like with all other service classes)
constructor as usual

idea: make an abstract class for all models and services
abstrac class for service just includes final connection and rethinkdb

----

message encryption
add encrypt: as a dependency
create Iencryption
{
    String encrypt
    String decrypt

}