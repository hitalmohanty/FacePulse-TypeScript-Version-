# FacePulse - Face Recognition Attendance System

## Overview

FacePulse is a modern face recognition attendance system designed for educational institutions. The application enables students to mark their attendance through facial recognition technology while providing teachers with comprehensive tools to monitor and manage student attendance. The system features separate interfaces for students and teachers, with real-time attendance tracking, analytics, and a clean, professional design system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The application uses a React-based Single Page Application (SPA) architecture with TypeScript for type safety. The frontend is built with Vite as the build tool and development server, providing fast hot module replacement and optimized builds. The UI follows a component-based architecture using shadcn/ui components built on top of Radix UI primitives and styled with Tailwind CSS.

**State Management**: The application uses React's built-in state management with hooks, along with TanStack Query for server state management and caching. No external state management library like Redux is used, keeping the architecture simple and lightweight.

**Routing**: Uses Wouter for client-side routing, providing a minimal routing solution that's lighter than React Router.

**Styling System**: Implements a comprehensive design system using Tailwind CSS with custom CSS variables for theming. The design follows a green and white color scheme with dark mode support. Custom utility classes handle hover effects and elevation states.

### Component Structure
The application is organized into several key components:
- **FacePulseApp**: Main application orchestrator managing state transitions
- **LoginPage**: Authentication interface with role selection
- **StudentDashboard**: Student-specific interface for viewing attendance stats
- **TeacherDashboard**: Teacher interface for managing classes and viewing analytics
- **FaceScanPage**: Face recognition interface using browser camera APIs
- **AnimatedBackground**: Decorative animated background with floating particles

### Backend Architecture
The backend follows a Node.js/Express.js architecture with TypeScript support. The server is structured with clear separation of concerns:

**Server Setup**: Uses Express.js with middleware for JSON parsing, CORS handling, and request logging. The server includes development-specific Vite integration for hot reloading.

**Storage Layer**: Implements an abstraction layer with interfaces for CRUD operations. Currently uses in-memory storage for development but is designed to easily switch to database persistence.

**API Structure**: RESTful API design with routes prefixed with `/api`. The route registration system allows for easy expansion of endpoints.

### Database Schema
Uses Drizzle ORM with PostgreSQL for database operations. The schema is defined with type safety and includes:
- **Users table**: Stores user authentication data with UUID primary keys
- **Zod validation**: Input validation schemas generated from Drizzle schemas

The database configuration uses environment variables for connection strings and supports migrations through Drizzle Kit.

### Authentication and Security
The authentication system is designed with simplicity in mind:
- Form-based login with username/password
- Role-based access control (student vs teacher)
- Session management preparation (connect-pg-simple for PostgreSQL sessions)
- Input validation using Zod schemas

### Development and Build System
**Development**: Vite development server with TypeScript checking, hot module replacement, and error overlay for better development experience.

**Build Process**: Dual build system - Vite for frontend bundling and esbuild for backend compilation. The build process creates optimized bundles for production deployment.

**TypeScript Configuration**: Comprehensive TypeScript setup with strict typing, module resolution, and path aliases for clean imports.

## External Dependencies

### UI and Styling
- **Radix UI**: Comprehensive set of unstyled, accessible UI primitives
- **Tailwind CSS**: Utility-first CSS framework for rapid UI development
- **Lucide React**: Icon library providing consistent iconography
- **class-variance-authority**: For creating variant-based component APIs
- **Fonts**: Google Fonts integration (Inter and Space Grotesk)

### Development Tools
- **Vite**: Modern build tool and development server
- **TypeScript**: Type safety and enhanced developer experience
- **PostCSS**: CSS processing with Tailwind CSS plugin
- **esbuild**: Fast JavaScript bundler for backend compilation

### Database and ORM
- **Drizzle ORM**: Type-safe ORM for PostgreSQL with migration support
- **@neondatabase/serverless**: Neon database serverless driver
- **Drizzle Zod**: Integration between Drizzle schemas and Zod validation

### State Management and Data Fetching
- **TanStack Query**: Server state management, caching, and synchronization
- **React Hook Form**: Form state management and validation
- **@hookform/resolvers**: Integration between React Hook Form and validation libraries

### Backend Infrastructure
- **Express.js**: Web application framework for Node.js
- **connect-pg-simple**: PostgreSQL session store for Express sessions
- **nanoid**: Unique ID generation for various purposes

### Camera and Media
The application uses native browser APIs for camera access:
- **MediaDevices.getUserMedia()**: For accessing user's camera
- **HTMLVideoElement**: For video stream display
- **Canvas API**: For potential image processing and capture

### Deployment and Environment
- **Replit Integration**: Special configuration for Replit deployment environment
- **Environment Variables**: Database connection and configuration management
- **Cross-platform Support**: Node.js compatibility across different operating systems