# Real Estate Property Showcase - Project Structure

## File Organization

```
├── index.html                     # Main HTML entry point
├── package.json                   # Project dependencies
├── tailwind.config.js            # Tailwind CSS configuration
├── postcss.config.js             # PostCSS configuration
├── vite.config.ts                # Vite build configuration
├── tsconfig.json                 # TypeScript configuration
├── svelte.config.js              # Svelte configuration
│
├── src/
│   ├── main.ts                   # Application entry point
│   ├── app.css                   # Global styles with Tailwind directives
│   ├── App.svelte                # Root component with routing logic
│   │
│   ├── components/               # Reusable components
│   │   ├── Navbar.svelte         # Navigation bar with mobile menu
│   │   ├── Footer.svelte         # Site footer
│   │   ├── PropertyCard.svelte   # Property listing card
│   │   ├── AgentCard.svelte      # Agent profile card
│   │   ├── ContactForm.svelte    # Contact form with validation
│   │   └── Gallery.svelte        # Image gallery with navigation
│   │
│   ├── pages/                    # Page components
│   │   ├── Home.svelte           # Homepage with hero, features, testimonials
│   │   ├── Listings.svelte       # Property listings with filters
│   │   ├── PropertyDetails.svelte # Individual property details
│   │   ├── About.svelte          # About page with team info
│   │   └── Contact.svelte        # Contact page with form and info
│   │
│   ├── stores/                   # Svelte stores for state management
│   │   └── navigation.js         # Current page and selected property state
│   │
│   └── data/                     # Static data
│       └── properties.js         # Property, agent, and testimonial data
```

## Component Details

### Navigation Components
- **Navbar.svelte**: Sticky navigation with responsive mobile menu, logo, and navigation links
- **Footer.svelte**: Multi-column footer with links, contact info, and social media

### Display Components
- **PropertyCard.svelte**: Card layout showing property image, price, location, specs, and view button
- **AgentCard.svelte**: Agent profile with photo, specialization, experience, and contact details
- **Gallery.svelte**: Image carousel with thumbnail navigation and arrow controls
- **ContactForm.svelte**: Form with name, email, phone, message fields and success feedback

### Page Components
- **Home.svelte**: Hero section, featured properties, benefits, testimonials, and CTA
- **Listings.svelte**: Grid layout with filter controls (type, bedrooms, price range)
- **PropertyDetails.svelte**: Full property details with gallery, specs, features, and inquiry form
- **About.svelte**: Company story, values, and team member profiles
- **Contact.svelte**: Contact form, office information, and map placeholder

## Data Structure

### Properties
Each property object contains:
- id, title, price, location, type
- bedrooms, bathrooms, area, yearBuilt
- images (array of URLs)
- description, features (array)
- featured, status

### Agents
Each agent object contains:
- id, name, title, email, phone
- image, specialization, experience, bio

### Testimonials
Each testimonial contains:
- id, name, role, content, rating, image

## Design System

### Colors
- **Primary (Emerald)**: #10b981 (primary-600)
- **Accent (Blue)**: #3b82f6 (accent-600)
- **Neutral**: White background with gray text

### Typography
- Font: Inter (Google Fonts)
- Weights: 300, 400, 500, 600, 700

### Button Styles
- `.btn-primary`: Emerald background
- `.btn-secondary`: Blue background
- `.btn-outline`: Emerald border with transparent background

### Responsive Breakpoints
- Mobile: Default
- Tablet: `md:` (768px)
- Desktop: `lg:` (1024px)

## Routing

Simple client-side routing using Svelte stores:
- Navigation controlled by `currentPage` store
- Property details accessed via `selectedPropertyId` store
- No external routing library required

## Key Features

1. **Fully Responsive**: Mobile-first design with breakpoints for tablet and desktop
2. **Static Data**: All content from local properties.js file
3. **Interactive Filters**: Type, bedrooms, and price range filtering on listings page
4. **Image Gallery**: Multi-image carousel with thumbnail navigation
5. **Contact Forms**: Form validation with success feedback
6. **Smooth Navigation**: Client-side routing without page reloads
7. **Modern Design**: Clean, premium aesthetic with subtle animations and hover effects

## Running the Project

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Technologies Used

- **Svelte 4**: UI framework
- **TypeScript**: Type safety
- **Vite**: Build tool and dev server
- **Tailwind CSS**: Utility-first styling
- **Pexels**: Stock photography (CDN links)
