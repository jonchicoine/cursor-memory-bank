# System Patterns

## Architecture Overview
- Next.js application with TypeScript
- App Router architecture
- Component-based structure
- Modern React patterns and hooks

## Key Technical Decisions
1. **Framework Choice**
   - Next.js for server-side rendering and optimal performance
   - TypeScript for type safety and better developer experience

2. **Project Structure**
   ```
   myVcm/
   ├── app/                 # Next.js app directory
   ├── public/             # Static assets
   ├── components/         # Reusable components
   ├── styles/            # Global styles and themes
   └── utils/             # Utility functions
   ```

3. **State Management**
   - React Context for global state
   - Local state with React hooks

4. **Styling Approach**
   - CSS Modules for component-specific styles
   - Global theme configuration
   - Responsive design patterns

## Design Patterns
1. **Component Patterns**
   - Functional components with hooks
   - Props interface definitions
   - Error boundary implementation

2. **Data Flow**
   - Unidirectional data flow
   - Props drilling prevention
   - Context-based state sharing

3. **Performance Patterns**
   - Code splitting
   - Image optimization
   - Lazy loading

## Security Patterns
- Input validation
- XSS prevention
- CSRF protection
- Secure headers

## Testing Strategy
- Unit tests for components
- Integration tests for features
- E2E tests for critical paths

## React Component Pattern Decisions

### Client vs Server Components
- **Server Components**: Default for most pages, especially those that don't need interactivity or browser APIs
- **Client Components**: Used when we need interactivity, state, or browser APIs
  - Must add "use client" directive at the top of the file
  - Currently identified in: varianceWorklist/page.tsx, components/customDataGrid.tsx

### React Hooks Usage
- Hooks should only be used:
  - Inside React functional components (starting with capital letter)
  - Inside custom hooks (starting with "use")
  - Never inside callbacks, conditions, or nested functions
- Common issues identified:
  - useEffect inside callbacks
  - useState/useGridApiContext in non-component functions

### Array Rendering
- Always use a unique 'key' prop for elements in arrays
- Key should be stable, unique, and consistent
- Never use index as key if items can reorder
- Pattern to follow:
  ```tsx
  {items.map((item) => (
    <Component key={item.id} data={item} />
  ))}
  ```

## Next.js Build Configuration
- For development: Allow looser type checking and linting
- For production: Stricter validation by default
- Current temporary solution:
  ```js
  // next.config.mjs
  const nextConfig = {
    eslint: {
      ignoreDuringBuilds: true,
    },
    typescript: {
      ignoreBuildErrors: true,
    },
  };
  ```
- Target solution: Fix all ESLint and TypeScript errors

## Data Grid Components
- CustomDataGrid requires specific props:
  - dataContext: String identifier for the grid context
  - Determines getRowId function behavior
  - Contexts should be added to the getRowId switch statement

## API Services
- Services should provide properly exported functions
- Issue identified: 'GetPayers' is not exported from payersApi

## Environment Configuration
- Development vs Production environments should have separate configurations
- Use .env.development and .env.production files
- Consider moving toggle flags (like ESLint/TypeScript bypassing) to these files 