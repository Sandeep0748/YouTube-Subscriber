
# Get YouTube Subscriber
(AlmaBetter__Capstone__Project)

This project is a backend application built with Express.js and Node.js that allows users to retrieve subscriber information from YouTube channels.

## Features

- Retrieve subscriber information including Name, ID subscription date, and subscribed channel.
- Get subscriber names along with their respective channels.
- Retrieve subscriber information for a specific user using their ID.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/get-youtube-subscriber.git
```

2. Navigate to the project directory:

```bash
cd get-youtube-subscriber
```

3. Install dependencies:

```bash
npm install
```


## Usage

### Starting the Server

Run the following command to start the server:

```bash
npm start
```

By default, the server will run on port `3000`. You can access the endpoints at `http://localhost:3000`.

### Endpoints

#### 1. Get Subscriber Information

- **Route:** `/subscribers`
- **Method:** `GET`
- **Description:** Retrieves subscriber information as an array of all subscribers in the database.
- (http://localhost:3000/subscribers)
# Get YouTube Subscriber (backend)

Small Express + MongoDB API to store and return YouTube subscriber records. This repository contains endpoints to list subscribers, get names, fetch by id, and add new subscribers.

This README contains quick setup and testing instructions.

## Features

- List all subscribers
- List subscriber names and channels
- Fetch a subscriber by ID
- Create a new subscriber (POST /subscribers)

## Prerequisites

- Node.js (recommended v18 or v20)
- npm
- A MongoDB instance (Atlas or local)

## Quick start

1. Clone the repo and install dependencies:

```powershell
git clone https://github.com/Sandeep0748/YouTube-Subscriber.git
cd 'YouTube-Subscriber/get-youtube-subscriber'
npm install
```

2. Create a `.env` file in the project root with the following variables (example):

```properties
# example .env
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.xyz.mongodb.net/subscribers?retryWrites=true&w=majority
PORT=3000
```

3. Start the server:

```powershell
npm start
```

The API will be available at `http://localhost:3000`.

## API Endpoints

- GET /subscribers
        - Returns an array of all subscribers.

- GET /subscribers/names
        - Returns subscriber names and channels (no IDs, no dates).

- GET /subscribers/:id
        - Returns a single subscriber by MongoDB `_id`.

- POST /subscribers
        - Creates a new subscriber. Request body (JSON):

```json
{
        "name": "Jane Doe",
        "subscribedChannel": "Awesome Channel",
        "subscribedDate": "2025-10-15T12:00:00Z"  // optional
}
```

        - Responses:
                - 201: created, returns the created document (without `__v`).
                - 400: missing `name` or `subscribedChannel`.
                - 500: internal server error.

## Example: create a subscriber (PowerShell)

```powershell
$body = @{ name = 'Jane Doe'; subscribedChannel = 'Awesome Channel' } | ConvertTo-Json
Invoke-RestMethod -Uri http://localhost:3000/subscribers -Method Post -Body $body -ContentType 'application/json'
```

## Project structure

```
get-youtube-subscriber/
├─ index.js             # server bootstrap and mongoose connect
├─ package.json
├─ .env                 # local env (not committed)
├─ src/
│  ├─ app.js            # express app and routes
│  ├─ createDatabase.js # helper used to populate DB (optional)
│  ├─ data.js           # sample data used by createDatabase
+│  └─ models/
│     └─ subscribers.js  # Mongoose model
```

## Notes

- `.env` contains your DB credentials — do not commit it. A `.gitignore` has been added to ignore `.env` and `node_modules`.
- If you committed `.env` previously, rotate those credentials and remove the file from the repo history.

## Deployment (Vercel)

This repo contains a `vercel.json` configured to use `index.js` as the entry point for Vercel deployments. Add environment variables in the Vercel dashboard (`MONGO_URI`, `PORT`) before deploying.

## Tests

No automated tests are included. You can add tests under `__tests__` and run the existing test script in `package.json`.

## Contributing

Contributions welcome — open issues or PRs.

---

If you'd like, I can also:

- Add an `env.example` file with placeholders.
- Add a simple test that verifies POST /subscribers works.
- Remove `.env` from git history safely if it was committed earlier.

