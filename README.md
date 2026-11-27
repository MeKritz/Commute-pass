# CommutePass – Lab Exercise 8 (Full Stack REST API)

This project extends the CommutePass ride-booking domain from Lab Exercises 5 & 6.
It replaces browser Local Storage with a SQLite database accessed through an Express
REST API. The React/Vite client uses Axios.

## Requirements
- Node.js 18 or newer
- npm

## Run the application

Open **two terminals** in the `CommutePass_Lab8` folder.

### Terminal 1 – backend
```bash
cd server
npm install
npm run dev
```
The API runs at `http://localhost:5000`. SQLite creates `database.db` and the
`bookings` table automatically on first start.

### Terminal 2 – frontend
```bash
cd client
npm install
npm run dev
```
Open the URL printed by Vite (normally `http://localhost:5173`).

## REST API
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/bookings` | List bookings |
| GET | `/api/bookings/:id` | Get one booking |
| GET | `/api/bookings?status=Confirmed` | Filter by status |
| GET | `/api/bookings?vehicle=Auto` | Filter by vehicle |
| GET | `/api/bookings?search=Krithika` | Search passenger/route |
| POST | `/api/bookings` | Create booking |
| PUT | `/api/bookings/:id` | Update booking |
| DELETE | `/api/bookings/:id` | Delete booking |

Filters can be combined, for example:
`/api/bookings?status=Confirmed&vehicle=Auto&search=MG`

## Test with Thunder Client / Postman

POST `http://localhost:5000/api/bookings`
Header: `Content-Type: application/json`
```json
{
  "name": "Krithika",
  "pickup": "Electronic City",
  "destination": "MG Road",
  "date": "2026-12-01",
  "time": "09:00",
  "vehicle": "Auto",
  "payment": "UPI",
  "fare": 142,
  "distanceKm": 8,
  "status": "Confirmed",
  "bookingMode": "Manual"
}
```

## Notes
- The fare preview in the UI uses the same simple vehicle base + per-km estimate
  structure as the original domain project. It is an estimate for demonstration.
- Voice booking, real map-distance lookup, payment processing and deployment are
  not configured in this starter ZIP; the main Lab 8 requirement is full-stack
  database-backed booking CRUD and filtering.
- Do not upload `server/database.db` if you do not want to submit your local test data.
