## Objective
Create a NoSQL table using DynamoDB and insert sample items.

## Steps

1. Open DynamoDB service
   - Go to DynamoDB → Tables → Create table

2. Configure table
   - Table name: Students
   - Partition key: UID (Number)
   - Keep default settings

3. Create table and wait until status becomes Active.

4. Add items
   - Open the created table
   - Go to Explore table items → Create item

5. Insert sample data
   Item 1
   UID: 101
   iteam1: pizza
   iteam2: burgur
   price: 290

   Item 2
   UID: 102
   iteam1: biryani
   iteam2: snj

6. Save items

7. View stored records in table

## Result
The DynamoDB table is created successfully and sample records are stored and displayed.