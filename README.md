# HydroSense 🌊

A comprehensive water quality monitoring mobile application built with React Native and Expo. HydroSense enables users to track and analyze water quality parameters including pH levels, turbidity, and TDS (Total Dissolved Solids) to protect and monitor water resources.

## 🌟 Features

### Core Functionality

- **Water Quality Monitoring**: Track essential water quality parameters
  - pH Levels (6.5-8.5 optimal range)
  - Turbidity measurement (NTU units)
  - TDS (Total Dissolved Solids) tracking (0-500 ppm optimal range)

- **Experiment Management**: Create, track, and analyze water quality experiments
  - Start new detection experiments with custom titles and descriptions
  - Real-time sensor data collection and analysis
  - Historical experiment tracking and review
  - Detailed experiment results with status indicators

- **User Authentication**: Secure user management with Supabase
  - Email/password authentication
  - User session management
  - Profile management

### User Interface

- **Modern Design**: Clean, intuitive interface with Tailwind CSS styling
- **Responsive Layout**: Optimized for mobile devices with tablet support
- **Dark/Light Mode**: Automatic theme switching based on system preferences
- **Interactive Components**: Smooth animations and haptic feedback

## 🏗️ Technical Architecture

### Frontend Stack

- **React Native**: Cross-platform mobile development
- **Expo**: Development platform and build tools
- **TypeScript**: Type-safe development
- **Expo Router**: File-based navigation system
- **Tailwind CSS**: Utility-first styling with NativeWind
- **React Native Reanimated**: Smooth animations

### Backend & Database

- **Supabase**: Backend-as-a-Service for authentication and database
- **PostgreSQL**: Database for storing experiment data
- **REST API**: Custom API endpoints for experiment management

### Key Dependencies

- `@supabase/supabase-js`: Database and authentication
- `expo-router`: Navigation system
- `react-native-reanimated`: Animations
- `nativewind`: Tailwind CSS for React Native
- `lucide-react-native`: Icon library
- `@expo/vector-icons`: Additional icon support

## 📱 App Structure

### Navigation

```
app/
├── (auth)/           # Authentication screens
│   ├── _layout.tsx   # Auth layout
│   └── index.tsx     # Login/Signup screen
├── (tabs)/           # Main app screens
│   ├── _layout.tsx   # Tab navigation
│   ├── index.tsx     # Home/Dashboard
│   ├── history.tsx   # Experiment history
│   └── profile.tsx   # User profile
└── experiments/      # Experiment detail screens
    └── [id]/
        └── index.tsx # Individual experiment view
```

### Key Components

- `StartDetection`: Modal for creating new experiments
- `AuthForm`: User authentication forms
- `UI Components`: Reusable UI elements (buttons, inputs, dialogs)

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- Expo CLI
- iOS Simulator or Android Emulator (for development)
- Supabase account for backend services

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd hydrosense
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env` file in the root directory:

   ```env
   EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
   EXPO_PUBLIC_SUPABASE_KEY=your_supabase_anon_key
   EXPO_PUBLIC_API_URL=your_api_url
   ```

4. **Start the development server**

   ```bash
   npm start
   ```

5. **Run on device/simulator**

   ```bash
   # iOS
   npm run ios

   # Android
   npm run android

   # Web
   npm run web
   ```

## 📊 Water Quality Parameters

### pH Levels

- **Optimal Range**: 6.5 - 8.5
- **Good Range**: 6.0 - 9.0
- **Critical**: Outside 6.0 - 9.0

### Turbidity

- **Excellent**: < 1 NTU
- **Good**: < 5 NTU
- **Normal**: 5+ NTU

### TDS (Total Dissolved Solids)

- **Excellent**: < 300 ppm
- **Good**: 300 - 500 ppm
- **Fair**: 500 - 900 ppm
- **Poor**: > 900 ppm

## 🔧 Development

### Available Scripts

- `npm start`: Start Expo development server
- `npm run android`: Run on Android device/emulator
- `npm run ios`: Run on iOS device/simulator
- `npm run web`: Run in web browser
- `npm run lint`: Run ESLint

### Code Structure

- **Components**: Reusable UI components in `/components`
- **Screens**: App screens in `/app`
- **Utils**: Utility functions and configurations
- **Hooks**: Custom React hooks for shared logic

## 🌐 API Integration

The app integrates with a custom REST API for experiment management:

### Endpoints

- `POST /experiments`: Create new experiment
- `GET /experiments?userId={id}`: Fetch user experiments
- `GET /experiments/{id}`: Get specific experiment
- `PATCH /experiments/{id}`: Update experiment data

### Data Flow

1. User creates experiment → API call to create experiment
2. Sensor data collection → Real-time data updates
3. Analysis completion → Results stored and displayed

## 🎨 Design System

### Color Palette

- **Primary**: #0279C2 (Blue)
- **Success**: #10B981 (Green)
- **Warning**: #F59E0B (Orange)
- **Error**: #EF4444 (Red)
- **Neutral**: Gray scale variations

### Typography

- **Headings**: Bold, large text for titles
- **Body**: Regular weight for content
- **Captions**: Small text for metadata

## 📱 Platform Support

- **iOS**: Full support with native features
- **Android**: Full support with Material Design
- **Web**: Progressive Web App capabilities

## 🔒 Security

- **Authentication**: Secure user authentication with Supabase
- **Data Protection**: User data encrypted in transit and at rest
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
- Contact the development team
- Check the documentation for common solutions

---

**HydroSense** - Protecting water resources through technology 🌊✨
