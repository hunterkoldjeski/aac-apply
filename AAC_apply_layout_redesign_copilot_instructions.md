# AAC Apply Page — Layout Redesign Instructions (Single Column, Card-Per-Section)
## Objective
Refactor the existing `index.html` into a **single-column** layout where **each section is its own card** (visual separation), while preserving **all attribution + Typeform functionality**.

### Required reading order (top → bottom)
1. Header card
2. Purpose
3. Common Conditions
4. Youth Pastors
5. What You Receive
6. Application
7. How It Works
8. Support

## Hard constraints (DO NOT CHANGE)
### Attribution + Typeform
- Do NOT change JavaScript logic, variables, or functions.
- Do NOT change the attribution system (capture, persistence, injection).
- Do NOT change the Typeform base URL (`TYPEFORM_BASE`) or `PRIMARY_AFF_PARAM` (`affiliate_code`).
- Do NOT change the iframe ID or the fallback link ID:
  - `typeformFrame`
  - `fallbackLink`
  - `refMeta`
- Do NOT change the scroll target:
  - CTA button `ctaApply` must still scroll to element with `id="apply"`.

### IDs that must remain exactly as-is
- `ctaApply`
- `apply`
- `typeformFrame`
- `fallbackLink`
- `refMeta`
- `y`

### Styling
- You may change CSS for layout ONLY (single column + card spacing).
- Do NOT alter theme colors, fonts, gradients, button styles, or overall visual system unless explicitly required by the layout change.
- The page should remain Stripe-safe and formal in tone.

---

# Implementation plan (safe procedure)
1. Make a backup commit of the current `index.html`.
2. Apply CSS layout changes first (so structure changes are easier to validate).
3. Refactor the HTML layout (move sections into their own `.card` blocks).
4. Validate functionality (scroll, Typeform, fallback link, attribution).

---

# Step 1 — CSS changes (layout only)
## A) Convert the two-column main grid to a single column stack
Find the existing `main{ ... }` block and replace it with:

```css
main{
  margin-top: 16px;
  display: flex;
  flex-direction: column;
  gap: 14px;
}
```

### Important
- Keep the `@media` block (if present), but it will become unnecessary. You may delete the `@media (max-width: 920px){ main{...} }` rule or leave it; it will be harmless if it matches the same structure.

## B) Ensure the single column width matches the current overall layout
- **Do not change** `.wrap{ max-width: var(--max); ... }`
- This preserves the same overall page width as today.

## C) Typeform iframe sizing (allowed adjustment)
Because the Application card will sit in the single column, the iframe may need a bit more height. Adjust ONLY if needed.

Find the `iframe{ height: ... }` rule and set to:

```css
iframe{
  display:block;
  width:100%;
  height: 860px; /* increased for single-column readability */
  border:0;
  background: transparent;
}
```

Keep the mobile override if you want; consider:

```css
@media (max-width: 520px){
  iframe{ height: 920px; }
}
```

Do not change any iframe attributes in HTML.

---

# Step 2 — HTML structure changes (card-per-section)
## A) Replace the current `<main>...</main>` content
### Current (high-level)
- One left column card (`<section class="card" id="overview">`) containing multiple sections
- One right column card (`<aside class="card" id="apply">`) containing Application + How It Works + Support

### Target (single column)
`<main>` should contain **multiple** `.card` blocks in the exact order below.

## B) New `<main>` skeleton (paste and then fill)
Replace the entire content inside `<main> ... </main>` with the following structure.

IMPORTANT:
- Keep `id="apply"` on the Application card.
- Keep all existing Typeform embed markup inside the Application card.

