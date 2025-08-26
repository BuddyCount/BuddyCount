## Users

### Create a user 
**POST** `/users`

**Request body:**
```json
{
  "id": "something we'll use to derive unique id from"
}
```

**Response:**
```json
{
  "id": "userId"
}
```

### Get user info
**GET** `/users/{userId}`
Retrieve details of a user (not very useful yet, but could be if we add more user details later)

**Response:**
```json
{
  "id": "userId",
}
```

### Delete a user
**DELETE** `/users/{userId}`

### Get all users
**GET** `/users`
Retrieve all users.

**Response:**
```json
[
  { "id": "userId1" },
  { "id": "userId2" }
]
```

## Groups

### Create a Group
**POST** `/groups`  
Create a new expense-sharing group.

**Request body:**
```json
{
  "name": "Summer Trip",
  "description": "Trip to Spain",
  "currency": "EUR"
}
```

**Response:**
```json
{
  "id": "groupId",
  "name": "Summer Trip",
  "description": "Trip to Spain",
  "currency": "EUR"
}
```

### Get Group Info
**GET** /groups/{groupId}
Retrieve details of a group.

**Response:**
```json
{
  "id": "groupId",
  "name": "Summer Trip",
  "description": "Trip to Spain",
  "currency": "EUR"
}
```

### Get group infos for all groups of a user
**GET** /groups/user/{userId}

### Update group details.
**PUT** `/groups/{groupId}`
Update group details.

**Request body:**
```json
{
  "name": "New Name",
  "description": "New Description",
  "currency": "USD"
}
```

**DELETE** `/groups/{groupId}`
Delete a group.

### List Group Members
**GET** `/groups/{groupId}/members`
Retrieve all members of a group.

**Response:**
```json
[
  { "id": "userId1", "pseudo": "Alice" },
  { "id": "userId2", "pseudo": "Bob" }
]
```

### Add Member to Group
**POST** `/groups/{groupId}/members`
Add a user to a group.

**Request body:**
```json
{
  "userId": "12345",
  "pseudo" : "myname"
}
```

### Get all groups
**GET** `/groups`
Retrieve all groups.

**Response:**
```json
[
  {
    "id": "groupId",
    "name": "Summer Trip",
    "description": "Trip to Spain",
    "currency": "EUR"
  }
]
```

## Expenses

### Add Expense
**POST** `/groups/{groupId}/expenses`
Add a new expense to a group.

**Request body:**
```json
{
  "name": "Dinner",
  "category": "Food",
  "currency": "EUR",
  "date": "2025-08-26",
  "paidBy": [
    { "userId": "userId1", "amount": 60.0 }
  ],
  "paidFor": [
    { "userId": "userId1", "amount": 30.0 },
    { "userId": "userId2", "amount": 30.0 }
  ]
}
```

**Constraints:**
- Only users in the group can pay or be paid for.
- The sum of `paidBy.amount` and `paidFor.amount` must be equal.

### Get Expenses for Group
**GET** `/groups/{groupId}/expenses`
Retrieve all expenses for a group.

**Response:**
```json
[
  {
    "id": "expenseId",
    "name": "Dinner",
    "category": "Food",
    "currency": "EUR",
    "date": "2025-08-26",
    "paidBy": [ { "userId": "userId1", "amount": 60.0 } ],
    "paidFor": [ { "userId": "userId1", "amount": 30.0 }, { "userId": "userId2", "amount": 30.0 } ]
  }
]
```

### Update Expense
**PUT** `/groups/{groupId}/expenses/{expenseId}`
Update an expense.

**DELETE** `/groups/{groupId}/expenses/{expenseId}`
Delete an expense.

### Get all expenses
**GET** `/expenses`
Retrieve all expenses.

**Response:**
```json
[
  {
    "id": "expenseId",
    "name": "Dinner",
    "category": "Food",
    "currency": "EUR",
    "date": "2025-08-26",
    "paidBy": [ { "userId": "userId1", "amount": 60.0 } ],
    "paidFor": [ { "userId": "userId1", "amount": 30.0 }, { "userId": "userId2", "amount": 30.0 } ]
  }
]
```

## Settlements

### Get Balances for Group
**GET** `/groups/{groupId}/balances`
Retrieve who owes whom and how much in a group.

**Response:**
```json
[
  { "from": "userId1", "to": "userId2", "amount": 15.0 }
]
```

### Settle Up
**POST** `/groups/{groupId}/settle`
Record a settlement/payment between users.

**Request body:**
```json
{
  "from": "userId1",
  "to": "userId2",
  "amount": 50.0
}
```
