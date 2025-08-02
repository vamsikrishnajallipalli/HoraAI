# HoraAI Setup Instructions

## Prerequisites
- Python 3.9+
- Node.js 18+
- PostgreSQL 14+
- Redis 6+
- Docker & Docker Compose (optional but recommended)

## Quick Start with Docker

1. **Clone the repository**
```bash
git clone https://github.com/vamsikrishnajallipalli/HoraAI.git
cd HoraAI
```

2. **Create environment file**
```bash
cp .env.example .env
# Edit .env with your configuration
```

3. **Start all services with Docker**
```bash
cd docker
docker-compose up -d
```

This will start:
- PostgreSQL database
- Redis cache
- Backend API (http://localhost:8000)
- Frontend web app (http://localhost:3000)
- Celery workers for background tasks

## Manual Setup

### Backend Setup

1. **Navigate to backend directory**
```bash
cd backend
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Set up environment variables**
```bash
cp .env.example .env
# Edit .env file with your configuration
```

5. **Set up database**
```bash
# Make sure PostgreSQL is running
# Create database
createdb horaai_db

# Run migrations
alembic upgrade head
```

6. **Start the backend server**
```bash
uvicorn main:app --reload
```

The API will be available at http://localhost:8000
API documentation at http://localhost:8000/docs

### Frontend Setup

1. **Navigate to frontend directory**
```bash
cd frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Set up environment variables**
```bash
cp .env.example .env.local
# Edit .env.local with your configuration
```

4. **Start development server**
```bash
npm run dev
```

The web app will be available at http://localhost:3000

### Mobile App Setup

1. **Navigate to mobile directory**
```bash
cd mobile
```

2. **Install dependencies**
```bash
npm install
```

3. **Start Expo development server**
```bash
npm start
```

4. **Run on devices**
- Press `a` for Android emulator
- Press `i` for iOS simulator
- Scan QR code with Expo Go app on physical device

### Desktop App Setup

1. **Navigate to desktop directory**
```bash
cd desktop
```

2. **Install dependencies**
```bash
npm install
```

3. **Start development**
```bash
npm run dev
```

4. **Build for production**
```bash
npm run build
npm run dist
```

## AI Model Setup

1. **Navigate to ai-models directory**
```bash
cd ai-models
```

2. **Install AI dependencies**
```bash
pip install -r requirements.txt
```

3. **Download ephemeris data**
```bash
python download_ephemeris.py
```

4. **Train models (optional)**
```bash
python train_models.py
```

## Testing

### Backend Tests
```bash
cd backend
pytest
```

### Frontend Tests
```bash
cd frontend
npm test
```

### E2E Tests
```bash
cd e2e
npm test
```

## Deployment

### Using Docker
```bash
docker-compose -f docker-compose.prod.yml up -d
```

### Manual Deployment
See `docs/deployment.md` for detailed deployment instructions.

## Common Issues

1. **Database connection error**
   - Ensure PostgreSQL is running
   - Check DATABASE_URL in .env

2. **Redis connection error**
   - Ensure Redis is running
   - Check REDIS_URL in .env

3. **Port already in use**
   - Change ports in docker-compose.yml or .env files

4. **Module not found errors**
   - Ensure virtual environment is activated
   - Reinstall dependencies

## Next Steps

1. **Configure AI models**
   - Train custom models with your data
   - Fine-tune predictions

2. **Set up monitoring**
   - Configure Sentry for error tracking
   - Set up Prometheus + Grafana

3. **Enable premium features**
   - Configure Stripe for payments
   - Set up email service

4. **Customize UI/UX**
   - Modify themes in frontend
   - Add custom features

For more detailed documentation, see the `docs/` directory.