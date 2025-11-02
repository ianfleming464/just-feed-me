# Just Feed Me - Browser Extension

## 1. Executive Summary
Just Feed Me is a browser extension that automatically skips the lengthy preambles, stories, and advertisements on recipe websites by detecting and auto-clicking "Jump to Recipe" buttons. The extension eliminates the frustrating user experience of scrolling through irrelevant content to find actual cooking instructions.

### Key Value Propositions
- Instant access to recipes without manual scrolling or clicking
- Saves time and reduces frustration when browsing recipe websites
- Works silently in the background with minimal user intervention
- Respects user preferences with customizable site-specific controls

## 2. Target Audience
### Primary Users
- Home cooks who frequently use online recipes
- Meal planners who browse multiple recipes quickly
- Professional chefs researching recipes online
- Anyone frustrated with recipe blog content padding

### User Needs
- Quick access to recipe instructions without scrolling
- Ability to disable the extension on specific sites when desired
- Confirmation that the extension worked (subtle feedback)
- Simple, non-intrusive operation that doesn't interfere with browsing

## 3. Core Features & Functionality

### 3.1 Automatic Recipe Jump Detection
- Pattern matching system detects common "Jump to Recipe" buttons
    - Searches for "Jump to Recipe" text variants
    - Searches for "Skip to Recipe" text variants
    - Case-insensitive matching to catch all variations
- Automatic click simulation when button is detected
    - Triggers immediately upon page load
    - Only when extension is enabled (toggled on)
    - Respects blacklisted sites (does not activate)
- Graceful failure handling
    - If no jump button found, page loads normally
    - No error messages or interruptions to user experience

### 3.2 Extension Toggle Control
- Global on/off switch accessible via extension icon
    - Clicking icon opens popup interface
    - Toggle switch prominently displayed in popup
    - Visual indicator shows current state (icon change or badge)
    - State persists across browser sessions
- Toggle affects all recipe sites globally
    - When off, no automatic jumping occurs anywhere
    - When on, works on all sites except blacklisted ones

### 3.3 Site-Specific Blacklist
- Per-site disable functionality
    - Right-click extension icon reveals context menu
    - "Disable on this site" option adds current domain to blacklist
    - Blacklisted sites immune to auto-jump even when extension is on
- Blacklist management
    - Users can view list of blacklisted sites in settings
    - Users can remove sites from blacklist manually
    - Blacklist persists across browser sessions

### 3.4 Visual Feedback System
- Brief notification when auto-jump occurs
    - Small toast notification appears in corner of page
    - Message confirms "Jumped to recipe"
    - Auto-dismisses after 2-3 seconds
    - Non-intrusive, doesn't block content
- No notification when extension is toggled off
- No notification when no jump button is found

### 3.5 First-Time User Experience
- Welcome message on first installation
    - Brief explanation of what the extension does
    - Simple illustration of how to toggle on/off
    - Note about right-click to disable on specific sites
    - Dismissible with "Got it" or similar button
    - Only shows once per installation

### 3.6 Settings Interface
- Settings page accessible from popup
    - Link in popup labeled "Settings" or gear icon
    - Opens in new tab or embedded panel
    - Contains blacklist management interface
    - Provides information about extension permissions

## 4. User Interface Design

### 4.1 Design Philosophy
- Playful and approachable aesthetic matching "Just Feed Me" brand personality
- Minimal interface to avoid cluttering browser
- Clear visual states for enabled/disabled modes
- Friendly, food-themed visual elements

### 4.2 Visual Design Elements
- Extension icon with playful food theme (fork, plate, or hungry character)
- Color coding for states (e.g., full color when active, grayscale when disabled)
- Toast notifications with light, friendly styling
- Popup interface with clean, modern design
- Settings page with organized, scannable layout

### 4.3 Interactive Elements
- Clickable extension icon opens popup
- Toggle switch in popup for enable/disable
- Right-click context menu for blacklist
- Settings link/button in popup
- Clear call-to-action buttons in settings
- Dismissible welcome message

## 5. User Journey Flows

### 5.1 First-Time Installation
- User installs extension from Chrome Web Store or Firefox Add-ons
- Extension icon appears in browser toolbar
- Welcome message appears explaining functionality
    - Describes automatic jump feature
    - Shows how to toggle on/off via popup
    - Mentions right-click to disable on specific sites
- User dismisses welcome message
- Extension is enabled by default
- User visits recipe site and experiences automatic jump

### 5.2 Standard Recipe Browsing (Extension Enabled)
- User navigates to recipe website
- Page begins loading
- Extension detects "Jump to Recipe" button
- Extension auto-clicks button
- Page jumps to recipe section
- Brief toast notification confirms action
- User proceeds to read recipe

### 5.3 Toggling Extension On/Off
- User clicks extension icon in toolbar
- Popup opens showing current state
- User clicks toggle switch
- Extension changes state (enabled ↔ disabled)
- Icon updates to reflect new state
- Popup shows confirmation of state change
- User closes popup or it auto-closes

