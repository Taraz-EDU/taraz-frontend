# Constrack - Next.js TypeScript Project Rules

## Project Overview
This is a Next.js 15 project with TypeScript, Tailwind CSS, and modern React patterns. The project follows the App Router architecture and implements comprehensive development standards.

## Core Technologies
- **Framework**: Next.js 15 with App Router
- **Language**: TypeScript with strict mode
- **Styling**: Tailwind CSS with CSS root variables
- **State Management**: Zustand for global state, React Query for server state
- **Forms**: react-hook-form with Zod validation
- **Testing**: Jest, React Testing Library, Playwright
- **Deployment**: Fly.io with Docker

## Development Standards

### TypeScript Best Practices
- Use strict TypeScript configuration
- Prefer explicit types over `any` - use `unknown` when type is truly unknown
- Define interfaces for all data structures, especially API responses
- Use generic types for reusable components and functions
- Implement proper error handling with Result/Either patterns
- Use discriminated unions for different states

### Next.js App Router Patterns
- Use Server Components by default, Client Components only when necessary
- Implement proper data fetching with `fetch` and caching strategies
- Use `generateMetadata` for dynamic SEO
- Implement proper error boundaries and loading states
- Use middleware for authentication and request modification
- Optimize images with `next/image` and implement proper lazy loading

### React Component Standards
- Use functional components with hooks
- Keep components under 200 lines
- Extract complex logic into custom hooks
- Use `React.memo` for expensive components
- Implement proper `useCallback` and `useMemo` usage
- Use `React.lazy` for code splitting

### Styling Guidelines
- Define colors using CSS root variables in `index.css` (preferred over tailwind.config.js)
- Use utility-first approach with Tailwind CSS
- Implement responsive design with mobile-first approach
- Support dark mode with proper CSS variables
- Use consistent spacing and sizing scales
- Implement proper focus indicators and accessibility

### State Management Strategy
- Use local state for component-specific data
- Use React Query for all server state management
- Use Zustand for global app state
- Use React Context for theme, language, and configuration
- Implement proper state persistence with localStorage

### Form Handling
- Use react-hook-form for all forms in the project
- Implement Zod validation for both client and server
- Provide proper error handling and user feedback
- Use proper accessibility attributes

### Testing Standards
- Write tests that test behavior, not implementation
- Use React Testing Library for component testing
- Implement proper accessibility testing with jest-axe
- Use MSW for API mocking
- Test user workflows and interactions
- Maintain high test coverage with meaningful tests

### Performance Optimization
- Use dynamic imports for code splitting
- Implement proper caching strategies
- Use virtualization for large lists
- Optimize bundle size with tree shaking
- Implement proper loading states
- Monitor Core Web Vitals

### Security Best Practices
- Validate all inputs on both client and server
- Implement proper authentication and authorization
- Use HTTPS and security headers
- Implement rate limiting for API endpoints
- Sanitize user-generated content
- Use proper environment variable management

### Accessibility Standards
- Use semantic HTML elements
- Implement proper ARIA labels and roles
- Ensure keyboard navigation works correctly
- Maintain proper color contrast ratios
- Provide screen reader support
- Test with accessibility tools

### Error Handling
- Implement error boundaries for graceful error handling
- Provide meaningful error messages to users
- Log errors appropriately for debugging
- Implement retry mechanisms for failed operations
- Use proper loading and error states

## Code Organization

### File Structure
```
app/
├── (auth)/          # Route groups
├── dashboard/       # Feature-based routing
├── api/             # API routes
├── globals.css      # Global styles with CSS variables
components/
├── ui/              # Reusable UI components
├── forms/           # Form components
└── layout/          # Layout components
hooks/               # Custom hooks
stores/              # Zustand stores
types/               # TypeScript type definitions
utils/               # Utility functions
```

### Naming Conventions
- Use PascalCase for components: `UserProfile.tsx`
- Use camelCase for functions and variables: `getUserData`
- Use kebab-case for files: `user-profile.tsx`
- Use SCREAMING_SNAKE_CASE for constants: `API_BASE_URL`

### Import Organization
```typescript
// External libraries
import React from 'react';
import { NextPage } from 'next';

// Internal modules
import { Button } from '@/components/ui/Button';
import { useAuth } from '@/hooks/useAuth';

// Type imports
import type { User } from '@/types/user';
```

## Development Workflow

### Git Workflow
- Use feature branches for development
- Write descriptive commit messages
- Use conventional commits format
- Create pull requests for code review
- Run tests and linting before committing

### Code Quality
- Use ESLint and Prettier for code formatting
- Implement pre-commit hooks
- Use TypeScript strict mode
- Follow consistent naming conventions
- Write self-documenting code

### Performance Monitoring
- Monitor bundle size with webpack-bundle-analyzer
- Use React DevTools Profiler
- Implement performance monitoring
- Track Core Web Vitals
- Use proper caching strategies

## Deployment and Environment

### Environment Variables
- Use `.env.local` for local development
- Use `.env.production` for production environment
- Never commit secrets to version control
- Validate required environment variables
- Use different secrets for different environments

### Docker Configuration
- Use multi-stage builds for optimization
- Implement proper security practices
- Use non-root user in containers
- Optimize image size and layers

### CI/CD Pipeline
- Run tests and linting on every commit
- Build and test Docker images
- Deploy to staging environment
- Use proper deployment strategies

## Best Practices Summary

1. **Always use TypeScript** with strict configuration
2. **Prefer Server Components** over Client Components
3. **Use CSS root variables** for colors and design tokens
4. **Implement proper error handling** with user-friendly messages
5. **Write accessible code** that works with screen readers
6. **Test user interactions** not implementation details
7. **Optimize for performance** with proper caching and code splitting
8. **Secure your application** with proper validation and authentication
9. **Use consistent patterns** across the codebase
10. **Document complex logic** and business rules

## Common Patterns

### API Route Pattern
```typescript
export async function GET(request: NextRequest) {
  try {
    const data = await fetchData();
    return NextResponse.json(data);
  } catch (error) {
    return NextResponse.json(
      { error: 'Failed to fetch data' },
      { status: 500 }
    );
  }
}
```

### Component Pattern
```typescript
interface ComponentProps {
  // Define props with proper types
}

export function Component({ ...props }: ComponentProps) {
  // Component logic
  return (
    // JSX
  );
}
```

### Custom Hook Pattern
```typescript
function useCustomHook() {
  // Hook logic
  return {
    // Return values
  };
}
```

This document serves as the comprehensive guide for developing the Constrack project. Follow these patterns and practices to maintain code quality, performance, and accessibility standards.
