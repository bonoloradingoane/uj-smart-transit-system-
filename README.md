# UJ Smart Transit Queue & Tracking App (Angular & Firestore)

This project is a sophisticated web application built with **Angular (Standalone Components)**, **Tailwind CSS**, and **Firebase Firestore** to provide students with real-time transit information and a persistent virtual queuing system for campus shuttles.

## Key Features

* **Firebase Firestore:** Implements persistent storage for user-specific virtual queue bookings.
* **Firebase Authentication:** Handles user authentication automatically to secure private booking data.
* **Real-Time UI:** Uses Angular Signals and Firestore's `onSnapshot` listener to ensure the queue status updates in real-time.
* **Google Maps Integration:** Displays bus markers and allows users to zoom to specific shuttle locations.
* **Responsive Design:** Provides an excellent user experience across mobile, tablet, and desktop devices.
* **Virtual Queuing:** Allows users to book and cancel a single queue spot for a scheduled route.

## Technology Stack

* **Framework:** Angular (Standalone Component Architecture)
* **Styling:** Tailwind CSS for rapid, utility-first styling.
* **Mapping:** Google Maps JavaScript API for dynamic visualization.
* **Database:** Firebase Firestore (Real-time NoSQL database)
* **Authentication:** Firebase Auth (Custom Token/Anonymous Sign-in)

## Data Structure (Firestore)

User bookings are stored securely under the authenticated user's ID:

/artifacts/{appId}/users/{userId}/bookings/active_booking


Each `active_booking` document contains:

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Static ID: 'active_booking' |
| `route` | String | The bus route booked (e.g., 'APB to DFC Shuttle') |
| `departureTime` | String | The scheduled departure time |
| `queuePosition` | Number | The user's mock position in the queue (1-5) |
| `timestamp` | Number | UNIX timestamp of the booking creation |

## Setup and Usage

1.  **Access:** The application runs as a single, self-contained Angular TypeScript file (`src/app.ts`).
2.  **Authentication:** Upon loading, the app automatically initializes Firebase and authenticates the user, displaying a unique `User ID` needed for data storage.
3.  **Booking:** Select a route from the schedule and click the **Queue** button. The booking is instantly saved to Firestore, and the status box updates.
4.  **Persistence:** Refresh the browser or reload the app. The booking status will persist because it is loaded from the database using the `onSnapshot` listener associated with your `userId`.
5.  **Cancellation:** Click **Cancel Booking** to delete the record from Firestore and clear your status.
