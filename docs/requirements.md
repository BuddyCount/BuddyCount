# BuddyCount requirements

## Functional requirements

### Group creation 
Users can create a group via a dedicated widget on the welcome page.

Users can invite any other user using an auto-generated invite link.

Users can join an existing group via an invite link provided by another user, and choose their name in a list of members of said group.

### Expense Tracking

Users can record an expense.

Users can choose who paid for the expense.

Users can choose a category for their expense.

Users can choose and select the members of the group that are concerned by the expense.

Users can modify and update existing expenses.

The app must categorize the expense automatically in case the user didn't.

Users can upload images with their expense.

Users can select the shares of each user concerned by the expense.

Users can select multiple payers for an expense.

Users can select the date and time at which the expense was made.


### Balance tracking and debt settlement

Users can easily see their balance in a dedicated widget.

Users can see their debts, and specifically who they owe money to in order to settle their debt within the group.

### Expense Prediction and statistics

The app displays statistics via a dedicated analytics widget, which displays spending history with a plot over time.

Users can filter the analytics widget in order to show expense analytics for a given user, or for a given time frame.

## Customizable Expenses View

All expenses are shown in a dedicated widget.

Users can filter the expense list to show expenses concerning a given user, or a given time frame.

Users can click on an expense to see it's inherent details, attached images.

Users can delete any expense.

### Multi-Currency Support

Users can choose the currency of their expense.

If the currency of an expense differs from the base currency of a group, the app automatically converts into that currency, via a customizable exchange rate.


### Account-less Usage

Users can operate the app without creating an account or logging in.


### Offline functionnality

Users can use all features of the app when their device is offline: group and expense creation / deletion / modification.

## Non-functional requirements

User-Friendliness in UX and UI.

The interface must be intuitive and accessible by anyone.

### Secure Data Storage

All user data must be stored securely.

The app must be privacy oriented, with no personal data stored, and authentified access to any service.

The app must be designed to respect user privacy by eliminating the need for personal information or accounts. 

### Cross-Platform Compatibility

The app must be compatible with most modern platforms, namely Android and iOS devices, and web browsers.

### Performance & Responsiveness

The app should remain fast and responsive, even as entries grow.

### Reliability 

Given account-less operation, data integrity must be ensured locally, potentially with offline capabilities or local caching.

Users must be able to sync offline data with the api whenever they are back online.
