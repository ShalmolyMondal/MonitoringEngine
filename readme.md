# How to use the core

## Convert AWS json to csv

```bash
npm run csv-parser
```

- Creates a csv file.

- File location can be changed using the `filePath` variable in `src/dataParser.js` file.

## Execute monogo extractor

This connects to a MongoDB server, perform a query on a collection, and write the query results to both a JSON file and a CSV file. The JSON file contains the raw query results, while the CSV file includes specific fields from the query results in a comma-separated format.

```bash
npm run monogo-extractor
```

- Creates a csv and a json file in the current folder.

- You can set the connection, db name, and collection name by changing their corresponding variables in `src/monogClient.js` file.

- The query can be modified on line 22 of the file.

## Fiware rule based query evaluation

To set up an Express.js server that connects to a MongoDB database and interacts with it using Fiware rule-based query evaluation, run the following command

```bash
npm run fiware-listener
```

This will start an express server on port 1028, which has 2 main REST methods:

1. `localhost:1028/event` An HTTP POST method and a callback listener for Fiware Orion subscriptions. When a subscription is triggered, Orion will send an event to this method. The method adds the current time as the event detection time and stores the data in MongoDB.

2. `localhost:1028/export` An HTTP GET method that queries the MongoDB "event" collection, extracts the data, and generates a CSV file with entity ID, event detection time, observation time, and delay.
