# AAC Apply Page — Youth Minister ICP Copy Revamp
## Scope
You are editing ONLY the on-page COPY (text content) in `index.html` for the AAC apply page hosted on GitHub Pages.

### Hard constraints (DO NOT CHANGE)
- Do NOT change any JavaScript logic, variables, or functions.
- Do NOT change the attribution system (capture, persistence, injection).
- Do NOT change the Typeform embed URL base, iframe element, or embed-shell structure.
- Do NOT change element IDs used by JavaScript: `ctaApply`, `apply`, `typeformFrame`, `fallbackLink`, `refMeta`, `y`.
- Do NOT change anchors/structure that scrolling depends on: CTA button scrolls to `#apply`.
- Do NOT change CSS, layout, or section ordering beyond the specified copy edits.
- Do NOT alter any URL parameter names. `affiliate_code` must remain exactly as-is.

## What to change
Replace copy to target the specific ICP: **Youth Minister / Youth Pastor**, using the AAC Youth Ministry Formation System messaging as primary source and the Youth Minister ICP doc as context.

### Section order constraints
- Keep the current layout and placement:
  - Left column: Purpose → Common Conditions → What You Receive → Youth Pastors
  - Right column (below Typeform): How It Works → Support
- Do NOT reintroduce any “Referral code handling” copy section on the left.

---

# Step-by-step edit plan (safe procedure)
1. Open `index.html`.
2. Use “Find” to locate each section by its **label text** and **H2** header.
3. Replace ONLY the inner text content between existing tags, unless instructed to replace the entire block.
4. Confirm after edits:
   - Page loads without console errors.
   - “Begin Application” button still scrolls to the embedded Typeform section.
   - The Typeform still loads.
   - The fallback link still opens the Typeform in a new tab.
   - Affiliate attribution still works by testing:
     - `https://apply.joinaacwarfare.com/?affiliate_code=test123`
     - Submit the form; confirm hidden field captured `test123`.

---

# Copy replacements (paste exactly)

## A) Header copy (inside `<header>...</header>`)
### Replace H1 text
Current:
- `Alliance Advancing Christendom`
Replace with:
- `AAC Youth Ministry Formation System`

### Replace subheadline paragraph `<p class="sub">...</p>`
Replace entire paragraph content with:
A structured formation and operating system built for Youth Ministers who carry real responsibility with limited authority—designed to replace event-dependence with rhythm, responsibility, and continuity.

### Keep kicker, CTA button labels, and small disclaimer as-is unless you want them to match exactly:
- Kicker stays: `Application Portal`
- Buttons stay: `Begin Application` / `Contact`
- Small disclaimer stays: `Submission does not imply acceptance...`

---

## B) Left column — Purpose section (inside `<section class="card" id="overview">`)
Locate:
- `<span class="label">Purpose</span>`
- `<h2>Why This Exists</h2>`
Replace the following paragraphs under this H2 with:

1) Most youth ministries are not failing because of bad intentions, weak theology, or lack of effort. They struggle because the structure underneath them cannot carry the weight the role requires.

2) When formation depends on energy, personality, or novelty, it resets every semester. When expectations are vague, discipline feels personal. When leadership is informal, burnout becomes predictable.

3) This system exists to address those structural problems directly—without asking you to overhaul your church, fight unnecessary battles, or become someone you are not.

---

## C) Left column — Common Conditions section
Locate:
- `<span class="label">Common Conditions</span>`
- `<h2>What Leaders Are Experiencing</h2>`
Replace the H2 with:
- `What Youth Ministers Are Experiencing`

Then replace the four `.notice` boxes with the following exact HTML (replace only the content inside each notice block; keep the surrounding `<div class="notice">` structure unchanged):

1) Title line:
`<strong>Formation has been replaced by programming.</strong><br/>`
Body:
`Students attend, but responsibility is not cultivated. Emotional engagement is mistaken for growth, and the ministry resets as soon as momentum fades.`

2) Title line:
`<strong>Authority without structure.</strong><br/>`
Body:
`You are held accountable like a spiritual authority but treated like a program manager. Standards feel risky, correction feels political, and discipline becomes reactive rather than institutional.`

3) Title line:
`<strong>A fragile volunteer and student bench.</strong><br/>`
Body:
`Volunteers are recruited relationally but rarely formed structurally. Student leadership is informal or nonexistent. When relationships change, continuity collapses.`

4) Title line:
`<strong>Burnout driven by personal dependency.</strong><br/>`
Body:
`Rest feels irresponsible because the system is fragile. Your absence exposes how much depends on you—emotionally, operationally, and spiritually.`

---

## D) Left column — What You Receive (Bridge) section
Locate:
- `<span class="label">What You Receive</span>`
Replace the H2 with:
- `The Bridge: From Event-Dependence to Durable Formation`

