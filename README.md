[Play Blog V Blog here!](https://competent-thompson-123cfb.netlify.com/)

Related repos: [Client](https://github.com/Koblinskis/BlogVBlog-client), [Server](https://github.com/Koblinskis/BlogVBlog-server), [MongoDB](https://github.com/Koblinskis/BlogVBlog-mongo)
# Blog V Blog MongoData
Blog V Blog is a web application that pits two blog titles against each other and the winner is determined by the user. The client is a React application that talks to an ExpressJS API backend, and the server reads and writes to a MongoDB Database. The server selects two random blogs titles from the database and returns them to the client, and then the user picks their favorite. The server records a winning score for the title selected. The highest scoring titles per category can be viewed on the winners page. 

![Screenshot](https://raw.githubusercontent.com/Koblinskis/BlogVBlog-mongo/master/screenshot.png)

This repo contains the raw data that was used as well as one-time data modification scripts and a working snapshot of the data.
## How to Restore MongoDB Dump
To run this project locally, you will need to [restore](https://docs.mongodb.com/manual/reference/program/mongorestore/) the mongodb dump to a mongodb server.
* `mongorestore  dump/`
## Example Document Schemas
**Collection**: `blog` - Blog documents, including current score and opponent matchup scores

```js
{
    "_id" : ObjectId("5e1a1b3a35791dd5ad712158"),
    "category" : "politics",
    "title" : "#ElectionWatch: Inauthentic Activity in India",
    "subtitle" : "Pages used false identities to exacerbate polarization on both sides before elections",
    "score" : -2.0,
    "versus" : {
        "5e1a1b3a35791dd5ad7121b1" : -1,
        "5e1a1b3a35791dd5ad71219a" : -1
    }
}
```

**Collection**: `timeline` - Contains snapshots of a single vote

```js
{
    "_id" : ObjectId("5e610e747544d92918921ede"),
    "blogId" : "5e1a1b3a35791dd5ad712447",
    "category" : "javascript",
    "title" : "11 Javascript Data Visualization Libraries for 2019",
    "timestamp" : ISODate("2020-03-05T14:36:36.955Z"),
    "currentScore" : 1,
    "change" : 1,
    "opponentTitle" : "11 Javascript Utility Libraries you Should Know in 2019",
    "opponentId" : "5e1a1b3a35791dd5ad712448",
    "opponentCurrentScore" : -1,
    "__v" : 0
}
```

