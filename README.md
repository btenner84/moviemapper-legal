# 🎬 MovieMapper - Connect Movies Through Actors

A React Native puzzle game where players connect two movies by navigating through shared actors. Think "Six Degrees of Kevin Bacon" but for movies!

## 🎯 Game Concept

**Objective**: Connect a start movie to an end movie using the shortest path through shared actors.

**Example**: 
- Start: "Pulp Fiction" → John Travolta → "Grease" → Olivia Newton-John → "Xanadu" → End Movie
- Each step must be a valid actor who appeared in both movies

## 🏗️ Architecture Overview

### Frontend (React Native + Expo)
- **Platform**: iOS/Android mobile app
- **Framework**: React Native with Expo SDK 53
- **Navigation**: React Navigation stack
- **State Management**: React hooks + local state
- **Authentication**: Firebase Auth with Google Sign-In
- **Deployment**: EAS Build → TestFlight → App Store

### Backend (Python FastAPI)
- **API**: FastAPI REST service deployed on Railway
- **Database**: PostgreSQL with movie/actor relationship data
- **Data Source**: TMDB (The Movie Database) API
- **Graph Engine**: Custom shortest-path algorithm for movie connections
- **Hosting**: Railway production environment

### Data Pipeline
- **S3 Storage**: Compressed movie/actor datasets and precomputed graphs
- **Local Processing**: Movie curation scripts for balanced gameplay
- **Railway Database**: 19,607+ curated movies with rich metadata

## 🎮 Core Features

### Game Modes
1. **Easy Mode** (77 movies) - Mainstream hits, 2-step difficulty
2. **Normal Mode** (382 movies) - Diverse collection, 3-step difficulty  
3. **Impossible Mode** (4,786 movies) - Comprehensive database, 5-step difficulty

### Genre Filtering System
- **10 Categories**: Action/Adventure, Comedy, Drama, Horror/Thriller, etc.
- **Primary Genre Focus**: Movies limited to 1-2 main genres for clarity
- **Persistent Filters**: RANDOMIZE button maintains selected genres
- **Smart Filtering**: Works within existing difficulty modes

### User Experience
- **Beautiful UI**: Dark theme with gradient backgrounds
- **Movie Posters**: High-quality TMDB poster integration
- **Smart Search**: Fuzzy matching for actor/movie names
- **Hint System**: Progressive hints for stuck players
- **Leaderboard**: Track completion times and streaks

## 📊 Technical Specifications

### Mobile App (`mobile-app/`)
```
├── src/
│   ├── components/     # Reusable UI components
│   ├── screens/        # Main app screens
│   ├── services/       # API client and Firebase
│   └── types/          # TypeScript definitions
├── assets/             # Images and icons
└── app.json           # Expo configuration
```

**Key Technologies**:
- React Native 0.74+
- Expo SDK 53
- TypeScript
- Firebase Authentication
- Axios for API calls

### Backend Services (`services/`)

#### Graph Engine (`services/graph-engine/`)
- **FastAPI** REST API
- **PostgreSQL** database with movie relationships
- **S3 Integration** for large datasets
- **Smart Caching** for performance optimization

#### API Gateway (`services/api-gateway/`)
- Request routing and load balancing
- Rate limiting and authentication middleware

#### Background Jobs (`services/jobs/`)
- Metadata downloading from TMDB
- Graph building and optimization
- Actor index generation

### Database Schema (`db_structure.md`)

**Core Tables**:
- `movie_metadata` - Movie details, posters, ratings
- `person_metadata` - Actor information and popularity
- `movie_person_connections` - Actor-movie relationships
- `curated_movie_collections` - Hand-picked movie sets
- `collection_movies` - Movies within each collection

## 🚀 Deployment Status

