# GridSafe Development Environment

## Quick Start Commands

```bash
# Install all dependencies and setup database
npm run setup

# Start both backend and frontend in development mode
npm run dev

# Reset database with fresh sample data
npm run db:reset
```

## Development URLs
- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:4000
- **Database**: SQLite file at `fullstack/backend/dev.db`

## Login Credentials
- **Username**: `admin`
- **Password**: `Admin@123`
- **OTP**: Check console for mock OTP (6 digits)

## Key Features Implemented
✅ **Authentication**: JWT + OTP verification  
✅ **Real-time Alerts**: WebSocket with browser notifications  
✅ **Interactive Maps**: Leaflet with pole markers  
✅ **Voltage Charts**: Recharts with historical data  
✅ **Admin Panel**: Full CRUD for users/zones/poles  
✅ **Multi-language**: English, Malayalam, Hindi  
✅ **Export**: CSV download for reports  
✅ **Role-based Access**: Admin, Zone Officer, Field Staff  

## Project Structure
```
freact/
├── package.json          # Root scripts
├── README.md            # Full documentation
└── fullstack/
    ├── backend/         # Node.js + Express + Prisma
    └── frontend/app/    # React + TypeScript + Vite
```

## Mock Data
- **Zones**: Trivandrum Zone, Kochi Zone
- **Poles**: TVM-001, KOC-015 with GPS coordinates
- **Alerts**: Auto-generated every 30 seconds for testing
- **Voltage**: Mock historical data for charts

## Next Steps for Production
1. Replace SQLite with PostgreSQL
2. Integrate real OTP provider (Twilio/SMS)
3. Add MQTT integration for IoT sensors
4. Deploy with Docker containers
5. Add comprehensive logging and monitoring

---
*Developed for KSEBL - Kerala State Electricity Board Limited*
