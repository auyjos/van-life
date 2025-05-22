# VanLife

VanLife is a React-based web application that allows users to browse, rent, and host vans for van life adventures. The application includes features for both customers and van hosts, with protected routes that require authentication.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Environment Setup](#environment-setup)
- [Project Structure](#project-structure)
- [Firebase Integration](#firebase-integration)
- [Development Server](#development-server)
- [Authentication](#authentication)
- [Deployment](#deployment)
- [License](#license)

## Features

- **Van Browsing**: Users can browse available vans and filter by type (simple, luxury, rugged)
- **Van Details**: View detailed information about each van including pricing, description, and photos
- **Host Dashboard**: Van hosts can view their listed vans, income statistics, and customer reviews
- **Authentication**: Protected routes for host functionality requiring login
- **Responsive Design**: Mobile-friendly interface for on-the-go browsing

## Technologies Used

- **Frontend**: React
- **Routing**: React Router v6
- **API Mocking**: MirageJS (for development)
- **Backend/Database**: Firebase Firestore
- **Build Tool**: Vite
- **Styling**: CSS

## Getting Started

Install the dependencies and run the project:
```
npm install
npm run dev
```

Head over to https://vitejs.dev/ to learn more about configuring Vite.

## Environment Setup

Create a `.env` file in the root directory with your Firebase configuration:

```
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
VITE_FIREBASE_PROJECT_ID=your_firebase_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_firebase_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_firebase_messaging_sender_id
VITE_FIREBASE_APP_ID=your_firebase_app_id
VITE_FIREBASE_MEASUREMENT_ID=your_firebase_measurement_id
```

## Project Structure

```
/
├── assets/               # Static assets like images
├── components/           # Reusable UI components
│   ├── AuthRequired.jsx  # Authentication wrapper component
│   ├── Footer.jsx        # Site footer component
│   ├── Header.jsx        # Site header with navigation
│   ├── HostLayout.jsx    # Layout for host pages
│   └── Layout.jsx        # Main layout wrapper
├── pages/                # Application pages
│   ├── About.jsx         # About page
│   ├── Home.jsx          # Landing page
│   ├── Login.jsx         # Login page
│   ├── NotFound.jsx      # 404 page
│   ├── Host/             # Host-specific pages
│   │   ├── Dashboard.jsx
│   │   ├── HostVans.jsx
│   │   ├── HostVanDetail.jsx
│   │   ├── Income.jsx
│   │   └── Reviews.jsx
│   └── Vans/             # Van listing and detail pages
│       ├── Vans.jsx
│       └── VanDetail.jsx
├── api.js                # Firebase API integration
├── index.jsx             # Application entry point
├── server.js             # MirageJS mock server
└── vite.config.js        # Vite configuration
```

## Firebase Integration

This project uses Firebase Firestore for data storage. The `api.js` file contains functions for fetching van data from Firebase. During development, MirageJS is used to mock the API responses.

To set up your own Firebase project:

1. Create a Firebase project in the [Firebase Console](https://console.firebase.google.com/)
2. Create a Firestore database
3. Create a "vans" collection with documents following this structure:
   ```
   {
     "id": "1", 
     "name": "Van Name",
     "price": 60,
     "description": "Van description...",
     "imageUrl": "image-url",
     "type": "simple", // or "luxury" or "rugged"
     "hostId": "123"
   }
   ```
4. Add your Firebase config to the .env file

## Development Server

The project includes a MirageJS mock server (`server.js`) that provides fake API endpoints during development. This allows for development without requiring an actual backend.

To use the mock server:
- The mock server is automatically started when you run the development server
- It provides endpoints for fetching vans, van details, and handling authentication
- It passes through requests to Firebase so both can be used simultaneously

To use Firebase instead of the mock server, ensure your Firebase configuration is set up correctly in the `.env` file and the appropriate Firestore rules are configured.

## Authentication

The application includes a simple authentication system with protected routes for host functionality. For the mock server:

- Email: test.com
- Password: 123

For production, implement proper Firebase Authentication.

## Deployment

### Building for Production

```bash
npm run build
```

This will generate a `dist` folder with optimized production build.

### Deploying to Vercel

1. Push your code to a GitHub repository
2. Connect the repository to Vercel
3. Configure environment variables in Vercel dashboard
4. Deploy

### Deploying to Netlify

1. Push your code to a GitHub repository
2. Connect the repository to Netlify
3. Configure environment variables in Netlify dashboard
4. Deploy

### Deploying to Firebase Hosting

1. Install Firebase CLI:
   ```bash
   npm install -g firebase-tools
   ```

2. Login to Firebase:
   ```bash
   firebase login
   ```

3. Initialize Firebase project:
   ```bash
   firebase init
   ```

4. Select Firebase Hosting and follow the prompts
   - Use "dist" as your public directory
   - Configure as a single-page app

5. Build and deploy:
   ```bash
   npm run build
   firebase deploy
   ```

## License

This project is open source and available under the MIT License.
