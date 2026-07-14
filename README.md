# SmartMeter ⚡

An IoT-based smart energy metering system built with an ESP32 microcontroller and a React Native (Expo) mobile app. SmartMeter measures real-time voltage, current, and power from a 220V AC supply, and pushes the data to the cloud for live monitoring and energy analytics.

Developed for NANENG 211 (Power Machines), Zewail City of Science and Technology.

## 🌟 Features

### Core Functionality

- **Real-Time Power Monitoring**: Track essential electrical parameters
  - RMS Voltage (via ZMPT101B voltage sensor)
  - RMS Current (via SCT-013 current transformer)
  - Real power, apparent power, and power factor
  - Cumulative energy consumption (kWh)

- **Firmware-Level Signal Processing**: Accurate measurement from noisy AC signals
  - Current calibration and averaging logic to reduce sensor noise
  - Noise-filter thresholds tuned to reject false readings
  - Real-time RMS calculation using EmonLib

- **Experiment/Session Tracking**: Log and review energy usage over time
  - Live dashboard with real-time sync
  - Historical usage tracking and review
  - Interactive energy analytics charts

- **User Authentication**: Secure user management with Supabase
  - Email/password authentication
  - User session management
  - Profile management

### User Interface

- **Modern Design**: Clean, intuitive mobile interface
- **Responsive Layout**: Optimized for mobile devices with tablet support
- **Live Dashboard**: Real-time voltage/current/power widgets
- **Interactive Charts**: Energy consumption trends over time

## 🏗️ Technical Architecture

### Hardware

- **ESP32**: Wi-Fi-enabled microcontroller running the metering firmware
- **ZMPT101B**: Voltage sensor for measuring the 220V AC line voltage
- **SCT-013**: Non-invasive current transformer (CT) clamp for current sensing
- **220V AC Supply**: Target measurement circuit

### Firmware Stack

- **C++ (Arduino Framework)**: Core firmware logic
- **EmonLib**: RMS voltage/current and power calculation
- **ArduinoJson**: Structuring sensor payloads for API requests
- **REST API (HTTP)**: Pushing readings to the Supabase backend

### Frontend Stack (Mobile App)

- **React Native**: Cross-platform mobile development
- **Expo**: Development platform and build tools
- **Supabase Client (JS)**: Real-time data sync and auth

### Backend & Database

- **Supabase**: Backend-as-a-Service for authentication and database
- **PostgreSQL**: Database for storing readings and session/energy history
- **REST API**: Endpoints for pushing and retrieving metering data

### Key Dependencies

**Firmware (Arduino/ESP32):**
- `EmonLib`: Voltage/current RMS and power calculation
- `ArduinoJson`: JSON payload construction
- `WiFi.h` / `HTTPClient.h`: Connectivity and REST requests

**Mobile App:**
- `@supabase/supabase-js`: Database and authentication
- Chart library for energy analytics visualization

## 📱 App Structure

```
smart-meter/
├── firmware/
│   └── smart_meter.ino     # ESP32 firmware (EmonLib, calibration, REST push)
├── app/
│   ├── (auth)/             # Authentication screens
│   │   └── index.tsx       # Login/Signup screen
│   ├── (tabs)/             # Main app screens
│   │   ├── index.tsx       # Live dashboard (voltage/current/power)
│   │   ├── history.tsx     # Historical energy usage
│   │   └── profile.tsx     # User profile
│   └── readings/
│       └── [id]/
│           └── index.tsx   # Individual reading/session detail view
```

### Key Components

- `LiveDashboard`: Real-time display of voltage, current, power, and power factor
- `AuthForm`: User authentication forms
- `EnergyChart`: Historical energy consumption visualization

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- Expo CLI
- Arduino IDE or PlatformIO (for ESP32 firmware)
- ESP32 board, ZMPT101B voltage sensor, SCT-013 CT sensor
- iOS Simulator or Android Emulator (for development)
- Supabase account for backend services

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd smart-meter
   ```

2. **Flash the firmware**

   - Open `firmware/smart_meter.ino` in the Arduino IDE
   - Install the `EmonLib` and `ArduinoJson` libraries
   - Set your Wi-Fi credentials and Supabase REST endpoint in the sketch
   - Select your ESP32 board and upload

3. **Install app dependencies**

   ```bash
   cd app
   npm install
   ```

4. **Environment Setup**
   Create a `.env` file in the `app` root directory:

   ```env
   EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
   EXPO_PUBLIC_SUPABASE_KEY=your_supabase_anon_key
   ```

5. **Start the development server**

   ```bash
   npm start
   ```

6. **Run on device/simulator**

   ```bash
   # iOS
   npm run ios

   # Android
   npm run android

   # Web
   npm run web
   ```

## 📊 Measured Parameters

### Voltage (ZMPT101B)

- **Nominal**: 220V AC RMS
- Calibrated against a reference multimeter reading

### Current (SCT-013)

- Calibrated using known reference loads
- Averaging applied over multiple cycles to reduce sensor noise

### Power & Energy

- **Real Power (W)**: Calculated from instantaneous voltage × current samples
- **Power Factor**: Derived from real vs. apparent power
- **Cumulative Energy (kWh)**: Integrated over time for usage tracking

## 🔧 Development

### Available Scripts (App)

- `npm start`: Start Expo development server
- `npm run android`: Run on Android device/emulator
- `npm run ios`: Run on iOS device/simulator
- `npm run web`: Run in web browser
- `npm run lint`: Run ESLint

### Code Structure

- **Firmware**: Sensor reading, calibration, and RMS/power calculation logic
- **Components**: Reusable UI components in `/components`
- **Screens**: App screens in `/app`
- **Utils**: Utility functions and configurations

## 🌐 API Integration

The firmware pushes readings to a Supabase REST endpoint:

### Endpoints

- `POST /readings`: Push a new voltage/current/power reading
- `GET /readings?deviceId={id}`: Fetch historical readings for a device
- `GET /readings/{id}`: Get a specific reading
- `GET /readings/summary?deviceId={id}`: Get cumulative energy summary

### Data Flow

1. ESP32 samples voltage/current via EmonLib → computes RMS, power, power factor
2. Firmware pushes reading as JSON → REST API → Supabase
3. Mobile app subscribes to live updates → dashboard and charts refresh in real time

## 📱 Platform Support

- **iOS**: Full support
- **Android**: Full support with Material Design
- **Web**: Basic support via Expo web build

## 🔒 Security

- **Authentication**: Secure user authentication with Supabase
- **Data Protection**: Data encrypted in transit
- **Session Management**: Automatic token refresh and secure storage

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For support and questions:

- Create an issue in the repository
- Check the documentation for common solutions

---

**SmartMeter** — Real-time power monitoring, powered by ESP32 ⚡📊
