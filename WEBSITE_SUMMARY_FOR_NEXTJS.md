# United Muslim Ummah (UMU) Website - Complete Summary for Next.js Migration

## 📋 Project Overview
- **Project Name:** United Muslim Ummah (UMU)
- **Current Status:** Single-page HTML/CSS/JS application
- **Target Migration:** Next.js with React
- **Styling:** Tailwind CSS (currently CDN, can be npm package)
- **Current File:** `/home/amql3it/Desktop/AMQL3it/umu/index.html` (1,430 lines, monolithic)

---

## 🎨 Design System & Colors

### Color Palette
- **Primary Color:** `#0F6A3B` (Dark Green) - `bg-primary`, `text-primary`
- **Primary Dark:** Darker shade of primary - `bg-primary-dark`
- **Gold Accent:** `#B28800` - `bg-gold`, `text-gold`
- **Text Primary:** Dark gray
- **Background:** Light gray (`#f9fafb`, `#f3f4f6`)
- **White:** `#ffffff`
- **Borders:** Light gray with opacity

### Typography
- **Font Family:** System default (via Tailwind)
- **Heading Font Weight:** Bold/Black (font-black, font-bold)
- **Hero Font Size:** 4xl-6xl on desktop, 3xl on mobile
- **Section Titles:** 3xl-4xl font-black
- **Body Text:** Regular to semibold, gray colors

---

## 📱 Page Structure & Components

### 1. **Navigation Header** (Sticky, Always Visible)
**Location:** Top of page, sticky z-50

**Elements:**
- **Logo Section:**
  - Logo image: `./assets/logo.png` (40x40px, rounded, border)
  - Brand text: "United Muslim Ummah" (white, large, bold)
  - Tagline: "Global Islamic Community" (gold, small uppercase)

- **Desktop Navigation Menu:**
  - Links: Home, About (mission), Events, News Portal, Gallery, Contact
  - Active link styling: white text, gold hover effect
  - Join/Login button: gold background, text-primary-dark

- **Mobile Hamburger Menu:**
  - Toggle menu dropdown with same navigation items
  - Full-width dropdown below header

---

### 2. **Home Page** (Main Landing Page)

#### 2.1 Hero Section
- **Background:** Gradient or solid color background
- **Content:**
  - Large logo image (150x150px on mobile, 160x160px on desktop)
  - Main heading: "United Muslim Ummah" (largest size)
  - Subheading: "Global Islamic Community" (gold text, smaller)
  - Description paragraph about unity and progress
  - Two CTA buttons:
    - "Our Mission" (gold bg, primary text)
    - "Join Community" (transparent, border)

#### 2.2 Stats Section
**Card Style:** White background, rounded, shadow, -mt-16 offset effect

**4 Stat Cards:**
1. Counter: "1900" Million Muslims
2. Counter: "60" Member Countries
3. Counter: "100%" Percent United
4. Counter: "50" Peace Initiatives

**Animation:** Counter animation from 0 to target number on page load

#### 2.3 Motto Section
- **Center aligned**
- Quote: "One Ummah, One Heart, One Future"
- Decorative gold line underneath
- Supporting description text

#### 2.4 Mission & Vision Section (`#mission-section`)
**Layout:** 2 column cards

- **Card 1 - Our Mission:**
  - Icon: Lightning bolt SVG
  - Title: "Our Mission"
  - Content: Paragraph about uniting Muslims globally

- **Card 2 - Our Vision:**
  - Icon: Eye SVG
  - Title: "Our Vision"
  - Content: Paragraph about Muslim world vision

#### 2.5 Latest Event Section
**Card Layout:** 2-column flex (responsive)

- **Left Side:** Event image
- **Right Side:**
  - Status badge (UPCOMING)
  - Date and location indicators
  - Event title (large heading)
  - Event summary text
  - "View Details" button

**Data Source:** First item from `eventsData` array

#### 2.6 Gallery Carousel Section (`Moments of Unity`)
**Layout:** Horizontal scrollable carousel

- **Images:** Gallery items 1-7 from `galleryData`
- **Card Style:** Rounded, h-80, relative overflow, gradient overlay
- **Text Overlay:** Bottom left, title of gallery item
- **Controls:** Left/right arrow buttons (absolute positioned)
- **Interaction:** Click to view full gallery

#### 2.7 News Carousel Section (`News & Updates`)
**Layout:** Horizontal scrollable carousel

- **Cards:** News items 1-4
- **Card Content:**
  - Image (h-48)
  - Date badge (gold text)
  - Title (bold, primary color)
  - Summary text (line-clamped to 2 lines)
- **Interaction:** Click card to open modal

