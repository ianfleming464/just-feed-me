# Just Feed Me - Development Guide

## Project Overview
This is a browser extension that auto-clicks "Jump to Recipe" buttons on recipe websites.

**IMPORTANT**: Read `PRODUCT_REQUIREMENTS.md` in the root directory for complete product specifications, user requirements, and development phases.

---

## Current Phase
**Phase 1: Core Functionality (MVP)**

Goal: Get the basic auto-jump working in Chrome with manual testing.

---

## Development Philosophy: TEACH, DON'T JUST CODE

**CRITICAL**: I'm learning browser extension development. Before implementing any code:

### 1. EXPLAIN THE WHY
- Why are we using this particular browser API?
- Why is this file structure necessary?
- Why does the manifest need these specific permissions?
- What problem does this pattern solve?
- Why this approach over alternatives?

### 2. EXPLAIN THE HOW
- How do content scripts communicate with background scripts?
- How does browser storage work vs localStorage?
- How do different parts of the extension interact?
- How does the browser load and execute each file?
- How does data flow through the extension?

### 3. EXPLAIN ALTERNATIVES
- What other approaches could work?
- What are the tradeoffs of each approach?
- Why is this approach better for our use case?
- What would break if we did it differently?

### 4. PROVIDE CONTEXT
- How does this fit into browser extension architecture?
- What are common pitfalls or gotchas with this pattern?
- What will I need to know for the next phase?
- What real-world extensions use similar patterns?

---

## Learning Goals by Phase

### Phase 1 (Core Functionality)
After completing this phase, I should understand:
- How browser extensions inject code into web pages
- The difference between content scripts, background scripts, and popup scripts
- How manifest.json configures the extension
- How to detect and manipulate DOM elements safely
- Why permissions matter and what each one does
- How to load unpacked extensions for testing
- How to debug extension code in browser DevTools
- The extension lifecycle (when each script runs)

### Phase 2 (State Management)
After completing this phase, I should understand:
- How browser.storage API works vs regular localStorage
- Why we need message passing between different scripts
- How state persists across browser sessions and tabs
- The lifecycle of extension components (popup, background, content)
- How popup communicates with content scripts and background
- Async storage patterns and promises
- When to use chrome.storage.local vs chrome.storage.sync

### Phase 3 (Advanced Features)
After completing this phase, I should understand:
- How context menus integrate with the browser UI
- Data structures for managing blacklists efficiently
- URL/domain parsing and matching strategies
- How to structure settings pages that modify extension behavior
- Communication patterns between settings page and extension
- Best practices for user preferences storage

### Phase 4 (Polish & Feedback)
After completing this phase, I should understand:
- Toast notification implementation patterns
- First-run detection strategies
- CSS injection and styling in content scripts
- Animation best practices for injected content
- Icon design and multiple size requirements

### Phase 5 (Firefox Compatibility)
After completing this phase, I should understand:
- Manifest V2 vs V3 differences
- Cross-browser compatibility considerations
- Firefox-specific API differences
- Browser polyfills and feature detection
- Testing strategies across browsers

### Phase 6 (Distribution)
After completing this phase, I should understand:
- Web store submission requirements and process
- Extension packaging and zip file structure
- Store listing best practices (descriptions, screenshots)
- Versioning strategies (semantic versioning)
- Update and deployment workflows

---

## Code Implementation Guidelines

