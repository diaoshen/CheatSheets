```
Install MONGO and as Windows Service

Mongo lives here  :
C:\Program Files\MongoDB\Server\4.2\bin

Configuration file to where to store the dbs is in :
C:\Program Files\MongoDB\Server\4.2\bin\mongod.cfg

DB is stored in this folder :
C:\Program Files\MongoDB\Server\4.2\data


Start Mongo service
> net

Stop Mongo service

> net stop MongoDB





Collection/Table
Document/Row


db //show current db
show dbs  //show all dbs
show collections  //to show all tables
db.createCollection('posts')
use <db name> //use db name , if doesn't exist it will create
db.dropDatabase() //use the db then drop it



db.posts.insert({
})






```
