# AI Challenge Generator - Frontend

A modern React-based frontend application for generating and managing AI-powered coding challenges. Built with Vite, React Router, and Clerk authentication for a seamless user experience.

## 🚀 Features

- **Modern React UI**: Built with React 19 and modern hooks
- **Secure Authentication**: Seamless user authentication via Clerk with protected routes
- **Challenge Generation**: Interactive interface for generating coding challenges at different difficulty levels
- **Real-time Quota Display**: Shows remaining daily challenges and reset information
- **Challenge History**: View and review previously generated challenges
- **Responsive Design**: Clean, accessible interface that works across devices
- **Interactive MCQ Interface**: Click-to-answer multiple choice questions with immediate feedback

## 🛠️ Tech Stack

- **Frontend**: React 19, Vite
- **Routing**: React Router DOM v6
- **Authentication**: Clerk React SDK
- **Styling**: CSS3 with custom properties
- **Build Tool**: Vite with HMR
- **Code Quality**: ESLint with React-specific rules

## 📁 Project Structure

```
frontend/
├── public/                   # Static assets
├── src/
│   ├── App.jsx              # Main application component
│   ├── App.css              # Global styles and CSS variables
│   ├── index.css            # Base styles and resets
│   ├── main.jsx             # Application entry point
│   ├── auth/
│   │   ├── AuthenticationPage.jsx    # Sign-in/Sign-up page
│   │   └── ClerkProviderWithRoutes.jsx # Clerk provider setup
│   ├── challenge/
│   │   ├── ChallengeGenerator.jsx    # Main challenge generation interface
│   │   └── MCQChallenge.jsx          # Multiple choice question component
│   ├── history/
│   │   └── HistoryPanel.jsx          # Challenge history display
│   ├── layout/
│   │   └── Layout.jsx               # App layout with header and navigation
│   └── utils/
│       └── api.js                   # API utilities and request handling
├── index.html               # HTML template
├── package.json            # Dependencies and scripts
├── vite.config.js          # Vite configuration
├── eslint.config.js        # ESLint configuration
└── .env                    # Environment variables (not tracked)
```

## ⚙️ Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
```

## 🔧 Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/asheint/ai-challenge-generator-app.git
   cd ai-challenge-generator-app
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Set up environment variables**

   - Create a `.env` file in the root directory
   - Add your Clerk publishable key as shown above

4. **Run the development server**
   ```bash
   npm run dev
   ```

The application will start on `http://localhost:5173`.

## 🔗 Backend

This frontend works with the AI Challenge Generator backend:

- **Repository**: https://github.com/asheint/ai-challenge-generator-app-backend
- **Backend** handles AI generation, authentication, and data persistence

## 🎯 Key Components

### Authentication Flow

#### [`ClerkProviderWithRoutes`](src/auth/ClerkProviderWithRoutes.jsx)

- Wraps the application with Clerk authentication
- Configures routing for the entire app
- Validates Clerk publishable key

#### [`AuthenticationPage`](src/auth/AuthenticationPage.jsx)

- Handles both sign-in and sign-up flows
- Uses Clerk's built-in components
- Redirects authenticated users

### Challenge Management

#### [`ChallengeGenerator`](src/challenge/ChallengeGenerator.jsx)

- Main interface for generating new challenges
- Difficulty selector (Easy/Medium/Hard)
- Real-time quota display with reset information
- Error handling and loading states
- Integrates with [`useApi`](src/utils/api.js) hook

#### [`MCQChallenge`](src/challenge/MCQChallenge.jsx)

- Interactive multiple choice question display
- Click-to-answer functionality
- Visual feedback for correct/incorrect answers
- Conditional explanation display
- Handles both string and parsed JSON options

### History & Navigation

#### [`HistoryPanel`](src/history/HistoryPanel.jsx)

- Displays user's challenge history
- Loading and error states
- Retry functionality for failed requests
- Uses [`MCQChallenge`](src/challenge/MCQChallenge.jsx) component with explanations shown

#### [`Layout`](src/layout/Layout.jsx)