When implementing each phase, please structure responses as:
```
## Phase X: [Phase Name]

### What We're Building
[Brief 2-3 sentence description of the phase goal]

### Why This Matters
[Explanation of why this feature/pattern is important for the extension and user experience]

### Browser Extension Concepts Introduced
- **Concept 1**: [Clear explanation with real-world analogy if helpful]
- **Concept 2**: [Clear explanation with real-world analogy if helpful]
- **Concept 3**: [Clear explanation with real-world analogy if helpful]

### Architecture Overview
[Diagram or description of how the pieces fit together]

### Implementation Plan
1. **[Step name]**: Why we're doing this and what it achieves
2. **[Step name]**: Why we're doing this and what it achieves
3. **[Step name]**: Why we're doing this and what it achieves

### Code Walkthrough
[After showing code, explain:]
- What each significant section does
- Why it's structured this way
- What browser APIs are being used and why
- What would happen if we removed or changed key parts

### Testing Strategy
- How to test this phase
- What to look for when testing
- Common issues and how to verify they're fixed
- Which recipe sites to test on

### Common Gotchas
- Thing 1 that might trip me up and how to avoid it
- Thing 2 that might trip me up and how to avoid it
- Thing 3 that might trip me up and how to avoid it

### Checkpoint Questions
Before moving to the next phase, I should be able to answer:
- Question 1 about architecture?
- Question 2 about why we chose this approach?
- Question 3 about how debugging works?

### What's Next
[Brief preview of what the next phase will build on top of this]
```

---

## Phase Review Checkpoints

Before moving to the next phase, conduct a review covering:

### 1. File-by-File Understanding
- What does each file do?
- Why does it exist?
- How does it interact with other files?
- What would break if it was removed?

### 2. API Deep Dive
- Which browser APIs were used?
- Why these specific APIs?
- What alternatives exist?
- What are the limitations or gotchas?

### 3. Architecture Decisions
- Why this structure over alternatives?
- What patterns are being followed?
- How does this scale for future features?
- What would need to change if requirements shifted?

### 4. Testing & Debugging
- How do I test this component in isolation?
- How do I debug issues in content scripts vs background scripts vs popup?
- What tools should I use?
- Where should I look when something breaks?

### 5. Knowledge Gaps
- What concepts am I still fuzzy on?
- What should I research further?
- What documentation should I read?

---

## Development Instructions

### General Workflow
1. Read phase requirements from PRODUCT_REQUIREMENTS.md
2. Review learning goals for this phase (above)
3. Implement with explanations at each step
4. Test on multiple recipe sites after each significant change
5. Conduct phase review checkpoint before proceeding
6. Document learnings in "Architecture Notes" section below

### Testing Sites (use these for verification)
- allrecipes.com
- foodnetwork.com
- simplyrecipes.com
- budgetbytes.com
- seriouseats.com
- bonappetit.com
- thekitchn.com

### Debugging Tips
- **Content Scripts**: Use regular DevTools (inspect page → Sources tab)
- **Popup**: Right-click extension icon → Inspect popup
- **Background Script**: Go to chrome://extensions → Details → Inspect views: background page
- **Console Errors**: Always check browser console for extension errors

---

## Reference Documentation

As we progress, please link to relevant documentation for:
- Browser APIs used (MDN Web Docs)
- Chrome Extension documentation
- Firefox Extension documentation
- Common patterns and best practices
- Example extensions using similar techniques

---

## Anti-Patterns to Avoid

Please call out immediately if I'm about to:
- Use deprecated or outdated APIs
- Create security vulnerabilities (XSS, injection attacks)
- Violate extension store policies
- Make cross-browser compatibility unnecessarily difficult
- Use inefficient patterns that won't scale
- Request excessive permissions
- Create poor user experience patterns

---

## Documentation Deliverables

After project completion (Phase 6), please create:

### DEVELOPER_GUIDE.md

Should include:

#### 1. Extension Architecture Overview
- High-level diagram of how all pieces fit together
- Explanation of each component type (content, background, popup, settings)
- Lifecycle of the extension from installation to usage

#### 2. File-by-File Breakdown
For each file in the project:
- Its purpose and why it exists
- Key functions and what they do
- How it interacts with other files
- Browser APIs it uses

#### 3. Browser APIs Deep Dive
For each API used:
- What it does in plain English
- Why we chose it over alternatives
- Code examples of its usage in our extension
- Common gotchas and how we handle them
- Links to official documentation

#### 4. Data Flow Diagrams
- User visits recipe page → detection → click (Phase 1)
- Toggle on/off flow (Phase 2)
- Blacklist site flow (Phase 3)
- Message passing between components

