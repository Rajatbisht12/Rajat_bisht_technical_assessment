# Integrations Technical Assessment

This project is a full-stack application that demonstrates integration with various third-party services (HubSpot, Airtable, and Notion) using OAuth2 authentication. The application allows users to connect to these services and retrieve data from them.

## Project Structure

```.
├── frontend/
│ ├── src/ 
│ ├── public/ # Static files
│ └── package.json # Frontend dependencies
├── backend/ # FastAPI backend application
│ ├── integrations/ # Integration-specific code
│ ├── main.py # Main application file
│ └── requirements.txt # Backend dependencies
└── dump.rdb # Redis database file
```

## Features

- OAuth2 authentication with multiple services:
  - HubSpot
  - Airtable
  - Notion
- Modern React frontend with Material-UI components
- FastAPI backend with async support
- Redis for state management and caching
- Secure credential handling

## Prerequisites

Before running the application, make sure you have the following installed:

- Node.js (v14 or higher)
- Python (v3.8 or higher)
- Redis server
- Git

## Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd integrations_technical_assessment
```

### 2. Set up the backend

```bash
# Navigate to the backend directory
cd backend

# Create and activate a virtual environment
python -m venv myvenv
source myvenv/bin/activate  # On Windows: myvenv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Set up the frontend

```bash
# Navigate to the frontend directory
cd frontend

# Install dependencies
npm install
```

### 4. Configure environment variables

Create a `.env` file in the backend directory with the following variables:

```env
REDIS_HOST=localhost
```

## Running the Application

### 1. Start Redis server

Make sure Redis is running on your system. By default, it should run on `localhost:6379`.

### 2. Start the backend server

```bash
# From the backend directory
uvicorn main:app --reload
```

The backend server will start on `http://localhost:8000`

### 3. Start the frontend development server

```bash
# From the frontend directory
npm start
```

The frontend application will start on `http://localhost:3000`

## Usage

1. Open your browser and navigate to `http://localhost:3000`
2. You'll see a form with fields for User and Organization
3. Select an integration type from the dropdown (HubSpot, Airtable, or Notion)
4. Click the "Connect" button to initiate the OAuth2 flow
5. After successful authentication, you can load data from the selected service

## API Endpoints

### HubSpot Integration
- `POST /integrations/hubspot/authorize` - Start HubSpot OAuth flow
- `GET /integrations/hubspot/oauth2callback` - HubSpot OAuth callback
- `POST /integrations/hubspot/credentials` - Get HubSpot credentials
- `POST /integrations/hubspot/load` - Load HubSpot data

### Airtable Integration
- `POST /integrations/airtable/authorize` - Start Airtable OAuth flow
- `GET /integrations/airtable/oauth2callback` - Airtable OAuth callback
- `POST /integrations/airtable/credentials` - Get Airtable credentials
- `POST /integrations/airtable/load` - Load Airtable data

### Notion Integration
- `POST /integrations/notion/authorize` - Start Notion OAuth flow
- `GET /integrations/notion/oauth2callback` - Notion OAuth callback
- `POST /integrations/notion/credentials` - Get Notion credentials
- `POST /integrations/notion/load` - Load Notion data

## Technologies Used

### Frontend
- React
- Material-UI
- Axios
- ReactFlow

### Backend
- FastAPI
- Redis
- Python OAuth2
- Uvicorn

## Security Considerations

- OAuth2 state validation to prevent CSRF attacks
- Secure storage of credentials in Redis with expiration
- CORS protection
- Environment variable configuration

## Troubleshooting

1. If you encounter Redis connection issues:
   - Ensure Redis server is running
   - Check if Redis is accessible on localhost:6379
   - Verify Redis connection in the backend logs

2. If OAuth flows fail:
   - Check browser console for errors
   - Verify OAuth credentials are properly configured
   - Ensure callback URLs are correctly set up in the service providers' dashboards

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
