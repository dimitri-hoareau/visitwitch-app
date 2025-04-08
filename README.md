# VisitWitch App

A web application that allows users to search for videos related to video games via the Twitch API.

## Overview

VisitWitch App enables users to:

- Search for video games using a search field
- Display a list of videos related to the selected game in real-time
- Videos results are automatically updated every 2 minutes

## Technologies

- **Frontend**: Vue.js with Vite
- **Backend**: FastAPI (Python)
- **Database**: MongoDB
- **API**: Twitch API
- **Containerization**: Docker and Docker Compose

## Installation

### Prerequisites

- Docker and Docker Compose installed on your machine
- A Twitch developer account to obtain API credentials

### Clone the repository

```bash
# Option 1: Clone with submodules in one command
git clone --recurse-submodules https://github.com/dimitri-hoareau/visitwitch-app.git

# Option 2: Clone and then update submodules separately
git clone https://github.com/dimitri-hoareau/visitwitch-app.git
cd visitwitch-app
git submodule init
git submodule update --remote
```

### Configure Twitch API credentials

1. Create a .env file in the root directory with the following content:

```bash
TWITCH_CLIENT_ID=your_twitch_client_id
TWITCH_CLIENT_SECRET=your_twitch_client_secret
```

2. To obtain your Twitch API credentials:

- Go to the Twitch Developer Console

- Log in with your Twitch account

- Create a new application

- Note down the Client ID and generate a Client Secret

- Add http://localhost as an OAuth Redirect URL

## Running the application

Start all services using Docker Compose:

```bash
docker-compose up -d
```

The application will be available at:

Frontend: http://localhost:5173

Backend API: http://localhost:8000/docs

## Database Usage

While MongoDB isn't directly essential for the core functionality of this application, it has been integrated to store watched videos for potential future features such as:

- Viewing history
- Video recommendations
- User preferences

To verify that videos are being saved in the database when clicked:

```bash
docker exec -it visitwitch-mongodb mongosh -u admin -p password
use visitwitch
db.watched_videos.find()
```

## Implementation Notes

The 2-minute refresh functionality is implemented using setTimeout in the Video.vue component. It has been commented out in the current version as it was generating too many requests. This would be optimized in future iterations.

## Future Improvements

- Testing suite: Frontend, backend, and integration tests
- Optimize the 2-minute refresh mechanism
- Embed videos using iframes (potentially with a backend scraping tool)
- Complete API documentation
- Enhanced UX/UI (controlled search bar similar to YouTube, loading indicators)
- More precise backend filtering
- Add "Last Updated" timestamp in the footer
- User authentication system
- Personalized recommendations based on viewing history

Created by Dimitri Hoareau
