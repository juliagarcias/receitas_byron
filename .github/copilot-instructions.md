# Receitas App - AI Coding Guidelines

## Architecture Overview
This is a Next.js 16 app using the App Router for displaying recipes. Data is statically defined in `src/app/lib/data.ts` as an array of `Recipe` objects. Components are organized in `src/app/components/` with each component in its own folder containing an `index.tsx` file.

## Key Patterns
- **Path Aliases**: Use `@/*` for imports from `src/` (configured in `tsconfig.json`)
- **Component Structure**: Components export default from `index.tsx` files in named folders
- **Recipe Data Flow**: Recipes are imported from `@/app/lib/data`, displayed via `RecipeCard` components that link to `/receitas/[id]` pages
- **Styling**: Tailwind CSS v4 with orange (`orange-500`) as primary color for links and accents
- **Icons**: Lucide React icons (e.g., `ChevronRight`, `ChevronLeft`)
- **Language**: All UI text in Portuguese (pt-BR)

## Component Examples
- **InfoPill**: Displays metadata like prep time - accepts `title` (string) and `info` (string|number)
- **PreparationStep**: Numbered instruction steps - takes `index` (number) and `description` (string)
- **RecipeCard**: Recipe preview with image, title, description - links to individual recipe page

## File Organization
- Pages: `src/app/page.tsx` (home), `src/app/receitas/page.tsx` (list), `src/app/receitas/[id]/page.tsx` (detail)
- Components: `src/app/components/[ComponentName]/index.tsx`
- Data: `src/app/lib/data.ts`
- Images: `public/receitas/` (referenced as `/receitas/filename.png`)

## Development Workflow
- Start dev server: `npm run dev`
- Build: `npm run build`
- Lint: `npm run lint`
- No tests currently implemented

## Data Structure
```typescript
type Recipe = {
  id: string;
  title: string;
  description: string;
  image: string;
  prepTime: string;
  cookTime: string;
  servings: number;
  ingredients: string[];
  instructions: string[];
  category: string;
}
```

When adding new recipes, update the `recipes` array in `lib/data.ts` and ensure images are placed in `public/receitas/`.