#### 5. Storage & State Management
- What data we store and where
- How state persists across sessions
- How different components access shared state
- Storage patterns used and why

#### 6. Permissions Explained
- Why each permission is needed
- What would break without it
- Privacy implications
- How to explain to users

#### 7. Debugging Guide
- How to debug each script type
- Common errors and solutions
- Where to look for different types of issues
- Chrome vs Firefox debugging differences

#### 8. Extension Recipes
Step-by-step guides for common tasks:
- Adding a new button pattern to detect
- Adding a new feature to the popup
- Adding a new storage field
- Modifying the blacklist logic
- Adding browser-specific code

#### 9. Cross-Browser Differences
- Manifest differences (Chrome vs Firefox)
- API differences encountered
- Testing strategies
- Polyfill patterns used

#### 10. Publishing & Distribution
- Pre-submission checklist
- Store listing requirements
- Screenshot guidelines
- Description writing tips
- Version management
- Update process

#### 11. Common Issues & Solutions
- Issue 1: [Description] → [Solution] → [Why it works]
- Issue 2: [Description] → [Solution] → [Why it works]
- Issue 3: [Description] → [Solution] → [Why it works]

#### 12. Future Enhancement Guide
- How to add new features without breaking existing ones
- Architecture decisions that support extensibility
- Where to add different types of features

---

## Architecture Notes

[This section will be filled in as we learn during development]

### Phase 1 Learnings

#### Session Progress
**Status**: In progress
**Completed**: manifest.json created
**Next step**: Create placeholder icons, then implement content.js
**Current todo**: Item 3 - Create placeholder icons for MVP testing

---

#### What We're Building
We're building the foundational piece of the extension: a content script that detects "Jump to Recipe" buttons on recipe websites and automatically clicks them. This gets the core functionality working so you can load it in Chrome and see it in action on real recipe sites.

#### Why This Matters
This is the **heart** of the extension - everything else we build in later phases (toggles, blacklists, notifications) supports or controls this core behavior. Starting here lets us verify the fundamental concept works before adding complexity. You'll also learn the absolute basics of how browser extensions inject code into web pages, which is foundational knowledge for everything that follows.

---

#### Browser Extension Concepts Introduced

**1. Manifest File (manifest.json)**
Think of this as the extension's "birth certificate" and "instruction manual" combined. It tells the browser:
- What your extension is called
- What permissions it needs
- Which scripts to run and where
- What version of the extension API to use (Manifest V3 is the current standard)

**2. Content Scripts**
JavaScript files that run **inside** web pages, in the page's DOM context. They can:
- Read and modify the page's HTML/DOM
- Listen for events on the page
- Access the page just like the page's own JavaScript can
- But they run in an "isolated world" - they can't directly access variables from the page's JavaScript

