# Angular Frontend Integration with .NET Backend

## Configuration
- The Angular app uses `environment.ts` to point to the .NET backend URL
- Default development URL: `http://localhost:5000` (ASP.NET Core default)
- Production URL should be updated in `environment.prod.ts`

## Authentication Flow
1. **Local Signup/Login**: Angular sends credentials to `/auth/local/signup` or `/auth/local/login`
2. **JWT Response**: Backend returns `{ access_token, token_type }`
3. **Token Storage**: `TokenStorageService` stores JWT in `localStorage`
4. **HTTP Interceptor**: `AuthInterceptor` automatically attaches `Authorization: Bearer <token>` to subsequent requests
5. **Protected Routes**: Calls to `/users/me` or other protected endpoints include the JWT

## SSO Flow (Google/Azure)
1. Angular redirects to `/auth/google` or `/auth/azure` on the backend
2. Backend handles OAuth flow and issues JWT
3. Backend redirects back to frontend with `?token=<jwt>` query parameter
4. `LoginComponent` extracts token and stores it via `TokenStorageService`

## Environment Variables
No frontend environment variables needed for basic operation. For production:
- Update `apiBaseUrl` in `environment.prod.ts`
- Ensure CORS allows your production domain

## Running Together
1. Start .NET backend (default port 5000)
2. Start Angular dev server (port 4200)
3. Navigate to `http://localhost:4200`
4. The frontend will proxy API calls to the backend

## Docker/Deployment Notes
- In containerized environments, ensure the backend URL is reachable from the frontend container
- Use environment variables or configuration files to set the correct API base URL
