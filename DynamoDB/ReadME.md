# Query Data with DynamoDB

![Image](https://github.com/dev-boris67/AWS-Basics/blob/main/Project%20images/14.png?raw=true).

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-query)

**Author:** Nchindo Boris  
**Email:** nchindoboris37@gmail.com

---

## Query Data with DynamoDB

![Image](http://learn.nextwork.org/soothed_rose_serene_peach/uploads/aws-databases-query_733d9399)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a fully managed NoSQL database service provided by AWS that delivers fast, predictable performance and seamless scalability.

### How I used Amazon DynamoDB in this project

In thiss project, I used Amazon DynamoDB to query loaded data using partition and sort keys

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is that it would be an easy project

### This project took me...

This project took me 45 minutes to complete

---

## Querying DynamoDB Tables

A partition key is a filter that DynamoDB will use to split up and find data.

A sort key is a secondary key used to filter your query results again! Sort keys work after the partition key i.e. you still have to use the partition key to split up your data first, and then the sort key partitions your data again.

![Image](http://learn.nextwork.org/soothed_rose_serene_peach/uploads/aws-databases-query_d105b0b0)

---

## Limits of Using DynamoDB

I ran into an error when I queried for all comments posted by User Abdulrahman. This was because I did not use the Id (Partition key)

Insights we could extract from our Comment table includes; 
- Id (String)
- CommentDateTime (String)
- Message
- PostedBy 
Insights we can't easily extract from the Comment table includes; 
- ContentType
- Price
- Services
- Title


![Image](http://learn.nextwork.org/soothed_rose_serene_peach/uploads/aws-databases-query_cb3e260c)

---

## Running Queries with CLI

A query I ran in CloudShell
aws dynamodb get-item \
    --table-name ContentCatalog \
    --key '{"Id":{"N":"202"}}' \
    --projection-expression "Title, ContentType, Services" \
    --return-consumed-capacity TOTAL

Gives a strongly consistent read

Query options I added to my query are;
--consistent-read : for a strongly consistent read.
--projection-expression: to know some of the item's attributes.
--return-consumed-capacity : to know how much capacity was consumed by the request.

![Image](http://learn.nextwork.org/soothed_rose_serene_peach/uploads/aws-databases-query_733d9399)

---

## Transactions

A transaction is a group of operations that all have to succeed - if any of the operations in the group fails, none of the changes get applied. This makes sure that any change to your database is consistent across all your tables!

I ran a transaction using a command with CloudShell. This transaction did two things;
- Update the Comment table and 
- Update the Forum table

![Image](http://learn.nextwork.org/soothed_rose_serene_peach/uploads/aws-databases-query_2f65f83e)

---

---

