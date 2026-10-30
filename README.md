# IMovies MERN cinema booking

## Run
1. Install Node.js 18+ and MongoDB.
2. In the project root run `npm install`.
3. Copy `server/.env.example` to `server/.env`. Set a strong `JWT_SECRET` and your MongoDB URI.
4. Start MongoDB, then run `npm run dev`.
5. Open http://localhost:5173. API health: http://localhost:5000/api/health.

## Included
- React/Vite cinema discovery UI, search, genre filters, responsive layout.
- Demo seat selection, showtime choice, booking confirmation and browser-local booking history.
- Express API with MongoDB User, Movie, Show and Booking models.
- Password hashing, JWT authentication, admin role middleware, Helmet and rate limiting.
- Movie search, booking history, atomic seat booking in MongoDB transactions, cancellation.
- Socket.IO show-room events for seat updates.
- Admin movie create/update/archive and show creation endpoints.

## Important limitations
The included browser interface is a functional demo and uses sample catalogue data plus localStorage. It is not wired to the API yet. Real-time events are emitted by the API, but the demo UI does not subscribe. Payment is a placeholder reference, not a payment gateway. A production release still needs a payment provider with server-side verification/webhooks, expiring seat holds, theatre CRUD and show browsing UI, input validation schemas, tests, deployment configuration and monitoring. MongoDB transactions require a replica set (MongoDB Atlas supports this). Do not call this production-ready until those pieces are implemented and tested.

## Admin
Register a user through `POST /api/auth/register`, then promote that account manually in MongoDB:
`db.users.updateOne({email:"admin@example.com"},{$set:{role:"admin"}})`
Never expose public admin registration.
