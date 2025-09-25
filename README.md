# GridSafe - IoT Power Distribution Monitoring System

A comprehensive IoT-based solution for detecting breakage of Low Voltage AC Distribution Over Head conductors, developed for Kerala State Electricity Board Limited (KSEBL).

## 🚀 Features

### Core Functionality
- **Real-time Monitoring**: Live tracking of R, Y, B phase status across all poles
- **Fault Detection**: Instant alerts for phase cuts, low voltage, and communication failures
- **Role-based Access**: Admin, Zone Officer, and Field Staff permissions
- **Multi-language Support**: English, Malayalam, Hindi
- **Interactive Maps**: Leaflet-based visualization with pole locations
- **Historical Analysis**: Voltage trends and fault history with export capabilities

### Security Features
- **JWT Authentication**: Secure token-based access
- **OTP Verification**: Government-level 2FA security
- **Password Reset**: Secure password recovery flow
- **Role-based Authorization**: Granular permission system

### Real-time Features
- **WebSocket Alerts**: Instant notifications for critical events
- **Browser Notifications**: Desktop alerts for urgent faults
- **Live Dashboard**: Real-time summary cards and map updates
- **Mock Data Generation**: Automated test alerts every 30 seconds

## 🏗️ Architecture

### Backend (Node.js + Express)
- **Database**: Prisma ORM with SQLite (dev) / PostgreSQL (production)
- **Authentication**: JWT with bcrypt password hashing
- **Real-time**: Socket.IO for WebSocket connections
- **API**: RESTful endpoints with role-based access control

### Frontend (React + TypeScript)
- **Framework**: Vite + React 18 + TypeScript
- **Routing**: React Router with protected routes
- **State**: Context API for authentication
- **Charts**: Recharts for voltage history visualization
- **Maps**: React Leaflet for interactive mapping
- **i18n**: React i18next for multi-language support

## 📋 Prerequisites

- Node.js 18+ 
- npm 9+
- Git

## 🚀 Quick Start

### 1. Clone and Setup
```bash
git clone <repository-url>
cd freact
npm install
```

### 2. Install Dependencies
```bash
npm run setup
```

### 3. Start Development Servers
```bash
npm run dev
```

This will start:
- Backend API: http://localhost:4000
- Frontend App: http://localhost:5173

### 4. Login Credentials
- **Username**: `admin`
- **Password**: `Admin@123`
- **OTP**: Check console for mock OTP (6 digits)

## 📁 Project Structure

```
freact/
├── package.json                 # Root package with scripts
├── README.md                   # This file
└── fullstack/
    ├── backend/                # Node.js API server
    │   ├── src/
    │   │   ├── server.ts      # Express server + WebSocket
    │   │   └── seed.ts        # Database seeding
    │   ├── prisma/
    │   │   └── schema.prisma  # Database schema
    │   └── package.json
    └── frontend/
        └── app/               # React frontend
            ├── src/
            │   ├── pages/     # Route components
            │   ├── components/ # Reusable components
            │   ├── state/     # Auth context
            │   └── i18n.ts    # Internationalization
            └── package.json
```

## 🔧 Available Scripts

### Root Level
- `npm run dev` - Start both backend and frontend in development mode
- `npm run setup` - Install all dependencies and setup database
- `npm run db:reset` - Reset database and reseed with sample data
- `npm run db:seed` - Add sample data to existing database

### Backend
- `npm run backend:dev` - Start backend development server
- `npm run backend:build` - Build backend for production
- `npm run backend:start` - Start production backend server

### Frontend  
- `npm run frontend:dev` - Start frontend development server
- `npm run frontend:build` - Build frontend for production
- `npm run frontend:start` - Start production frontend server

## 🗄️ Database Schema

### Core Entities
- **Users**: Admin, Zone Officer, Field Staff with role-based access
- **Zones**: Geographic areas with coordinates and descriptions
- **Poles**: Individual monitoring points with phase status and metadata
- **Alerts**: Fault events with severity levels and timestamps

### Key Relationships
- Users can be assigned to multiple zones
- Poles belong to zones and can have assigned technicians
- Alerts are linked to specific poles and zones

## 🌐 API Endpoints

### Authentication
- `POST /api/auth/login` - User login with OTP
- `POST /api/auth/request-otp` - Request OTP for user
- `POST /api/auth/forgot-password` - Password reset request
- `POST /api/auth/reset-password` - Password reset with token

### Data Management
- `GET /api/zones` - List all zones with poles
- `GET /api/poles` - List poles (with optional zone filter)
- `GET /api/poles/:id` - Get pole details with history
- `GET /api/alerts` - List alerts with filtering
- `POST /api/alerts` - Create new alert (broadcasts via WebSocket)

### Admin Operations
- `GET /api/users` - List users (Admin only)
- `PUT /api/users/:id` - Update user (Admin only)
- `DELETE /api/users/:id` - Delete user (Admin only)
- Similar CRUD operations for zones and poles

## 🔌 WebSocket Events

### Client → Server
- Connection established automatically on page load

### Server → Client
- `newAlert` - Broadcast when new fault detected
- Includes alert details: severity, message, zone, pole info

## 🎨 User Interface

### Pages
1. **Login**: Username/password + OTP verification
2. **Dashboard**: Summary cards + live map with pole markers
3. **Zones**: Zone list + pole status table
4. **Pole Detail**: Phase status, voltage charts, fault history, metadata
5. **Alerts**: Real-time alert feed with WebSocket updates
6. **History**: Filterable alerts with CSV export
7. **Admin**: User/zone/pole management (Admin role only)

### Key Features
- **Responsive Design**: Works on desktop and mobile
- **Color Coding**: Red (critical), Yellow (warning), Green (normal)
- **Interactive Maps**: Click markers for pole details
- **Real-time Updates**: Live alerts and status changes
- **Export Capabilities**: CSV download for reports

## 🔒 Security Considerations

### Authentication
- JWT tokens with 12-hour expiration
- Password hashing with bcrypt (10 rounds)
- OTP verification for government-level security

### Authorization
- Role-based access control (RBAC)
- Protected routes and API endpoints
- Admin-only operations clearly separated

### Data Protection
- Input validation with Zod schemas
- SQL injection prevention via Prisma ORM
- CORS configuration for frontend access

## 🚀 Production Deployment

### Environment Variables
```bash
# Backend (.env)
DATABASE_URL="postgresql://user:password@localhost:5432/gridsafe"
JWT_SECRET="your-super-secret-jwt-key"
OTP_PROVIDER="twilio" # or "mock" for development
PORT=4000
```

### Database Migration
```bash
# Switch to PostgreSQL for production
cd fullstack/backend
# Update prisma/schema.prisma datasource to postgresql
npm run prisma:migrate:deploy
npm run prisma:seed
```

### Build for Production
```bash
npm run backend:build
npm run frontend:build
```

## 🧪 Testing Features

### Mock Data
- Sample zones: Trivandrum Zone, Kochi Zone
- Sample poles: TVM-001, KOC-015
- Mock voltage data generation
- Automated alert generation (every 30 seconds)

### Development Tools
- Hot reload for both frontend and backend
- TypeScript compilation with error checking
- Prisma Studio for database inspection

## 📞 Support

For technical support or feature requests, contact the KSEBL development team.

## 📄 License

This project is developed for Kerala State Electricity Board Limited (KSEBL) under government guidelines for power distribution monitoring systems.

---

**Note**: This system is designed to prevent electrocution deaths by detecting broken live conductors and providing immediate alerts to control rooms and field staff for rapid response and isolation of hazardous conditions.