**3. Permissions**
Browser extensions can be dangerous, so browsers enforce strict permissions. We only request what we need:
- `storage`: Lets us save user preferences (we'll use this in Phase 2)
- `<all_urls>`: Allows our content script to run on any website (needed because recipe sites are everywhere)

**4. Manifest V3 vs V2**
Manifest V3 is the current standard (as of 2021+). Key differences:
- V3 uses "service workers" instead of persistent background pages (saves memory)
- V3 has stricter Content Security Policy (better security)
- V3 is required for new Chrome extensions; Firefox supports both

---

#### Architecture Overview

```
Browser Extension Architecture (Phase 1)

┌─────────────────────────────────────────────────────────┐
│  manifest.json                                          │
│  • Defines extension configuration                     │
│  • Registers content.js as a content script            │
│  • Specifies it should run on all URLs                 │
└─────────────────────────────────────────────────────────┘
                        │
                        │ (Browser reads manifest and
                        │  knows to inject content.js)
                        ▼
┌─────────────────────────────────────────────────────────┐
│  User visits: allrecipes.com/recipe/12345               │
│                                                         │
│  ┌───────────────────────────────────────────┐         │
│  │  content.js                               │         │
│  │  • Runs automatically when page loads     │         │
│  │  • Searches DOM for button text patterns │         │
│  │  • Clicks button if found                │         │
│  └───────────────────────────────────────────┘         │
│                                                         │
│  Page DOM: <button>Jump to Recipe</button>             │
└─────────────────────────────────────────────────────────┘
```

---

#### manifest.json Deep Dive

**Complete file structure:**
```json
{
  "manifest_version": 3,
  "name": "Just Feed Me",
  "version": "0.1.0",
  "description": "Automatically skip to the recipe by detecting and clicking 'Jump to Recipe' buttons.",

  "icons": {
    "16": "icons/icon-16.png",
    "48": "icons/icon-48.png",
    "128": "icons/icon-128.png"
  },

  "content_scripts": [
    {
      "matches": ["<all_urls>"],
      "js": ["content.js"],
      "run_at": "document_idle"
    }
  ],

  "permissions": [
    "storage"
  ],

  "action": {
    "default_popup": "popup.html",
    "default_icon": {
      "16": "icons/icon-16.png",
      "48": "icons/icon-48.png",
      "128": "icons/icon-128.png"
    }
  }
}
```

**Line-by-line explanation:**

- **`"manifest_version": 3`**: Uses Manifest V3 API (required for modern Chrome)

- **`"name"`, `"version"`, `"description"`**: Basic metadata shown in chrome://extensions

- **`"icons"`**: Three sizes required:
  - 16px: Shown in extension bar
  - 48px: Shown in extensions management page
  - 128px: Shown in Chrome Web Store

- **`"content_scripts"`**: This is the critical part for Phase 1
  - `"matches": ["<all_urls>"]`: Run on every website (we don't know which sites have recipes)
  - `"js": ["content.js"]`: The script file to inject
  - `"run_at": "document_idle"`: Wait until page finishes loading before running our script
    - **Alternatives**: `"document_start"` (runs immediately, but DOM might not be ready) or `"document_end"` (DOM ready but images might still load)
    - **Why "document_idle"**: Perfect balance - DOM is fully ready, and most page JavaScript has run, so the "Jump to Recipe" button definitely exists

- **`"permissions": ["storage"]`**: We're not using this in Phase 1, but we'll need it in Phase 2 for saving toggle state

- **`"action"`**: Defines the extension icon and popup (we'll implement popup in Phase 2)

---

#### content.js Strategy & Design

**The Challenge:**
Recipe websites don't have a standard for their "Jump to Recipe" buttons. They might:
- Use different text: "Jump to Recipe", "Skip to Recipe", "Go to Recipe", etc.
- Use different HTML elements: `<button>`, `<a>`, `<div>` with click handlers
- Use different CSS classes or IDs
- Place them in different locations on the page

**Our Strategy:**
We'll use a **pattern matching approach**:
1. Wait for the page to load (manifest already handles this with `run_at: "document_idle"`)
2. Search through ALL clickable elements on the page
3. Look for text content that matches our patterns (case-insensitive)
4. When we find a match, click it
5. Only click once per page load (to avoid loops or weird behavior)

**Key DOM APIs We'll Use:**
- **`document.querySelectorAll()`**: Gets all elements matching a CSS selector
  - We'll search for common clickable elements: `a`, `button`, `div[role="button"]`
- **`element.textContent`**: Gets the text inside an element
- **`element.click()`**: Programmatically clicks an element (simulates user click)
- **`String.includes()`**: Check if text contains our target phrases

**Why This Approach?**

*Alternatives we could use:*
1. **XPath**: More powerful but harder to read and maintain
2. **Search ALL elements**: Would work but slower (we narrow to clickable elements)
3. **Site-specific selectors**: Would be more accurate but requires maintaining a database of sites

*Our approach is best for MVP because:*
- Simple to understand and debug
- Works on most recipe sites without site-specific code
- Fast enough for good UX (runs in <100ms typically)
- Easy to expand with more patterns later

---

#### content.js Code Walkthrough

**Planned implementation:**

```javascript
// content.js - Automatically click "Jump to Recipe" buttons

(function() {
  'use strict';

  // Prevent multiple executions on the same page
  if (window.hasRunJustFeedMe) {
    return;
  }
  window.hasRunJustFeedMe = true;

  /**
   * Patterns to search for (case-insensitive)
   * We'll add more as we discover variations on recipe sites
   */
  const RECIPE_BUTTON_PATTERNS = [
    'jump to recipe',
    'skip to recipe',
    'go to recipe',
    'recipe'  // More generic fallback
  ];

  /**
   * Finds the first button matching our patterns
   * @returns {Element|null} The button element or null if not found
   */
  function findRecipeButton() {
    // Search in common clickable elements
    const clickableElements = document.querySelectorAll('a, button, [role="button"]');

    console.log(`[Just Feed Me] Scanning ${clickableElements.length} clickable elements...`);

    // Check each element's text content against our patterns
    for (const element of clickableElements) {
      const text = element.textContent.trim().toLowerCase();

      // Check if this element matches any of our patterns
      for (const pattern of RECIPE_BUTTON_PATTERNS) {
        if (text.includes(pattern)) {
          console.log(`[Just Feed Me] Found match: "${element.textContent.trim()}" contains "${pattern}"`);
          return element;
        }
      }
    }

    console.log('[Just Feed Me] No recipe button found on this page');
    return null;
  }

  /**
   * Main execution: find and click the recipe button
   */
  function autoJumpToRecipe() {
    const button = findRecipeButton();

    if (button) {
      console.log('[Just Feed Me] Clicking button:', button);
      button.click();
      console.log('[Just Feed Me] Successfully jumped to recipe!');
    } else {
      console.log('[Just Feed Me] No action taken (no recipe button detected)');
    }
  }

  // Run when content script loads
  autoJumpToRecipe();
})();
```

**Code section explanations:**

**1. IIFE (Immediately Invoked Function Expression)**
```javascript
(function() {
  'use strict';
  // ... code ...
})();
```
- **What**: Wraps our code in a function and immediately runs it
- **Why**: Creates a private scope so our variables don't pollute the page's global namespace
- **What would break**: Without this, if the recipe site has a variable named `RECIPE_BUTTON_PATTERNS`, we'd overwrite theirs or they'd overwrite ours

**2. Execution Guard**
```javascript
if (window.hasRunJustFeedMe) {
  return;
}
window.hasRunJustFeedMe = true;
```
- **What**: Checks if we've already run on this page
- **Why**: Some sites use dynamic routing (single-page apps) that might re-trigger our script
- **What would break**: Without this, we might click the button multiple times or run unnecessarily

**3. Pattern Array**
```javascript
const RECIPE_BUTTON_PATTERNS = [
  'jump to recipe',
  'skip to recipe',
  'go to recipe',
  'recipe'
];
```
- **What**: List of text patterns to search for
- **Why**: Different sites use different wording; we cast a wide net
- **Trade-off**: The 'recipe' pattern is very generic - might match unintended buttons. We can refine this during testing

**4. querySelector vs querySelectorAll**
```javascript
document.querySelectorAll('a, button, [role="button"]')
```
- **What**: Gets ALL matching elements (not just the first)
- **Why**: We need to check text content of each, so we need all of them
- **Alternative**: `getElementsByTagName()` would work but `querySelectorAll()` is more modern and flexible
- **Why these selectors?**
  - `<a>` tags are links (most common for "jump" functionality)
  - `<button>` tags are explicit buttons
  - Elements with `role="button"` act as buttons for accessibility

**5. Console Logging**
```javascript
console.log('[Just Feed Me] ...')
```
- **What**: Logs our actions to the browser console
- **Why**: Critical for debugging - you'll see exactly what the extension is doing
- **Where to find**: Open DevTools (F12) on any recipe page and watch the console

---

#### Testing Strategy

Once we create the placeholder icons and implement content.js, you'll:

1. **Load the extension in Chrome:**
   - Navigate to `chrome://extensions/`
   - Enable "Developer mode" toggle (top right)
   - Click "Load unpacked"
   - Select the `just-feed-me` folder
   - Extension appears in your toolbar

2. **Test on these sites:**
   - **allrecipes.com** - Very common site with "JUMP TO RECIPE" button
   - **budgetbytes.com** - Has "Skip to Recipe" text
   - **google.com** - No recipe button, should do nothing gracefully

3. **What to look for:**
   - Open DevTools (F12) before visiting recipe site
   - Watch Console tab for our `[Just Feed Me]` logs
   - Page should automatically jump to recipe section
   - No errors in console

4. **Debugging tips:**
   - If nothing happens: Check console for our logs
   - If button isn't clicked: Check what text the button actually contains
   - If extension doesn't load: Check for manifest errors in chrome://extensions

---

#### Common Gotchas

**1. Extension doesn't run on local HTML files (`file://` URLs)**
- **Why**: Security restriction in Manifest V3
- **Solution**: Always test on real websites

**2. Button exists but click doesn't work**
- **Why**: Some sites use JavaScript event listeners instead of href links
- **Solution**: `.click()` should trigger these, but we might need to dispatch custom events in rare cases

**3. Page loads slowly and button appears after our script runs**
- **Why**: `document_idle` usually catches this, but some sites lazy-load content
- **Solution**: Phase 4 could add a MutationObserver to watch for buttons appearing

**4. Icons missing warning**
- **What happens**: Chrome shows yellow warning in chrome://extensions
- **Impact**: Extension still works fine, just cosmetic
- **Solution**: Create placeholder icon files (our next todo)

---

#### Checkpoint Questions

Before moving forward, make sure you understand:

**Q1: Why do we use `document.querySelectorAll()` instead of just searching for one specific ID or class?**
- **A**: Because every recipe site structures their buttons differently - we can't rely on consistent IDs/classes across all recipe websites. We need a flexible pattern-matching approach.

**Q2: What's the difference between a content script and regular JavaScript on the page?**
- **A**: Content scripts run in an "isolated world" - they can access the DOM but not the page's JavaScript variables. This prevents conflicts and improves security. The page can't access our extension code, and we can't accidentally interfere with the page's JavaScript.

**Q3: Why do we include `'use strict'` at the top of the function?**
- **A**: Enables strict mode, which catches common coding mistakes and prevents some confusing behaviors (like creating global variables accidentally).

**Q4: Why `"run_at": "document_idle"` instead of `"document_start"`?**
- **A**: `document_idle` ensures the DOM is fully loaded and most page JavaScript has executed, so the "Jump to Recipe" button definitely exists. `document_start` would run too early - the button might not be in the DOM yet.

**Q5: What does `<all_urls>` mean in the matches field?**
- **A**: It means our content script will run on every website. We need this because we don't know in advance which sites are recipe sites. In Phase 2, we'll add toggle controls so users can disable it globally. In Phase 3, we'll add blacklist so users can disable it per-site.

---

#### What's Next (When You Resume)

1. Create placeholder icons (3 simple PNG files: 16x16, 48x48, 128x128)
2. Implement content.js with the code above
3. Load extension in Chrome
4. Test on recipe sites
5. Observe console logs
6. Verify auto-jump functionality works
7. Review and refine before moving to Phase 2

### Phase 2 Learnings
[To be added after Phase 2 completion]

### Phase 3 Learnings
[To be added after Phase 3 completion]

### Phase 4 Learnings
[To be added after Phase 4 completion]

### Phase 5 Learnings
[To be added after Phase 5 completion]

### Phase 6 Learnings
[To be added after Phase 6 completion]

---

## Questions & Clarifications

[Use this space to track questions that come up during development]

- Q: [Your question]
  - A: [Answer after research/discussion]

---

## Resources & Links

[Collect useful resources here as you discover them]

- [Link to useful resource with brief description]
- [Link to useful resource with brief description]

---

## Version History

- **v0.1.0** - Initial project structure and requirements (Phase 0)
- [Future versions will be logged here]