#### 2.8 Contact Section (`#contact-section`)
**Background:** Primary color with white text

**Layout:** 2 columns

- **Left Column (Contact Info):**
  - Headquarters: International Islamic Center, Dubai, UAE
  - Email: info@ummaah.org
  - Phone: +971 (0) 4 123 4567

- **Right Column (Contact Form):**
  - Fields: Full Name, Email, Message (textarea)
  - Submit button: "Send Message"
  - Styling: Light background inputs, primary button

---

### 3. **Events Page**

#### 3.1 Header Section
- **Title:** "All Community Events"
- **Subtitle:** Description about joining gatherings
- **Background:** Primary color

#### 3.2 Filter Tabs
**Horizontal tabs:**
- All Events (default active)
- Upcoming (filter by status: "upcoming")
- Ongoing (filter by status: "ongoing")
- Previous (filter by status: "previous")

#### 3.3 Events Grid
**Grid:** 3 columns on desktop, 2 on tablet, 1 on mobile

**Event Card Components:**
- Image (h-48, hover scale effect)
- Status badge (top-right, color-coded):
  - "upcoming" = gold bg
  - "ongoing" = green bg
  - "previous" = gray bg
- Date and location indicators (top-left corner text)
- Title (xl font-bold)
- Summary text (line-clamped)
- "View Details →" link button
- Full height flex column for proper spacing

#### 3.4 Pagination
- Previous/Next arrow buttons
- Page number buttons (smart display: 1, ..., current-1, current, current+1, ..., last)
- Current page highlighted in primary color

**Items per page:** 6

---

### 4. **News Portal Page**

#### 4.1 Header Section
- **Title:** "News Portal"
- **Subtitle:** "Latest updates from the Ummah"
- **Background:** Light gray/white

#### 4.2 News Grid
**Grid:** 3 columns on desktop, 2 on tablet, 1 on mobile

**News Card Components:**
- Image (h-48)
- Date badge (gold, small text)
- Title (bold, primary color)
- Summary text (line-clamped)
- Click opens modal

#### 4.3 Pagination
Same as events page

**Items per page:** 6

---

### 5. **Gallery Page**

#### 5.1 Header Section
- **Title:** "Gallery"
- **Subtitle:** "Moments captured from around the world"
- **Background:** Primary color

#### 5.2 Masonry Grid
**Grid:** CSS Grid with auto-rows and smart span classes

**Layout Logic:**
- Every 5th item spans 2 columns and 2 rows (col-span-2 row-span-2)
- Other items: col-span-1 row-span-1
- Rounded corners, overflow hidden

**Image Interactions:**
- Hover scale effect (scale-110)
- Dark overlay on hover (opacity-0 → opacity-100)
- Title text centered on overlay

#### 5.3 Pagination
**Items per page:** 12

---

### 6. **Modal/Detail View**

**Structure:** Overlay modal that appears on top of page

**Components:**
- **Background:** Semi-transparent black with backdrop blur
- **Modal Container:** White rounded card, max-width-3xl
- **Close Button:** Top-right, circular white button with "×"

**Content Sections:**
1. **Header Image:** 300-400px height, gradient overlay from top
2. **Title Section (over image):**
   - Status/Category badge (gold bg, top-left)
   - Title (largest text, white, bottom-left)
3. **Content Area:**
   - Meta info: Date and location (if event)
   - Full description content (HTML with formatting)
   - Call-to-action button (if event)

**Trigger:** Clicking on event card, news card, or "View Details" button
**Close:** Click close button or click backdrop overlay

---

## 📊 Data Models & Content Arrays

### Events Data Array (`eventsData`)
**Total:** 10 events with Islamic themes

**Each Event Object:**
```javascript
{
  id: number,
  title: string,
  date: string (formatted as "Mar 15, 2026"),
  status: "upcoming" | "ongoing" | "previous",
  location: string,
  image: string (Unsplash URL with fallback),
  summary: string (1-2 sentences),
  content: string (HTML formatted, with <p>, <ul>, <button> tags)
}
```

**Event Titles:**
1. Quran Competition 2026 (Dubai) - Upcoming
2. Quran Meaning & Tafsir Event (Istanbul) - Upcoming
3. Islamic History & Culture Expo (Cairo) - Ongoing
4. Quiz Competition on Islamic Knowledge (London) - Upcoming
5. Mosque Architecture & Design Symposium (Kuala Lumpur) - Upcoming
6. Islamic Awareness & Education Movement (Global Online) - Ongoing
7. Halal Expo 2026 (Singapore) - Upcoming
8. Educational Expo: Islamic Learning Pathways (Beirut) - Upcoming
9. Islamic Finance & Economics Conference (Bahrain) - Previous
10. Interfaith Dialogue Summit (Vienna) - Previous