Replace the paragraphs and list under this section with:

Paragraph 1:
This membership provides a bridge between sincerity and structure—between a youth ministry that relies on energy and a youth ministry that compounds year over year through responsibility, discipline, and continuity.

Paragraph 2:
The system is built for the constraints Youth Ministers actually face: limited authority, volunteer instability, parental politics, and institutional ambiguity. It does not require a church-wide reorganization, a bigger budget, or constant conflict.

Paragraph 3:
It replaces vague expectations with clear standards; replaces one-off events with repeatable rhythms; and creates a leadership bench that survives graduation cycles and leadership transitions.

Replace the `<ul>...</ul>` contents with the following list items (keep the `<ul>` element itself):

- `<li><strong>Operating doctrine for youth ministry:</strong> a clear articulation of purpose, expectations, boundaries, and non-negotiables—so leadership is principled, not improvised.</li>`
- `<li><strong>Student responsibility pathway:</strong> defined expectations by age and maturity—so students move from attendance to service to leadership in a visible progression.</li>`
- `<li><strong>Named student leadership roles:</strong> specific roles that train students to carry weight and lead peers through responsibility, not popularity.</li>`
- `<li><strong>Volunteer structure and role clarity:</strong> expectations that reduce churn, burnout, and inconsistency—so volunteers stay longer and lead better.</li>`
- `<li><strong>Men’s formation track:</strong> a structured pathway focused on discipline, service, and accountability—built to engage the most disengaged demographic.</li>`
- `<li><strong>Weekly and monthly rhythm:</strong> a cadence that replaces constant event-building and allows formation to compound instead of resetting.</li>`

Then replace the small concluding line (a `<p class="small">` if present, or add one directly after the list) with:
This is not a curriculum. It is not a content library. It is an operating system that makes formation possible.

---

## E) Left column — Youth Pastors section
Locate:
- `<span class="label">Youth Pastors</span>`
Replace H2 with:
- `A Direct Word to Youth Ministry Leadership`

Replace the paragraphs under that H2 with:

1) You are operating at the fault line—between church leadership and parents, between institutional expectations and cultural reality, and between a spiritual calling and operational fragility.

2) You are expected to innovate, retain, disciple, protect, and stabilize—often simultaneously—while being discouraged from introducing the structure that would actually make those outcomes sustainable.

3) This system gives you language, structure, and a disciplined pathway you can implement inside reality: expectations that depersonalize discipline, roles that create a leadership bench, and rhythms that reduce dependence on you as the ministry’s engine.

Small line (`<p class="small">`):
If you want a ministry that survives your absence, retains students beyond graduation, and forms responsibility rather than chasing novelty, you are the intended applicant.

---

## F) Right column — How It Works section (must be below the embed)
Locate in the right column after the iframe embed shell:
- `<span class="label">How It Works</span>`
Replace H2 with:
- `Application, Review, and Membership Environment`

Replace the paragraphs and list with:

Paragraph 1:
This is a limited-capacity, application-based membership. The objective is quality, trust, and seriousness—not scale at the expense of formation.

Paragraph 2:
After submission, applications are reviewed for alignment: responsibility level, readiness to uphold expectations, and willingness to participate meaningfully. Submission does not imply acceptance.

Paragraph 3:
If accepted, members enter an active environment designed around implementation—not passive consumption. The system is intended to be adapted to your constraints, not copied blindly.

Replace the `<ul>...</ul>` contents with:
- `<li><strong>Participation expectations:</strong> engagement with operating doctrine, discussion, and implementation prompts—so the system produces compounding change, not temporary inspiration.</li>`
- `<li><strong>Training and instruction:</strong> periodic training focused on youth ministry structure, leadership bench building, discipline norms, and rhythm design.</li>`
- `<li><strong>Network proximity:</strong> access to other Youth Ministers facing similar constraints—sharing tested structures, language that works with parents, and implementation patterns.</li>`
- `<li><strong>Capacity discipline:</strong> controlled growth to preserve signal, accountability, and the seriousness required for real formation work.</li>`

Small line (`<p class="small">`):
Most visible shifts occur within 60–90 days simply because confusion decreases and expectations become clear.

---

## G) Right column — Support section (must be below How It Works)
Do not change the support email address or link.
Keep as:
- `office@joinaacwarfare.com`

Only ensure the Support section appears directly after How It Works.

---

# Validation checklist
- No HTML validation errors (basic).
- JS still finds required IDs: `ctaApply`, `apply`, `typeformFrame`, `fallbackLink`, `refMeta`, `y`.
- Typeform loads in iframe.
- Fallback “Open in new tab” link works.
- Affiliate attribution works with `?affiliate_code=test123`.

End of instructions.
