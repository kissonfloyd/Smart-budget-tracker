# Smart Budget Tracker - Replit Configuration

## Overview

Smart Budget Tracker is a full-stack web application for managing personal budgets and tracking expenses. The application features a React frontend with TypeScript, an Express.js backend, and uses Drizzle ORM with PostgreSQL for data persistence. The project is structured as a monorepo with shared TypeScript schemas and uses modern UI components from shadcn/ui.

## User Preferences

Preferred communication style: Simple, everyday language.
Currency: Nepali Rupees (रू)
Language: Nepali localization for UI elements and categories
Color theme: Coral/orange primary theme with mauve secondary colors throughout the application

## System Architecture

### Web App (PWA) Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state
- **Form Handling**: React Hook Form with Zod validation
- **Routing**: Wouter for lightweight client-side routing

### Native App (React Native) Architecture  
- **Framework**: React Native 0.73.4 with TypeScript
- **Navigation**: React Navigation 6 with bottom tabs and stack navigation
- **State Management**: React Context API with AsyncStorage persistence
- **UI Components**: Native components with Material Design icons
- **Data Storage**: AsyncStorage for offline-first data persistence
- **Charts**: react-native-chart-kit for analytics visualization
- **Platform**: Android and iOS native compilation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework (optional for development)
- **Language**: TypeScript with ES modules
- **Data Layer**: Browser localStorage (web) / AsyncStorage (native) for offline persistence
- **Validation**: Zod schemas shared between client and server
- **Storage**: LocalStorageManager for client-side data persistence

### Database Schema
- **budgets**: Stores budget information with account name and total amount
- **expenses**: Tracks individual expenses linked to budgets with categories and dates
- Uses PostgreSQL-compatible schema with UUID primary keys

## Key Components

### Shared Components
- **Schema Definition**: Centralized Zod schemas in `/shared/schema.ts`
- **Type Safety**: Shared TypeScript types for Budget and Expense entities
- **Validation**: Client and server use identical validation rules

### Frontend Components
- **BudgetOverview**: Manages budget creation and displays budget progress
- **AddExpenseForm**: Form for adding new expenses with category selection and receipt photo upload
- **ExpenseList**: Displays and manages existing expenses with delete functionality and receipt viewing
- **ReceiptViewer**: Full-screen modal for viewing receipt photos with zoom capability
- **QuickStats**: Shows budget statistics and spending analytics
- **ExpenseAnalytics**: Comprehensive analytics with charts, insights, and spending trends
- **BannerAd**: Rotating banner advertisements with local business content
- **InterstitialAd**: Full-screen premium upgrade ads after 5 expenses
- **RemoveAdsSettings**: Premium upgrade interface with pricing plans
- **Welcome**: Onboarding screen with Nepali message

### Backend Components
- **Routes**: RESTful endpoints for budgets and expenses CRUD operations
- **Storage Interface**: Abstracted storage layer for easy database switching
- **Error Handling**: Centralized error handling with appropriate HTTP status codes

## Data Flow

1. **Client Requests**: React components use TanStack Query for data management
2. **Local Storage**: LocalStorageManager handles all data operations in browser
3. **Data Persistence**: All data stored in browser localStorage (no server required)
4. **Client Updates**: Query cache invalidation triggers UI updates
5. **Offline First**: App works completely offline with local data storage

The application follows an offline-first pattern with React Query managing local state synchronization and browser localStorage for persistence.

## External Dependencies

### Frontend Dependencies
- **UI Components**: Extensive Radix UI component library
- **Styling**: Tailwind CSS with PostCSS
- **Date Handling**: date-fns for date manipulation
- **Icons**: Lucide React for consistent iconography
- **Charts**: Recharts for data visualization and analytics
- **Analytics**: Custom expense analytics with spending insights

### Backend Dependencies
- **Database**: @neondatabase/serverless for PostgreSQL connection
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Session**: connect-pg-simple for PostgreSQL session storage
- **Validation**: Zod and drizzle-zod for schema validation

### Development Dependencies
- **Build Tools**: Vite, esbuild for production builds
- **TypeScript**: Full TypeScript setup with strict mode
- **Replit Integration**: Cartographer and runtime error overlay plugins

## Deployment Strategy

### Automatic Build System (GitHub Actions)
- **Build Triggers**: Manual workflow dispatch, code pushes, and release tags
- **Build Outputs**: Production-ready APK and AAB files
- **Distribution**: GitHub Artifacts and Releases for easy download
- **Build Time**: 5-10 minutes with full automation

### Native App Deployment
- **Android**: React Native compiled to native APK/AAB for Google Play Store
- **Automatic Signing**: Auto-generated keystores for production builds
- **Build Artifacts**: APK for testing, AAB for Play Store submission
- **Development**: Metro bundler with hot reloading
- **Production**: GitHub Actions with Gradle build system

### Google Play Store Deployment
- **Package Name**: com.smartbudgettracker
- **Target SDK**: 34 (Android 14)
- **Min SDK**: 21 (Android 5.0)
- **App Category**: Finance
- **Content Rating**: Everyone
- **Monetization**: Freemium with Premium subscription (रू 499/month)

### Data Storage
- **Native**: AsyncStorage for device-local data persistence
- **Offline-First**: Complete functionality without internet connection
- **Receipt Photos**: Base64 encoding for offline storage
- **Data Privacy**: All data stored locally on device

### App Store Readiness
- **Google Play Store**: Automatic APK/AAB generation ready for immediate submission
- **Build System**: Complete CI/CD pipeline with GitHub Actions
- **Signing**: Production-ready signed builds
- **Testing**: APK files for device testing before store submission

The application features complete build automation with GitHub Actions, enabling one-click generation of production-ready files for immediate Google Play Store deployment.