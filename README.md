# Job Board Application

A comprehensive job board platform built with React, designed to streamline the job search and recruitment process.

## Features

- User Authentication (Login/Register)
- Role-based access (Job Seekers and Employers)
- Job Listings with Search and Filter
- Application Management
- User Dashboard

## Code Structure

### Backend (`/server`)

- `auth.ts`: Authentication system using Passport.js
- `routes.ts`: API endpoints for jobs and applications
- `storage.ts`: In-memory storage implementation
- `index.ts`: Express server setup

### Frontend (`/client/src`)

#### Pages
- `auth-page.tsx`: Login and registration forms
- `home-page.tsx`: Job listings with search
- `dashboard-page.tsx`: User dashboard (different views for seekers/employers)

#### Components
- `job-card.tsx`: Job listing card with apply functionality
- `search-filters.tsx`: Search and filter controls
- `navbar.tsx`: Navigation with auth status

#### Core
- `hooks/use-auth.tsx`: Authentication context and hooks
- `lib/protected-route.tsx`: Route protection
- `lib/queryClient.ts`: API client setup

### Shared (`/shared`)
- `schema.ts`: Type definitions and validation schemas

## API Endpoints

### Authentication
- POST `/api/register`: Create new user account
- POST `/api/login`: User login
- POST `/api/logout`: User logout
- GET `/api/user`: Get current user

### Jobs
- GET `/api/jobs`: List all jobs
- GET `/api/jobs/:id`: Get specific job
- POST `/api/jobs`: Create new job (employers only)

### Applications
- GET `/api/applications`: List user's applications
- POST `/api/jobs/:id/apply`: Apply to job
- POST `/api/applications/:id/status`: Update application status

## Types

### User
```typescript
interface User {
  id: number;
  username: string;
  role: "seeker" | "employer";
  company: string | null;
  title: string | null;
  bio: string | null;
}
```

### Job
```typescript
interface Job {
  id: number;
  title: string;
  company: string;
  description: string;
  location: string;
  salary: string | null;
  employerId: number;
  createdAt: Date;
}
```

### Application
```typescript
interface Application {
  id: number;
  jobId: number;
  seekerId: number;
  status: "pending" | "accepted" | "rejected";
  coverLetter: string | null;
  createdAt: Date;
}
```

## Usage

1. Register as either a job seeker or employer
2. For job seekers:
   - Browse and search job listings
   - Apply to jobs with optional cover letter
   - Track application status in dashboard
3. For employers:
   - Post new job listings
   - Review and manage applications
   - Accept or reject applications

The application uses React Query for data fetching and caching, Shadcn UI for components, and Tailwind CSS for styling.