- App header with navigation
- User button for account management
- Protected route wrapper
- Responsive navigation menu

### API Integration

#### [`useApi`](src/utils/api.js)

- Custom hook for authenticated API requests
- Automatic token injection using Clerk
- Error handling for common scenarios (401, 429)
- Configures requests to backend at `localhost:8000`

## 🎨 Styling System

### CSS Custom Properties

The application uses a comprehensive CSS custom property system defined in [`App.css`](src/App.css):

```css
:root {
  --primary-color: #2563eb;
  --error-color: #dc2626;
  --text-color: #1f2937;
  --bg-color: #f3f4f6;
  --border-color: #e5e7eb;
}
```

### Key Style Features

- **Responsive Design**: Mobile-first approach with flexible layouts
- **Accessible Focus States**: Keyboard navigation support
- **Interactive Feedback**: Hover and click states for all interactive elements
- **Loading States**: Visual feedback during async operations
- **Error Handling**: Styled error messages with retry options

## 🛡️ Protected Routes

The application implements route protection using Clerk:

- **Public Routes**: `/sign-in`, `/sign-up`
- **Protected Routes**: `/` (ChallengeGenerator), `/history` (HistoryPanel)
- **Automatic Redirects**: Unauthenticated users redirected to sign-in

## 📱 Features Overview

### Challenge Generation

- Select difficulty level (Easy, Medium, Hard)
- Real-time quota tracking
- Instant challenge generation
- Visual feedback for selections

### Interactive Questions

- Click-to-answer multiple choice
- Immediate visual feedback
- Detailed explanations after answering
- Support for both new and historical challenges

### User Management

- Seamless sign-in/sign-up flow
- User profile management via Clerk
- Session persistence
- Secure token handling

### History Management

- Complete challenge history
- Review previous questions and answers
- Explanations always visible in history
- Chronological organization

## 🚀 Development Scripts

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Run ESLint
npm run lint

# Preview production build
npm run preview
```

## 📦 Key Dependencies

### Core Dependencies

- **React 19.1.0**: Modern React with latest features
- **React Router DOM 6.30.1**: Client-side routing
- **@clerk/clerk-react 5.32.0**: Authentication integration

### Development Dependencies

- **Vite 6.3.5**: Fast build tool and dev server
- **@vitejs/plugin-react 4.4.1**: React plugin for Vite
- **ESLint 9.25.0**: Code linting and quality
- **eslint-plugin-react-hooks**: React hooks linting rules

## 🔧 Development Configuration

### Vite Configuration

[`vite.config.js`](vite.config.js) includes:

- React plugin for JSX support
- Hot Module Replacement (HMR)
- Fast development server

### ESLint Configuration

[`eslint.config.js`](eslint.config.js) provides:

- React-specific linting rules
- Modern JavaScript standards
- React hooks validation
- Import/export validation

## 🌐 API Integration

The frontend communicates with the backend through standardized endpoints:

- **POST** `/api/generate-challenge` - Generate new challenge
- **GET** `/api/my-history` - Fetch user history
- **GET** `/api/quota` - Check remaining quota

All requests include:

- Automatic authentication via Clerk tokens
- Proper error handling and user feedback
- Loading states for better UX

## 🛠️ Build & Deployment

### Production Build

```bash
npm run build
```

### Build Features

- **Optimized bundles**: Tree-shaking and minification
- **Asset optimization**: Image and font optimization
- **Modern browser targets**: ES2020+ support
- **Source maps**: For debugging in production

## ⭐ Support

If you found this project helpful, please star the repository!

[![GitHub stars](https://img.shields.io/github/stars/asheint/ai-challenge-generator-app.svg?style=social&label=Star)](https://github.com/asheint/ai-challenge-generator-app)

## ☕ Buy Me A Coffee

Support the development of this project:

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-support-yellow.svg)](https://buymeacoffee.com/asheint)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

**Related Projects:**

- [Backend Repository](https://github.com/asheint/ai-challenge-generator-app-backend) - FastAPI backend for this application
