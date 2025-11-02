# Tech Term Explorer

## Overview
Tech Term Explorer is a streamlined web application designed for engineers to efficiently learn and comprehend technical terminology. The application provides comprehensive definitions, pronunciations, examples, and usage information for technical terms through an intuitive, visually polished interface.

**Status**: Production-ready MVP ✅  
**Last Updated**: October 8, 2025

## Features
- **Real-time Search**: Debounced search input with 500ms delay for optimal performance
- **Comprehensive Definitions**: Displays word definitions, parts of speech, phonetics, examples, and synonyms
- **Audio Pronunciation**: Play audio pronunciation for terms when available
- **Beautiful UI**: Professionally designed with shadcn/ui components and Tailwind CSS
- **Dark Mode**: Full theme toggle support with localStorage persistence
- **Responsive Design**: Mobile-first approach that works seamlessly across all devices
- **Loading States**: Elegant skeleton loaders during data fetching
- **Error Handling**: Clear error messages for invalid or not-found terms
- **Empty States**: Helpful prompts when no search has been performed

## Tech Stack

### Frontend
- **React 18** with TypeScript
- **Wouter** for client-side routing
- **TanStack Query (React Query)** for data fetching and caching
- **Tailwind CSS** for styling
- **shadcn/ui** component library
- **Lucide React** for icons

### Backend
- **Express.js** server
- **Node.js 20**
- **Zod** for schema validation
- **Free Dictionary API** (dictionaryapi.dev) for term definitions

## Project Architecture

### Data Model (`shared/schema.ts`)
- Type-safe schemas using Zod for dictionary API responses
- Interfaces for: DictionaryEntry, Meaning, Definition, Phonetic
- Full validation for API responses

### Backend (`server/routes.ts`)
- Proxy endpoint: `GET /api/dictionary/:word`
- Validates search terms
- Handles API errors gracefully (404 for not found, 500 for server errors)
- Parses and validates responses using Zod schemas

### Frontend Structure
```
client/src/
├── components/
│   ├── Header.tsx           # App header with branding and theme toggle
│   ├── SearchBar.tsx        # Search input with debounce and clear button
│   ├── ResultCard.tsx       # Displays word definitions and details
│   ├── LoadingSkeleton.tsx  # Loading placeholder cards
│   ├── EmptyState.tsx       # Initial state before search
│   ├── ErrorState.tsx       # Error display with retry option
│   ├── Footer.tsx           # App footer with attribution
│   └── ThemeToggle.tsx      # Dark/light mode toggle
├── pages/
│   └── Home.tsx             # Main application page
└── App.tsx                  # Root component with routing
```

## Design System
The application follows a Modern Utility Design approach inspired by Linear, Notion, and Material Design.

### Colors (defined in `client/src/index.css`)
- **Primary**: Professional blue (220 70% 50%) for interactive elements
- **Accent**: Purple (260 60% 55%) for phonetics and examples
- **Background**: Pure white (light) / Deep charcoal (dark)
- **Card Surface**: Subtle gray for elevated content

### Typography
- **Font**: Inter (Google Fonts)
- Clear hierarchy with font sizes from text-sm to text-3xl
- Optimized for readability of technical content

### Component Guidelines
- All interactable controls use default shadcn sizing (no manual height/padding overrides)
- Consistent spacing using Tailwind units (2, 4, 6, 8, 12, 16)
- Rounded corners (rounded-md for small, rounded-xl for prominent elements)
- Subtle shadows and smooth transitions

## API Integration
- **External API**: Free Dictionary API (https://dictionaryapi.dev)
- **No Authentication Required**: The dictionary API is freely accessible
- **Rate Limiting**: None for MVP, handled gracefully by the API
- **Response Format**: JSON array of dictionary entries

## Development Workflow

### Running the Application
```bash
npm run dev
```
This starts both the Express backend (port 5000) and Vite frontend development server.

### File Organization
- `client/`: All frontend React code
- `server/`: Express backend and API routes
- `shared/`: TypeScript schemas shared between frontend and backend

## User Experience Flow

1. **Initial Load**: User sees empty state with search suggestions
2. **Search**: User types a term, debounce waits 500ms
3. **Loading**: Skeleton cards appear during API fetch
4. **Results**: Beautiful cards display definitions, examples, and audio
5. **Clear**: X button clears search and returns to empty state
6. **Error Handling**: Clear messages for not-found or API errors
7. **Theme Toggle**: Moon/Sun icon switches between light/dark modes

## Testing
- ✅ End-to-end tests passed for all user flows
- ✅ Search functionality with debounce
- ✅ Clear button resets to empty state
- ✅ Error handling for non-existent terms
- ✅ Theme toggle with persistence
- ✅ Responsive design across breakpoints

## Future Enhancements (Next Phase)
- Search history with local storage
- Favorites/bookmarks functionality
- Advanced filtering by part of speech
- Synonym/antonym exploration with clickable links
- Export definitions to markdown/PDF
- Multiple language support
- Offline mode with cached definitions

## Known Limitations
- Dictionary API only supports English language terms
- Audio pronunciation not available for all words
- No user authentication (stateless application)
- Search limited to single terms (no phrase support)

## Code Quality Standards
- ✅ TypeScript strict mode enabled
- ✅ Zod schema validation for all API responses
- ✅ Component-based architecture with clear separation of concerns
- ✅ Accessibility standards met (ARIA labels, keyboard navigation)
- ✅ Mobile-first responsive design
- ✅ Design guidelines strictly followed