### Production Environment
- **Backend**: Railway (https://supportive-warmth-production.up.railway.app)
- **Database**: Railway PostgreSQL with 19,607 curated movies
- **Mobile**: TestFlight (ready for App Store submission)

### Current Build
- **Version**: 1.0.0 (build 2)
- **Status**: ✅ Core functionality working perfectly
- **TestFlight**: Available for testing
- **App Store**: Ready for submission

## 🎯 Game Generation Algorithm

### Collection-Based Approach
1. **Select Collection** based on difficulty mode
2. **Apply Genre Filters** if specified by user
3. **Random Movie Selection** from filtered set
4. **Path Validation** ensure connection exists
5. **Metadata Enrichment** add posters, ratings, descriptions

### Quality Assurance
- **Curated Collections**: Hand-picked movies for balanced gameplay
- **Connection Validation**: All game pairs guaranteed solvable
- **Metadata Coverage**: 97%+ movies have complete poster/title data
- **Performance**: Sub-3 second game generation

## 📱 Current Features Status

### ✅ Working Perfectly
- **Core Game Logic** - Movie connection gameplay
- **All Game Modes** - Easy/Normal/Impossible working
- **Genre Filtering** - 10 categories with persistence
- **RANDOMIZE Function** - Maintains user preferences
- **Movie Metadata** - Posters, titles, ratings, descriptions
- **Search System** - Actor and movie lookup
- **Network Connectivity** - API calls working in production builds

### 🔧 Known Issues
- **Google Sign-In** - Redirect URI needs configuration for production builds
- **Email Auth** - Working as fallback authentication method

### 🎯 Ready for App Store
- Core gameplay experience is polished and functional
- All major features implemented and tested
- Network issues resolved for production builds
- Beautiful UI with proper loading states and error handling

## 🔧 Development Setup

### Prerequisites
- Node.js 18+
- Python 3.9+
- PostgreSQL 14+
- Expo CLI
- Apple Developer Account (for iOS)

### Local Development
```bash
# Backend setup
cd services/graph-engine
pip install -r requirements.txt
python main.py

# Mobile app setup  
cd mobile-app
npm install
npx expo start
```

### Environment Variables
```bash
# Backend (.env)
DATABASE_URL=postgresql://...
TMDB_API_KEY=your_tmdb_key
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret

# Mobile (app.json)
apiUrl=https://your-backend-url
```

## 📈 Data Statistics

### Movie Database
- **Total Movies**: 19,607 curated films
- **Metadata Coverage**: 97.2% complete
- **Genre Coverage**: 1-2 primary genres per movie
- **Release Years**: 1920s to 2024

### Collections
- **Easy Mode**: 77 mainstream movies
- **Normal Mode**: 382 diverse films  
- **Impossible Mode**: 4,786 comprehensive collection
- **Total Connections**: 500,000+ actor-movie relationships

## 🎮 User Journey

1. **Launch App** - Beautiful onboarding experience
2. **Select Mode** - Choose difficulty and optional genre filters
3. **Get Game** - Receive two movies to connect
4. **Play Game** - Search actors, build connection path
5. **Get Hints** - Progressive assistance if stuck
6. **Complete** - Track time and submit to leaderboard
7. **Randomize** - Get new game in same mode/genre

## 🚀 Next Steps

### Immediate (Pre-App Store)
1. **Fix Google Sign-In** - Add production redirect URI to Google Console
2. **Final Testing** - Comprehensive TestFlight validation
3. **App Store Submission** - Screenshots, description, submission

### Future Enhancements
- **Multiplayer Mode** - Head-to-head competitions
- **Daily Challenges** - Curated daily puzzles
- **Achievement System** - Unlock rewards for milestones
- **Social Features** - Share results, challenge friends

## 📞 Support & Contact

- **Developer**: Ben Tenner
- **Email**: bentenner84@gmail.com
- **TestFlight**: Available for beta testing
- **Repository**: Private development repository

---

**MovieMapper** - Where cinema knowledge meets puzzle-solving fun! 🎬✨ 

# MovieMapper Legal Documents

This repository hosts the official legal documents for the MovieMapper puzzle game.

## 📋 Documents Available

- **Privacy Policy** (`privacy-policy.html`) - How we collect, use, and protect user data
- **Terms of Service** (`terms-of-service.html`) - Rules and conditions for using MovieMapper

## 🌐 Live Site

These documents are hosted via GitHub Pages at: `https://[username].github.io/moviemapper-legal/`

## 📱 About MovieMapper

MovieMapper is a puzzle game where players connect movies through actors who appeared in both films. Challenge yourself to find the shortest path between any two movies using our database of 441,000+ movies and 187,000+ actors!

## 🔗 Links

- **Privacy Policy**: [privacy-policy.html](privacy-policy.html)
- **Terms of Service**: [terms-of-service.html](terms-of-service.html)

## ⚖️ Legal Notice

These documents are effective as of July 4, 2025 and govern the use of the MovieMapper application.

---

*Last updated: July 4, 2025* 