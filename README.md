# 🌐 JourneyJournal

JourneyJournal is a community-driven platform where users can share and explore travel experiences from around the globe! 🌍 Share details of your adventures, learn about exciting destinations, and connect with fellow travelers!

## 🚀 Features

- **Post Trips**: Share details of your travel experiences, from destinations and duration to travel costs.
- **Explore**: Browse trips shared by other users.
- **Filter & Search**: Easily find specific trips or destinations.
- **Community Driven**: Engage with other travelers and learn from their experiences.
- **Categories**: Classify trips into various categories for easier navigation and exploration.

## Database Schema

### Entity-Relationship Diagram (ERD)
![ERD of JourneyJournal Database](entitydesign.png)

### Data Dictionary

#### Table: `Trips`

| Field Name | Data Type | Description | Constraints |
|------------|-----------|-------------|-------------|
| TripID | int | Unique identifier for each trip | Primary Key, Unique, Auto-Increment |
| Destination | varchar | Destination of the trip | Not Null |
| StartDate | date | Start date of the trip | Not Null |
| EndDate | date | End date of the trip | Not Null |
| DurationDays | int | Duration of the trip in days | Not Null |
| TravelerName | varchar | Name of the traveler | Not Null |
| TravelerAge | int | Age of the traveler | - |
| TravelerGender | varchar | Gender of the traveler | - |
| TravelerNationality | varchar | Nationality of the traveler | - |
| TripComment | varchar | Comment provided by the user about the trip | - |

#### Table: `Expenses`

| Field Name | Data Type | Description | Constraints |
|------------|-----------|-------------|-------------|
| ExpenseID | int | Unique identifier for each expense | Primary Key, Unique, Auto-Increment |
| TripID | int | Identifier of the associated trip | Foreign Key referencing `Trips.TripID` |
| MainAccommodationType | varchar | Type of main accommodation for the trip | - |
| AccommodationCost | float | Cost of the accommodation | - |
| MainTransportationType | varchar | Type of main transportation used during the trip | - |
| TransportationCost | float | Cost of the transportation | - |

#### Table: `TripCategories`

| Field Name | Data Type | Description | Constraints |
|------------|-----------|-------------|-------------|
| CategoryID | int | Unique identifier for each category | Primary Key, Unique, Auto-Increment |
| CategoryName | varchar | Name of the category (e.g., Business, Vacation) | Not Null |

#### Table: `TripCategoryAssociations`

| Field Name | Data Type | Description | Constraints |
|------------|-----------|-------------|-------------|
| TripCategoryID | int | Unique identifier for each trip-category association | Primary Key, Unique, Auto-Increment |
| TripID | int | Identifier of the associated trip | Foreign Key referencing `Trips.TripID` |
| CategoryID | int | Identifier of the associated category | Foreign Key referencing `TripCategories.CategoryID` |

### Descriptions:
- The `Trips` table holds the main data about each trip.
- The `Expenses` table holds data about the expenses associated with each trip.
- The `TripCategories` table holds different categories under which trips can be classified.
- The `TripCategoryAssociations` table establishes a many-to-many relationship between trips and categories.

### Relationships:
- **Trips to Expenses**: One-to-many from `Trips` to `Expenses`, as one trip can have multiple expenses but each expense is associated with one trip.
- **Trips to TripCategories through TripCategoryAssociations**: Many-to-many, as one trip can fall under multiple categories and each category can be associated with multiple trips.