### 5.4 Disabling on Specific Site
- User is on a recipe site where they don't want auto-jump
- User right-clicks extension icon
- User selects "Disable on this site"
- Current domain added to blacklist
- Brief confirmation message appears
- Future visits to this site load normally (no auto-jump)

### 5.5 Managing Blacklist
- User clicks extension icon to open popup
- User clicks "Settings" link or gear icon
- Settings page opens in new tab
- User views list of blacklisted domains
- User selects domain to remove
- User clicks remove/delete button
- Domain removed from blacklist
- Confirmation message appears
- Future visits to this site will auto-jump (if extension enabled)

## 6. Business Rules & Logic

### 6.1 Detection Priority
- Extension only activates on pages containing recipe-related content
- Button detection occurs immediately after DOM loads
- First matching button is clicked (if multiple exist)
- Maximum one auto-click per page load (no repeated clicking)

### 6.2 Blacklist Rules
- Blacklist applies at domain level (e.g., allrecipes.com)
- Subdomains treated as part of parent domain
- Blacklist overrides global enabled state
- Empty blacklist means extension works on all sites (when enabled)

### 6.3 Toggle State Rules
- Extension disabled state applies universally across all sites
- Toggle state persists when browser closes and reopens
- Toggle state syncs across browser windows (if browser supports sync)
- Default state after installation is enabled

### 6.4 Notification Rules
- Notifications only appear when auto-jump successfully executes
- No notification if extension is disabled
- No notification if site is blacklisted
- No notification if no jump button found
- Notifications never stack or queue (one at a time maximum)

### 6.5 Welcome Message Rules
- Displays only on first installation
- Does not reappear after dismissal
- Does not block normal extension functionality
- Can be dismissed without reading
- Does not appear after extension updates

## 7. Accessibility Requirements
- Extension icon has appropriate alt text for screen readers
- Toast notifications are screen-reader accessible
- Popup interface keyboard navigable
- Settings page follows WCAG 2.1 AA standards
- Toggle switch has clear focus indicators
- All interactive elements have sufficient color contrast
- Screen reader announces state changes

## 8. Performance Expectations
- Button detection completes within 500ms of page load
- Auto-click triggers within 100ms of detection
- Extension has negligible impact on page load times
- Popup opens within 100ms of icon click
- Settings and blacklist operations respond instantly
- Extension memory footprint remains under 50MB

## 9. Security & Privacy Requirements
- Extension requests only necessary browser permissions
    - `activeTab` - to detect and interact with current page
    - `storage` - to save toggle state and blacklist
    - `contextMenus` - for right-click "Disable on this site" option
