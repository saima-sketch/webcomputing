# Tech Term Explorer - Design Guidelines

## Design Approach
**Selected System**: Modern Utility Design (inspired by Linear, Notion, and Material Design)
**Rationale**: Engineers need efficient, distraction-free tools focused on information clarity and quick access to definitions. The design prioritizes readability, clean information hierarchy, and professional aesthetics.

## Core Design Elements

### A. Color Palette
**Light Mode:**
- Primary: 220 70% 50% (professional blue for interactive elements)
- Background: 0 0% 100% (pure white)
- Surface: 220 13% 97% (subtle gray for cards)
- Text Primary: 220 15% 20% (near-black for definitions)
- Text Secondary: 220 10% 45% (gray for metadata)
- Border: 220 13% 90% (subtle card dividers)
- Accent: 260 60% 55% (purple for phonetics/examples)

**Dark Mode:**
- Primary: 220 70% 55% (slightly brighter blue)
- Background: 220 15% 10% (deep charcoal)
- Surface: 220 13% 15% (elevated card background)
- Text Primary: 220 15% 95% (off-white for definitions)
- Text Secondary: 220 10% 65% (light gray for metadata)
- Border: 220 13% 20% (subtle dark borders)
- Accent: 260 60% 65% (lighter purple for visibility)

### B. Typography
**Font Family**: Inter (via Google Fonts CDN) - exceptional readability for technical content
- Headers: font-semibold, tracking-tight
- Body: font-normal, leading-relaxed
- Technical Terms: font-medium
- Examples/Phonetics: font-light, italic

**Scale:**
- H1 (App Title): text-2xl md:text-3xl, font-bold
- H2 (Term Result): text-xl md:text-2xl, font-semibold
- Body (Definitions): text-base, leading-7
- Metadata (Part of Speech): text-sm, font-medium
- Examples: text-sm, italic

### C. Layout System
**Container Strategy**: max-w-4xl mx-auto px-4 sm:px-6 lg:px-8
**Spacing Primitives**: Use Tailwind units of 2, 4, 6, 8, 12, 16
- Micro spacing: gap-2, p-2 (within cards)
- Component spacing: p-4, gap-4, my-6 (between elements)
- Section spacing: py-8, my-12 (major sections)
- Large spacing: py-16 (header/footer)

**Grid System**: Single column for search results, stacking cards vertically with gap-6

### D. Component Library

**Header**
- Fixed position with backdrop-blur-sm and border-b
- Contains app title/logo (left), optional documentation link (right)
- Height: h-16, padding: px-6
- Background: bg-white/80 dark:bg-gray-900/80

**Search Bar**
- Prominent placement below header with py-12 spacing
- Input: rounded-xl, p-4, text-lg, w-full max-w-2xl
- Icon: Heroicons magnifying glass (left side)
- Shadow: shadow-lg on focus, transition-all duration-200
- Border: 2px focus ring in primary color

**Result Cards**
- Each card: rounded-2xl, p-6, bg-surface, border border-gray-200/50
- Shadow: shadow-sm, hover:shadow-md transition
- Card Header: Term name (text-2xl, font-semibold) + phonetic (text-sm, text-accent)
- Part of Speech: Pill-style badge (rounded-full, px-3, py-1, text-xs, bg-primary/10)
- Definitions: Numbered list (pl-6) with text-base, leading-7
- Examples: Blockquote style with border-l-4, pl-4, italic, text-secondary
- Spacing within card: space-y-4

**Footer**
- Minimal design: py-8, border-t, text-center
- Content: text-sm, text-secondary
- Links: hover:text-primary transition

**Empty State**
- Icon: Heroicons book-open (size-16, text-gray-300)
- Message: text-lg, text-secondary
- Center-aligned with py-24 spacing

**Loading State**
- Skeleton cards: animate-pulse with bg-gray-200 dark:bg-gray-700
- 3 placeholder cards to indicate content loading
- Maintains card structure without content

**Error State**
- Alert icon: Heroicons exclamation-triangle (text-amber-500)
- Message: text-base, clear error description
- Retry button: Primary button style

### E. Interactive Elements

**Buttons (if needed)**
- Primary: bg-primary, text-white, rounded-lg, px-6, py-3, font-medium
- Hover: bg-primary/90, transform scale-105
- Focus: ring-4, ring-primary/20

**Input Fields**
- Focus state: ring-2, ring-primary, border-primary
- Placeholder: text-gray-400
- Clear button (×): absolute right-4, text-gray-400, hover:text-gray-600

**Transitions**
- Cards: transition-all duration-200 for hover effects
- Search: transition duration-150 for responsive feel
- NO complex animations - keep interface snappy

## Accessibility
- Maintain consistent dark mode across all inputs and cards
- Ensure 4.5:1 contrast ratio for all text
- Focus indicators on all interactive elements
- ARIA labels for search input and result cards
- Keyboard navigation support (Tab, Enter for search)

## Key Design Principles
1. **Content First**: Typography and spacing optimized for reading definitions
2. **Clean Hierarchy**: Clear visual distinction between terms, definitions, and examples
3. **Efficient Interaction**: Immediate visual feedback, fast search, no distractions
4. **Professional Polish**: Subtle shadows, smooth transitions, refined details
5. **Responsive Excellence**: Mobile-first approach, touch-friendly targets (min 44px)

## Mobile Considerations
- Search bar: Full width on mobile with p-3 (slightly reduced)
- Cards: Reduce padding to p-4 on small screens
- Typography: Scale down by one size (text-xl → text-lg for terms)
- Header: Sticky positioning maintained, simplified on mobile