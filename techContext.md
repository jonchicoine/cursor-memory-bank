# Technical Context
Last Updated: [Current Date]
## Technology Stack
- **Framework**: Next.js
- **Language**: TypeScript
- **Styling**: CSS Modules
- **Package Manager**: npm
- **Version Control**: Git
- **Development Environment**: VS Code/Cursor

## Development Setup
1. **Prerequisites**
   - Node.js (Latest LTS version)
   - npm (Latest version)
   - Git
   - VS Code/Cursor IDE

2. **Environment Variables**
   ```
   # .env.local
   NEXT_PUBLIC_API_URL=
   ```

3. **Development Tools**
   - ESLint for code linting
   - Prettier for code formatting
   - TypeScript for type checking

## Build & Deployment
1. **Build Process**
   ```bash
   npm run build
   ```

2. **Development Server**
   ```bash
   npm run dev
   ```

3. **Production Server**
   ```bash
   npm start
   ```

## Dependencies
Key packages:
- next
- react
- react-dom
- typescript
- @types/react
- @types/node
- eslint
- prettier

## Development Workflow
1. Feature branches from main
2. Pull request reviews
3. Automated testing
4. Deployment to staging/production

## Performance Considerations
- Image optimization
- Code splitting
- Bundle size monitoring
- Lighthouse metrics 