### News Data Array (`newsData`)
**Total:** 25 news articles (auto-generated format)

**Each News Object:**
```javascript
{
  id: number,
  title: string (format: "News Title {i}: Global Initiative"),
  date: string (formatted date),
  image: string (Pexels URL placeholder),
  summary: string,
  content: string (Lorem ipsum formatted)
}
```

### Gallery Data Array (`galleryData`)
**Total:** 30 gallery items with Islamic themes

**Each Gallery Object:**
```javascript
{
  id: number,
  title: string (Islamic-themed titles),
  image: string (Unsplash URL)
}
```

**Gallery Titles (Sample):**
- Beautiful Islamic Calligraphy
- Historic Mosque Architecture
- Quranic Verses Display
- Islamic Cultural Festival
- Grand Mosque Interior
- Ramadan Celebrations
- Islamic Art & Patterns
- Ummah Unity Event
- Quran Competition Finals
- Mosque Dome & Minarets
- Islamic Educational Programs
- (... and 20 more)

---

## 🎯 Key Functionality & Interactions

### 1. **Navigation & Routing**
- **Function:** `router(pageId)` - switches between pages
- **Behavior:**
  - Hides all sections (`.page-section`)
  - Shows selected section
  - Updates nav link active state
  - Scrolls to top for major page changes
  - Smooth scroll for internal sections (#mission, #contact)
- **Pages:**
  - `home` - Landing page with all home components
  - `events` - Events listing and filtering
  - `news` - News portal
  - `gallery` - Photo gallery

### 2. **Event Filtering**
- **Function:** `filterEvents(type, buttonElement)`
- **Logic:**
  - Filters `eventsData` by status: 'all', 'upcoming', 'ongoing', 'previous'
  - Updates tab button styling (active = primary, inactive = gray)
  - Re-renders events grid and pagination

### 3. **Modal System**
- **Open Function:** `openModal(type, id)`
- **Close Function:** `closeModal()`
- **Parameters:**
  - `type`: 'event' or 'news'
  - `id`: Item ID to display
- **Behavior:**
  - Finds item from appropriate data array
  - Populates modal with image, title, date, location (if event), content
  - Disables body scroll while open
  - Closes on close button or backdrop click

### 4. **Carousel Scrolling**
- **Function:** `scrollCarousel(elementId, amount)`
- **Behavior:** Smooth horizontal scroll by amount pixels

### 5. **Pagination**
- **Function:** `createPagination(total, limit, current, elementId, renderFn)`
- **Logic:**
  - Calculates total pages
  - Shows prev/next buttons
  - Shows smart page number buttons (1, ..., current area, ..., last)
  - Calls render function on page change

### 6. **Counter Animation**
- **Function:** `animateCounters()`
- **Behavior:**
  - Triggers on home page load
  - Animates numbers from 0 to target over 200 frames
  - Speed: 20ms per frame

### 7. **Responsive Mobile Menu**
- **Hamburger Toggle:** Toggles visibility of mobile menu dropdown
- **Mobile Menu:** Shows on devices below md breakpoint
- **Behavior:** Closes when navigation item clicked

---

## 🖼️ Asset Requirements

### Images to Create/Upload to `assets/` folder:
1. **Logo:** `logo.png` (40x40px minimum, ideally 100x100px for high DPI)
   - Circular, with rounded border
   - Islamic/Ummah related icon
   - Current fallback: placehold.co placeholder

### Image Sources (Current):
- **Events & Gallery:** Unsplash images (Islamic-themed URLs)
- **News:** Placeholder service URLs
- **Fallback Strategy:** If image fails to load, use `placehold.co` service

---

## 🛠️ Technical Implementation Details

### State Management
```javascript
const state = {
  eventsPage: 1,
  newsPage: 1,
  galleryPage: 1,
  itemsPerPage: 6,
};

let currentEventFilter = 'all';
let animated = false;
```

### Template Rendering Pattern
- Uses template literals with `${variable}` syntax
- Dynamic HTML injection via `innerHTML`
- Event handlers via `onclick` attributes

### CSS Classes Used
- **Tailwind Utilities:** Spacing (px, py, m, mt, mb), sizing (w, h), colors, flexbox, grid
- **Custom Animations:** `animate-slide-up` (for modal), counter animation
- **Responsive Prefixes:** `md:` (medium breakpoint), `lg:` (large breakpoint)
- **State Classes:** `active-section`, `active` (for nav), `hidden` (for mobile menu/modal)

---

## 📦 Dependencies & Scripts

### Current (HTML/CSS/JS):
- **Tailwind CSS:** CDN (v3+)
- **No other dependencies**

### For Next.js Migration:
- Next.js 14+ (with App Router recommended)
- React 18+
- Tailwind CSS (npm package)
- Optional: React Router (for internal routing)

---

## 📄 File Structure for Next.js

### Suggested Structure:
```
src/
├── app/
│   ├── layout.tsx (Header, Footer, Providers)
│   ├── page.tsx (Home/Landing Page)
│   ├── events/
│   │   └── page.tsx
│   ├── news/
│   │   └── page.tsx
│   └── gallery/
│       └── page.tsx
├── components/
│   ├── Header.tsx
│   ├── Footer.tsx
│   ├── Navigation.tsx
│   ├── MobileMenu.tsx
│   ├── Modal.tsx
│   ├── EventCard.tsx
│   ├── NewsCard.tsx
│   ├── GalleryCard.tsx
│   ├── Carousel.tsx
│   ├── Pagination.tsx
│   └── ...
├── data/
│   ├── events.ts
│   ├── news.ts
│   ├── gallery.ts
│   └── constants.ts
├── hooks/
│   └── useNavigation.ts
├── types/
│   └── index.ts
├── styles/
│   └── globals.css (Tailwind imports)
└── public/
    └── assets/
        └── logo.png
```

---

## 🎨 Styling Notes for Next.js

### Tailwind Configuration Needed:
```javascript
// tailwind.config.ts
export default {
  theme: {
    extend: {
      colors: {
        primary: '#0F6A3B',
        'primary-dark': '#0a4620', // darker shade
        gold: '#B28800',
        'text-primary': '#1f2937',
        'sky-light': '#e0f2fe',
      },
    },
  },
}
```

### Global Styles:
- Remove browser defaults
- Set font families
- Configure scrollbar hiding (scrollbar-hide class)

---

## 🔄 User Interaction Flow

1. **Landing:** User arrives → Home page loads → Counters animate
2. **Browse Events:** User clicks "Events" → Events page → Can filter by status
3. **View Event Details:** User clicks event card → Modal opens with full content
4. **Browse Gallery:** User clicks "Gallery" → Masonry grid → Can paginate
5. **Read News:** User clicks "News Portal" → News grid → Can click to open details
6. **Contact:** User scrolls to contact section → Fills form → Submits

---

## ⚠️ Known Issues & Improvements Needed

1. **Images:** Currently using external Unsplash URLs with fallback to placehold.co
   - **Recommendation:** Download images locally to `assets/` folder for guaranteed availability

2. **Mobile Responsiveness:** Mobile menu hamburger needs better interaction feedback

3. **Performance:** Single 1,430-line HTML file should be split into components

4. **Accessibility:** Limited alt text and semantic HTML structure

5. **SEO:** No meta tags or structured data

---

## 📋 Component Checklist for Next.js

**Essential Components:**
- [ ] Header/Navigation
- [ ] Mobile Menu
- [ ] Hero Section
- [ ] Stats Counter
- [ ] Mission/Vision Cards
- [ ] Event Card
- [ ] News Card
- [ ] Gallery Card/Item
- [ ] Carousel (Horizontal scroll)
- [ ] Modal/Detail View
- [ ] Pagination
- [ ] Footer
- [ ] Filter Tabs
- [ ] Contact Form

**Hooks/Utilities:**
- [ ] useRouter (page navigation)
- [ ] useState (modal state, pagination, filters)
- [ ] useEffect (animations, data loading)

**Pages:**
- [ ] Home (/)
- [ ] Events (/events)
- [ ] News (/news)
- [ ] Gallery (/gallery)

---

## 🎯 Next.js Migration Strategy

1. **Setup:** Create Next.js project with Tailwind CSS
2. **Layout:** Create root layout with Header, Footer, Navigation
3. **Components:** Build reusable components (cards, carousel, modal, pagination)
4. **Data:** Move arrays to separate TypeScript files in `data/` folder
5. **Pages:** Create page components for each route
6. **Styling:** Implement Tailwind config with custom colors
7. **Routing:** Use Next.js App Router for navigation
8. **Assets:** Create `public/assets/` folder and optimize images
9. **Testing:** Test all interactions and responsive design
10. **Deploy:** Deploy to Vercel or preferred hosting

---

**Document Created:** January 12, 2026  
**Current File Size:** 1,430 lines (index.html)  
**Total Events:** 10  
**Total News Items:** 25  
**Total Gallery Items:** 30  
**Target Framework:** Next.js 14+  

---

**Note:** This document is comprehensive enough for an AI agent to understand the complete website structure, design system, functionality, and data models needed to recreate the website as a modern Next.js application.