```html
<main>
  <!-- 1) Purpose -->
  <section class="card" id="purpose">
    <span class="label">Purpose</span>
    <h2>Why This Exists</h2>
    <!-- keep your Youth Minister copy paragraphs here -->
  </section>

  <!-- 2) Common Conditions -->
  <section class="card" id="conditions">
    <span class="label">Common Conditions</span>
    <h2>What Youth Ministers Are Experiencing</h2>
    <!-- keep the grid2 + notice blocks here -->
  </section>

  <!-- 3) Youth Pastors -->
  <section class="card" id="youthpastors">
    <span class="label">Youth Pastors</span>
    <h2>A Direct Word to Youth Ministry Leadership</h2>
    <!-- keep the youth pastor-specific copy here -->
  </section>

  <!-- 4) What You Receive -->
  <section class="card" id="receive">
    <span class="label">What You Receive</span>
    <h2>The Bridge: From Event-Dependence to Durable Formation</h2>
    <!-- keep bridge paragraphs + UL here -->
  </section>

  <!-- 5) Application (must keep id="apply") -->
  <section class="card" id="apply">
    <span class="label">Application</span>
    <h2>Begin Application</h2>
    <p class="small" style="margin-bottom:12px;">
      The form is embedded below. If it does not load, refresh once or use the fallback link.
    </p>

    <!-- KEEP this embed shell exactly as-is (do not change IDs) -->
    <div class="embedShell">
      <div class="embedHeader">
        <div class="left">
          <div class="title">AAC Application Form</div>
          <div class="meta" id="refMeta">Referral: none detected</div>
        </div>
        <a class="btn secondary" id="fallbackLink" href="#" target="_blank" rel="noopener">Open in new tab</a>
      </div>
      <iframe
        id="typeformFrame"
        title="AAC Application Typeform"
        loading="lazy"
        allow="camera; microphone; autoplay; encrypted-media;"
        src=""
      ></iframe>
    </div>
  </section>

  <!-- 6) How It Works -->
  <section class="card" id="how">
    <span class="label">How It Works</span>
    <h2>Application, Review, and Membership Environment</h2>
    <!-- keep expanded how-it-works paragraphs + UL + small line here -->
  </section>

  <!-- 7) Support -->
  <section class="card" id="support">
    <span class="label">Support</span>
    <h2>Support</h2>
    <p><strong>Email:</strong> <a href="mailto:office@joinaacwarfare.com">office@joinaacwarfare.com</a></p>
    <p class="small">
      For technical issues related to the application form, include a screenshot and the URL you used to access this page.
    </p>
  </section>
</main>
```

## C) What happens to the old cards?
- Delete the old combined left column card (`id="overview"`) once its content has been redistributed into the new cards.
- Delete the old combined right column card (the `<aside class="card" id="apply">`) once the Application embed has been moved into the new Application card.
- DO NOT delete the global `<header>...</header>` card at the top of the page. The header remains as the first “card.”

---

# Step 3 — Ensure the CTA scroll still works
In the header, this button must remain unchanged:

```html
<button class="btn primary" id="ctaApply" type="button">Begin Application</button>
```

The JavaScript scrolls to:
- `document.getElementById("apply")`

Therefore:
- the Application card MUST keep `id="apply"`.

---

# Step 4 — Testing checklist (must pass)
1. Load `https://apply.joinaacwarfare.com`:
   - No console errors.
2. Click “Begin Application”:
   - Smooth scroll lands at the Application card.
3. Confirm Typeform loads inside the iframe.
4. Confirm “Open in new tab” works and opens the same form URL.
5. Confirm referral capture:
   - Visit `https://apply.joinaacwarfare.com/?affiliate_code=test123`
   - Confirm the meta line updates from “none detected” to a masked value.
   - Submit the form; confirm Typeform hidden field captured `test123`.

---

# Notes for Copilot / IDE agent
- Perform the refactor mechanically: move existing content blocks into new cards without rewording.
- Do not rename any IDs listed in constraints.
- Do not change the `<script>` section.
- Keep the embed shell HTML identical (IDs, structure, attributes).
- Adjust only the iframe height in CSS if necessary.

End of instructions.
