# Role-Based Auth for Google Login - Implementation Plan

## Completed:
- Analysis & Planning
- Read Program.cs: Has Viewer/Admin policies; missing AddGoogle auth (uses session but no provider config).
- Read appsettings.json: Has Google ClientId/Secret.
- Read login.component.ts: Already handles ?token= query perfectly (stores, clears param).

## Pending Steps:
1. **Edit Program.cs**: AddGoogle auth config using appsettings.
2. **Update TODO-auth-fix.md & TODO-fix-auth.md**: Mark relevant items resolved.
3. **Test**: dotnet build/run backend, ng serve frontend, end-to-end Google login + asset reads/CRUD (after manual role=Admin).
4. **(Optional)** Expand UsersController for role updates.

**Next: Edit Program.cs**