- No data collection or external transmission
- No tracking of user browsing history
- No analytics or telemetry
- Blacklist stored locally only (browser's built-in sync if available)
- Open source code for community security review
- No third-party dependencies that could compromise privacy

## 10. Distribution & Maintenance
- Primary distribution via Chrome Web Store
- Secondary distribution via Firefox Add-ons
- Future consideration: Safari App Store (requires separate implementation)
- Open source repository on GitHub from day one
- Clear installation instructions in repository README
- Version numbering following semantic versioning (semver)
- Changelog maintained for all releases
- Issue tracking via GitHub Issues
- Community contributions welcome via pull requests

### 10.1 Browser Compatibility Notes
- **Chrome/Edge**: Share identical codebase (both Chromium-based)
- **Firefox**: Requires minor manifest and API adjustments, but core logic identical
- **Safari**: Requires significant additional work
    - Must be wrapped in native Swift/Objective-C app
    - Requires Xcode and macOS for development
    - Requires Apple Developer account ($99/year)
    - Uses Apple's web extension converter tool
    - Separate build and distribution pipeline
    - Recommended as Phase 4 (post-launch enhancement)

## 11. Development Phases

### Phase 1: Core Functionality (MVP)
**Goal**: Get the basic auto-jump working in Chrome with manual testing

**Deliverables**:
- Manifest file (extension configuration)
- Content script that detects and clicks "Jump to Recipe" buttons
- Basic pattern matching for common button text
- Load extension in Chrome as "unpacked extension"
- Test on 5-10 popular recipe sites

**Learning Focus**:
- Understanding extension architecture (manifest, content scripts)
- DOM manipulation and element detection
- Chrome extension APIs basics
- Manual testing workflow

**Review Checkpoint**: Test the extension on various recipe sites, understand how button detection works, discuss what's working and what needs refinement

---

### Phase 2: User Controls & State Management
**Goal**: Add toggle functionality and persistent storage

**Deliverables**:
- Simple popup UI with on/off toggle
- Storage API integration to persist enabled/disabled state
- Extension icon in toolbar
- Icon badge or color change to indicate state
- State persists across browser sessions

**Learning Focus**:
- Browser storage APIs
- Popup HTML/CSS/JavaScript
- State management patterns
- Communication between popup and content scripts

**Review Checkpoint**: Review how state is managed, understand storage patterns, test toggle functionality, discuss UI/UX improvements

---

### Phase 3: Blacklist & Context Menu
**Goal**: Add per-site control and settings page

**Deliverables**:
- Right-click context menu "Disable on this site"
- Blacklist stored in browser storage
- Settings page UI for managing blacklist
- Logic to check blacklist before auto-clicking
- Remove sites from blacklist functionality

**Learning Focus**:
- Context menus API
- Settings page development
- Data structure for blacklist
- Domain extraction and matching

**Review Checkpoint**: Review blacklist implementation, test context menu, understand how settings page communicates with extension, discuss edge cases

---

### Phase 4: Polish & Feedback
**Goal**: Add visual feedback and welcome experience

**Deliverables**:
- Toast notification when auto-jump occurs
- Welcome message on first install
- Improved popup UI with playful design
- Extension icon with food theme
- Polish CSS and animations

**Learning Focus**:
- Toast/notification implementation
- First-run detection
- CSS animations and transitions
- Icon design basics

**Review Checkpoint**: Review notification system, test welcome flow, evaluate overall UX, finalize design elements

---

### Phase 5: Firefox Compatibility
**Goal**: Make extension work in Firefox

**Deliverables**:
- Firefox-compatible manifest adjustments
- Test in Firefox Developer Edition
- Fix any Firefox-specific issues
- Update documentation for Firefox

**Learning Focus**:
- Browser differences and compatibility
- Firefox add-on specifics
- Cross-browser testing strategies

**Review Checkpoint**: Compare Chrome vs Firefox implementations, understand manifest differences, test in both browsers

---

### Phase 6: Publication & Distribution
**Goal**: Publish to web stores and set up GitHub

**Deliverables**:
- Chrome Web Store listing (screenshots, description, etc.)
- Firefox Add-ons listing
- GitHub repository with README
- Installation instructions
- License file (MIT or similar)
- Initial release (v1.0.0)

**Learning Focus**:
- Web store submission process
- Writing effective extension descriptions
- Creating promotional materials
- Open source best practices
- Version control and releases

**Review Checkpoint**: Review store listings, discuss marketing copy, finalize documentation, prepare for launch

---

### Phase 7 (Future/Optional): Safari Support
**Goal**: Extend to Safari users

**Deliverables**:
- Xcode project with Swift wrapper
- Converted web extension
- Safari App Store listing
- macOS testing

**Learning Focus**:
- Safari extension architecture
- Apple's web extension converter
- Xcode basics
- App Store submission

**Review Checkpoint**: Assess complexity vs demand, decide if worth pursuing

---

## 12. Technical Implementation Overview

### 12.1 Technology Stack
- **Languages**: JavaScript (core logic), HTML (UI), CSS (styling), JSON (configuration)
- **No build tools required**: Pure vanilla JavaScript, no frameworks needed
- **Development environment**: Any text editor + browser
- **Version control**: Git + GitHub

### 12.2 File Structure
```
just-feed-me/
├── manifest.json          (Extension configuration)
├── content.js            (Main auto-jump logic)
├── popup.html            (Popup UI)
├── popup.js              (Popup logic)
├── settings.html         (Settings page)
├── settings.js           (Settings logic)
├── background.js         (Background service worker)
├── styles.css            (Shared styles)
└── icons/                (Extension icons)
    ├── icon-16.png
    ├── icon-48.png
    └── icon-128.png
```

### 12.3 Testing Process
**Local Testing**:
1. Chrome: Navigate to `chrome://extensions/`
2. Enable "Developer mode" toggle
3. Click "Load unpacked"
4. Select extension folder
5. Visit recipe sites to test

**Firefox Testing**:
1. Navigate to `about:debugging#/runtime/this-firefox`
2. Click "Load Temporary Add-on"
3. Select manifest.json file
4. Visit recipe sites to test

**Test Sites** (recommended for thorough testing):
- allrecipes.com
- foodnetwork.com
- simplyrecipes.com
- budgetbytes.com
- seriouseats.com

### 12.4 Publishing Process

**Chrome Web Store**:
1. Create developer account ($5 one-time fee)
2. Prepare assets (screenshots, promotional images, description)
3. Zip extension files
4. Upload to Chrome Web Store Developer Dashboard
5. Fill out store listing details
6. Submit for review (typically 1-3 days)

**Firefox Add-ons**:
1. Create account on addons.mozilla.org (free)
2. Prepare assets and description
3. Zip extension files (or submit source files)
4. Submit through developer hub
5. Wait for automated and manual review (1-7 days)

**Safari App Store** (if Phase 7):
1. Enroll in Apple Developer Program ($99/year)
2. Use Xcode to convert web extension
3. Create App Store listing
4. Submit through App Store Connect
5. Longer review process (typically 1-2 weeks)

### 12.5 Key Permissions Explained
- **`activeTab`**: Allows extension to access current page content only when user interacts with extension (e.g., clicks icon)
- **`storage`**: Allows extension to save data locally (toggle state, blacklist)
- **`contextMenus`**: Allows extension to add items to right-click menu