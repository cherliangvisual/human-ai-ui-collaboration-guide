# Human–AI Collaboration for UI Design and Development: Lessons Learned and Pitfalls to Avoid

> **Author:** Cher Liang (梁卓滢)  
> **Edition:** 1.0.0 · 26 September 2026  
> **Purpose:** A shared working reference for users, AI agents, designers, and developers who design or implement websites, desktop tools, dashboards, application workspaces, dialogs, floating panels, and interactive components.  
> **Goal:** Preserve creative freedom in greenfield and zero-to-one design while preventing overlay-based patching, unintended layer-wide changes, coordinate-system mistakes, duplicated CSS, stale state, and partial checks being treated as end-to-end proof.  
> **Applies to:** New visual design, major redesigns, targeted UI repairs, UX interaction changes, visual asset production, and cross-platform adaptation.

---

## 1. What this guide governs—and what it does not

This guide governs:

- Whether implementation remains clean and maintainable.
- Whether the requested interaction has actually been understood.
- Whether changes are being made in the right page and the canonical implementation.
- Whether the real user journey has been verified end to end.
- Whether production assets are kept separate from failed or obsolete variants.

This guide does **not** restrict:

- Visual style or creative direction.
- Color, composition, and brand expression.
- The choice of minimalist, cultural, modern, experimental, or other aesthetics.
- Bold proposals during zero-to-one design.

Rules that prevent implementation mistakes must not be used to reject creativity. Exploration may be open-ended; implementation must remain disciplined.

---

## 2. Classify the task before starting

Different tasks should not be forced through one rigid process.

### 2.1 Greenfield or zero-to-one design

There may be no approved page, screenshot, design system, or existing code. That is normal.

The model should make progress from whatever is available:

- What problem the product solves.
- Who will use it.
- What users do most often.
- How the product should feel.
- Content, brand, device, or technical constraints.

When information is incomplete, ask a small number of consequential questions or state reasonable assumptions. Do not require the user to prepare a complete design specification first.

When the visual directions could differ substantially, prefer asking:

> This is a significant visual decision. Would you like to see a rough visual or wireframe before I modify the production code?

This is a preferred option, not a universal requirement. If the user explicitly wants direct implementation, proceed while stating the design assumptions being made.

For zero-to-one work, the model may propose two or three genuinely different directions, for example:

- Restrained and efficiency-first.
- More expressive, branded, or culturally distinctive.
- Lighter, more contemporary, and optimized for frequent use.

Do not present three structures that are identical apart from minor color changes as if they were distinct concepts.

### 2.2 Major redesign of an existing product

First identify:

- The current approved page and the version that is actually running.
- Which information architecture must remain.
- Which visual decisions may be reconsidered.
- Which data, functions, and established user workflows must not be lost.

Major redesigns also benefit from a visual draft or preview before code changes, because the cost of reversing production changes is higher.

### 2.3 Targeted repair of an existing UI

Examples include:

- Changing one header color.
- Reducing a button or font size.
- Fixing a visible edge, misalignment, or blocked click.
- Adjusting dialog dragging or scroll behavior.

In this mode, strictly control scope. Do not redesign other approved areas as a side effect.

---

## 3. Technical terms are welcome; the user need not be a frontend engineer

The model may use professional terms such as:

- `margin`
- `padding`
- `display: flex`
- `display: grid`
- `position: fixed`
- `position: absolute`
- `overflow`
- `z-index`
- `max-width`
- responsive breakpoints

Keeping the real terms is useful because:

- The user can direct later changes more precisely.
- It is easier to audit what was actually changed.
- The user can gradually build design and development judgment.
- The model cannot hide implementation decisions behind vague language.

However, the model must not require the user to guess values or make uninformed technical choices.

A sound collaboration pattern is:

1. The model proposes a technical approach and recommended parameters.
2. It states the visible effect of that approach.
3. A user who understands can decide directly.
4. If the user asks about a term, the model explains it in plain language using the current page as the example.

For example:

> I recommend changing the card container to `display: flex` and giving the bottom action `margin-top: auto`. This keeps every action aligned to the card bottom even when the cards contain different amounts of text.

If the user asks what `margin-top: auto` means, explain:

> It consumes the remaining space above the button, which automatically pushes the button to the bottom. We do not have to give every card a different manual offset.

The model should not:

- Hide all implementation detail merely to sound simple.
- Dump large amounts of jargon without describing the visible result.
- Give the user multiple technical choices without making a recommendation.
- Stop because the user did not provide exact pixel values.

---

## 4. What the user should decide and what the model should own

### The user is best placed to decide

- Whether the result feels right.
- What emotional or visual impression the page should create.
- Which information matters most.
- Which behaviors fit the user’s real working habits.
- Whether a substantial visual change is acceptable.

### The model is best placed to own

- Translating intent into layout, typography, spacing, hierarchy, and interaction.
- Recommending values for `margin`, `display`, dimensions, and breakpoints.
- Explaining the visual and maintenance tradeoffs of each option.
- Finding the single source of truth in the current codebase.
- Removing rules that have been replaced.
- Running static checks and automated regression tests.

Do not offload technical design decisions onto the user merely because the user is not a frontend engineer.

---

## 5. For substantial visual changes, prefer reviewing a draft first

A draft image, wireframe, or visual preview is especially useful when:

- Creating a new product from scratch.
- Significantly changing information architecture.
- Changing the overall brand, palette, or typographic direction.
- Redesigning navigation, a dashboard, a result page, or a complex floating panel.
- The user can describe the desired feeling but cannot yet imagine the result.
- Editing the implementation would cost more than validating a draft.

The draft stage should confirm:

- Overall composition.
- Information hierarchy.
- Visual character.
- Primary interaction entry points.
- Content density.
- The broad relationship between wide and narrow layouts.

The draft stage does not need to settle:

- Every pixel value.
- Final animation parameters.
- Every error state.
- Every edge case.

After the direction is approved, translate it into maintainable production code.

---

## 6. Five non-negotiable rules when modifying an existing UI

1. **Modify the source; do not cover the outcome.**
2. **Remove the replaced implementation; do not stack patches.**
3. **Define interaction states before styling them.**
4. **Verify the full user journey; do not treat a partial check as proof of completion.**
5. **Preserve approved visual decisions by default and change only the authorized scope.**

These rules primarily apply to changes and repairs in an existing UI. They are not intended to restrict zero-to-one visual exploration.

---

## 7. Do not hide the old design under a new color block or layer

### Incorrect approaches

- Placing a new colored rectangle over an old header and calling it a color change.
- Using a background rectangle to hide unwanted text or edges.
- Using a pseudo-element to conceal an old radius, border, incorrect label, or residual asset.
- Keeping the old DOM and adding a second, similar DOM structure for the new version.
- Adding progressively stronger selectors and `!important` rules until a patch wins.
- Leaving an old event handler active and adding another handler to compensate.

Common consequences include:

- Old colors or pale edges remain visible.
- White seams, rectangular artifacts, or double radii appear.
- A visible close button cannot be clicked.
- An invisible layer blocks controls underneath.
- Later maintainers cannot tell which rule is actually in control.

### Correct approaches

- To change color, edit the original element’s `background`, `color`, or `border`.
- To change size, edit the original layout and box model.
- To remove content, delete the relevant DOM, background image, or state branch.
- To change behavior, remove the old listener and retain one authoritative implementation.
- To replace an asset, keep one unambiguous production file.
- `::before` and `::after` are valid for well-defined background, decoration, or state layers. The problem is not using pseudo-elements; the problem is using them to hide old mistakes, simulate deletion, or permanently patch a production asset.

In one sentence:

> Modify the original thing instead of placing a new thing over it.

---

## 8. For targeted changes, list what changes and what stays fixed

A lightweight format is enough:

```text
Change in this iteration:
- Make the reading-panel header slightly thinner.

Keep unchanged:
- Panel width.
- Body font size.
- Drag boundaries.
- Inside-versus-outside scrolling behavior.
- Close-button behavior.
```

If the user asks only for a thinner header, the model should not simultaneously change:

- Dialog width.
- Body font size.
- Corner radius.
- The shape of the close button.
- How the page opens.

If a related change is technically unavoidable, explain why before proceeding.

---

## 9. Understand page context before implementing the component

An “independent reading panel” does not necessarily mean a separate webpage. Before implementation, establish:

- Whether the underlying page remains visible.
- Whether the new content is navigation, a modal, a drawer, or a floating window.
- Where closing returns the user.
- What a refresh restores.
- Whether product startup should open the full application workspace or an internal result view.

Do not create a second page unless the user asked for navigation.

If the user asks for a panel above the current application, preserve the surrounding application context rather than opening a page that contains only the result.

---

## 10. Floating windows, dialogs, and reading panels need a complete interaction model

It is not enough for the component to appear.

### Opening

- What opens it?
- Is the underlying page position preserved?
- What are the default size and position?
- Does scroll focus initially belong inside or outside the panel?

### Closing

- Is the close control always visible?
- Is its hit target large enough?
- Is it blocked by drag logic or a transparent layer?
- Should Escape or background click close it? Do not add these behaviors without a requirement.

### Dragging

- Which area is the drag handle?
- The close control and other buttons must not accidentally initiate dragging.
- Is movement constrained to the component container, the application canvas, or the full browser viewport?
- May part of the panel move below the viewport?
- What remains visible so the user can retrieve it?
- Do not add resizing when the user requested dragging only.

### Scrolling

- Clicking inside the panel should scroll its content when that is the intended focus.
- Clicking outside may return scroll focus to the page when required.
- Nested scroll areas need distinct responsibilities.
- Do not simulate content scrolling by moving the entire floating window.

---

## 11. Align cards and lists through structure, not manual nudging

When adjacent cards contain different amounts of text, their bottom actions should not drift with the content.

One common structure is:

```css
.card {
  display: flex;
  flex-direction: column;
}

.card-action {
  margin-top: auto;
}
```

The remaining space above the action is absorbed automatically, keeping each action aligned to the bottom.

Do not:

- Give each card a different manual `margin-top`.
- Use blank lines or transparent text as spacers.
- Test alignment with only one fixed set of copy.

---

## 12. Model the states of data-driven UI before styling it

Uploads, material boxes, collections, task results, and account connections often include:

```text
initial empty state
data present
multiple items
processing
success
failure
state restored after refreshing the page
state restored after restarting the application
remove one item
clear all items
connection lost
previous result retained
```

The model should map these states proactively. The user should not have to enumerate them in technical language.

For each state, establish:

- What is shown.
- Which actions are available.
- Whether the source of truth is browser memory, a server, or a local file.
- What is preserved on failure.
- What is restored after refresh.

---

## 13. Deleting and clearing require end-to-end verification

An end-to-end acceptance check should cover:

```text
click the control
→ event handler runs
→ request method and URL are correct
→ server receives the request
→ persistent storage changes
→ server returns the new state
→ frontend adopts the returned state
→ DOM re-renders immediately
→ refresh still shows the correct state
```

None of the following alone proves that the UI is complete:

- A storage-layer unit test passes.
- The endpoint works from the command line.
- A backend file changed.
- The console contains no error.

The real control in the real page must be exercised.

---

## 14. A gray button is not necessarily a CSS problem

When an action cannot be clicked, check in this order:

1. Does the DOM actually contain `disabled`?
2. Which state variable controls it?
3. Is that state locally inferred or supplied by the server?
4. Is SSE, WebSocket, or polling delayed?
5. Is a transparent layer intercepting pointer input?
6. Only then inspect the button color and CSS.

Visual state should reflect business state. Do not treat “it looks gray” as proof of a styling root cause.

---

## 15. Separate success, error, and running states

- Running state: show the real stage and elapsed time.
- Error: remain in the current task workspace, explain the cause, and offer recovery or retry.
- Export success: use a short-lived notification that disappears after a few seconds.
- Page navigation: clear local success notifications.
- Previous successful result: store it separately so the current error does not overwrite it.

Do not let an “exported file” message remain visible across unrelated feature pages.

---

## 16. When refresh shows no change, investigate in this order

Do not immediately add another CSS layer.

Check:

1. Is the current page the complete product or an internal result view?
2. Does the URL belong to the latest running instance?
3. Is the service process using the workspace that was just edited?
4. Is the current service serving the static assets?
5. Is the browser still connected to an old port or session?
6. Has the DOM actually changed?
7. Has the CSS file actually loaded?
8. Only then investigate browser caching.

Do not keep increasing CSS specificity to “fight the cache.”

---

## 17. Visual asset management

### Reference priority

A project may contain an approved page, old screenshots, annotated screenshots, source assets, and AI drafts at the same time. When they conflict, use this default priority:

1. The latest result or production asset explicitly approved by the user.
2. The approved state of the currently running product.
3. The current design specification and lock list.
4. An annotated screenshot supplied for the current issue.
5. Original source material, used only to understand content, structure, and style.
6. AI-generated drafts, which are proposals and must not overwrite the approved baseline.

If high-priority references conflict with one another, surface the conflict and request a decision. Do not invent an unapproved compromise.

### Production assets

- Keep one production file for each visual role.
- Use stable names rather than `final-v12-final2`.
- Production code should reference production assets only.

### Design references

- Keep source images, drafts, and licensing evidence in a separate reference directory.
- Mark them clearly as non-production assets.

### QA and test assets

- Store screenshots, comparisons, and demos in a QA or test directory.
- Do not mix them with production assets.
- Delete obsolete failure screenshots that have no regression value. If one must remain, label it explicitly as a historical failure example.

### Visual lock records

For an important visual decision approved by the user, consider recording:

- Production asset or component name.
- Where it is used and what it does.
- Rules for default, hover, expanded, and disabled states.
- Properties that may still be adjusted.
- Properties that must not be changed incidentally.
- Target viewport or responsive behavior.
- Date of human approval.
- Corresponding Git commit, tag, or recoverable version.

A lock does not forbid future redesign. It means the redesign should be presented as a new proposal rather than quietly introduced during feature work.

### Prohibited practices

- Accumulating numbered experiments in the production asset directory.
- Referencing files directly from Downloads or temporary generation directories.
- Creating a new filename merely to bypass browser cache.
- Shipping unused historical visual assets in a release package.

---

## 18. Standard workflows

### Zero-to-one

1. Understand the product, its users, and the primary jobs to be done.
2. Ask necessary questions or state reasonable assumptions.
3. Offer two or three meaningfully different visual directions.
4. For major decisions, ask whether the user wants to see a visual draft first.
5. Implement production code after a direction is approved.
6. Complete states, responsiveness, and accessibility.

### Redesign or repair of an existing UI

1. Open the real, complete product.
2. Confirm the active source tree and running instance.
3. Restate what changes and what remains fixed.
4. Locate the authoritative DOM, CSS, state, and event source.
5. Modify the source and remove the replaced implementation.
6. Search for old assets, duplicate selectors, and covering layers.
7. Verify the real interaction journey.
8. Return subjective visual judgment to the user.

---

## 19. Definition of done

Select the checks that apply to the task. Do not execute every item mechanically.

- The requested visual outcome is present.
- Unauthorized areas did not change unexpectedly.
- There are no leftover overlay blocks, visible seams, transparent hit blockers, or doubled corner radii.
- There is no duplicate DOM, CSS, or event logic.
- Buttons, closing, dragging, and scrolling work in the actual product.
- Data operations work from click through persistence.
- Refresh or restart produces the required state.
- The production asset directory contains no experiment variants.
- Automated tests and human visual judgment have each served their proper role.

A zero-to-one concept draft does not need to satisfy every engineering acceptance criterion. Complete those checks when the design enters production implementation.

---

## 20. Know when to stop adding patches

Stop and locate the root cause when:

- The same visible seam remains after two attempts.
- A visible close control still cannot be clicked.
- Refresh shows no change at all.
- The backend succeeds but the frontend remains unchanged.
- A third patch layer is becoming necessary to fix one issue.
- You cannot confirm that the user is viewing the current instance.

At that point, report:

```text
Confirmed observation:
Unconfirmed link in the chain:
Most likely root cause:
Smallest next verification:
What requires human judgment:
```

Do not consume time and tokens through repeated guessing.

### 20.1 Distinguish structural problems from aesthetic problems

The following are usually structural or implementation failures:

- A contour does not close.
- An element attaches to the wrong location or floats in space.
- A state transition visibly jumps.
- A hit target is blocked.
- Coordinates drift after scrolling.
- The frontend still displays old data after a clear operation.

Do not hide these problems by making something fainter, blurrier, more shadowed, or differently colored. Establish structural correctness before debating aesthetics.

### 20.2 Use testable hypotheses instead of continuous visual nudging

For example:

```text
Observation: A white fringe appears on a dark background.
Hypothesis: Transparent pixels still contain white RGB values.
Change in this test only: Disable CSS filters and render the asset at native size.
Pass criterion: Determine whether the fringe remains.
```

Testing one main root cause at a time does **not** mean that creative exploration may change only one visual variable. This method is for diagnosis and precision repair.

---

## 21. Ready-to-use prompts

### General version

```text
Read “Human–AI Collaboration for UI Design and Development: Lessons Learned and Pitfalls to Avoid” in full. Decide whether this task is zero-to-one design, a major redesign, or a targeted repair, and use the appropriate workflow.

You may use professional terms such as margin, display, position, and overflow. Explain the visible effect of the approach you recommend. If I ask about a term, explain it in plain language using the current page; do not require me to guess technical parameters I do not understand.

If this is a substantial visual change, ask whether I would like to review a visual draft before you modify production code. The safeguards constrain implementation quality, not visual creativity.

If this task involves transparent assets, multi-state animation, pixel-level repair, pointer-following effects, complex floating panels, or multi-viewport positioning, enable only the relevant high-risk modules from the guide. Do not apply every module mechanically to an ordinary page.
```

### Zero-to-one version

```text
This is a zero-to-one visual design task and there may be no approved page or screenshot yet. Use the product goal, users, and context to ask only the necessary questions or state reasonable assumptions. Offer two or three genuinely different visual directions. Do not require a complete design specification before making progress.
```

### Existing-UI version

```text
Inspect the real current page and its source first. Change only the requested scope by editing the authoritative DOM, CSS, state, and event implementation, and remove what the new implementation replaces. Do not use color blocks, pseudo-elements, duplicate DOM, or additional layers to hide the old design.

Before editing, restate what will change, what will remain fixed, and the expected interaction. Verify the result in the complete product rather than opening only a component or isolated result page.
```

---

## 22. Optional brief for a single change

The user may fill only the parts they know. Blank fields should prompt recommendations from the model, not block the task.

```text
[Product / page]

[What I want the result to feel like or accomplish]

[What I want to change]

[What I definitely do not want changed]

[Existing screenshot or reference, optional]

[Would I like to see a draft first? Optional]

[Interaction I care about most]

[Devices or environments to check, optional]
```

The model should add:

```text
[Recommended implementation]

[Key technical parameters and their visible effects]

[Recommended option]

[Possible alternatives]

[Acceptance method]
```

---

## 23. Advanced safeguards for high-risk visual work

Enable these modules only when the relevant risk exists. Ordinary text pages, simple forms, and low-risk style adjustments do not need every check.

### 23.1 Layers and property scope

Use this module for opacity, filters, scaling, blur, texture, backgrounds, and compound components.

Separate at least these layers:

| Layer | Common objects | Common properties |
|---|---|---|
| Positioning layer | Entire floating window or tool | `top`, `left`, `right`, `bottom`, responsive position |
| Object layer | Illustration, product image, logo | Dimensions, crop, object alpha |
| Background layer | Card color, glass, paper, gradient | Background color, background opacity, blur, texture |
| Content layer | Heading, body, controls, list | Font size, line height, spacing, scrolling |
| Effect layer | Smoke, particles, shadow, glow | Blend, opacity, animation, anchor |

Before changing a property, identify which layer owns it. Setting `opacity` on a shared parent fades all of its children. If only the background should be translucent, use a translucent background color or a dedicated background layer with a clear responsibility.

“Make it larger” also needs scope: the complete component, the primary object, or one effect. If a label or decoration extends outside the object, do not shrink the object merely to fit everything into one crop.

### 23.2 Coordinate spaces and annotation mapping

Use this module for movement, cropping, pixel-level repair, annotated screenshots, and local alignment.

Distinguish:

- Browser viewport coordinates.
- Document/page coordinates.
- Application-shell or component-local coordinates.
- Position inside a background image.
- Source-image pixel coordinates.

“Move it left” may mean moving the whole component, moving an image inside a fixed container, shifting the background crop, or moving one local layer. For high-risk changes, restate the object and coordinate space first.

An arrow drawn on a screenshot uses screenshot coordinates. The production asset may already be scaled, cropped, and offset. For precision repairs:

1. Identify the endpoints or exact target region.
2. If necessary, produce a small preview with numbered anchors.
3. Convert screenshot coordinates to source-asset coordinates.
4. Edit the canonical production asset instead of permanently drawing a corrective line in the webpage.
5. Review both a magnified image and the actual display size.

### 23.3 Multi-state assets and animation anchors

Use this module for default/hover, open/closed, expanded/collapsed, active/inactive, or illuminated/unilluminated state assets.

States should normally preserve:

- The same canvas dimensions.
- The same object scale.
- The same baseline or specified anchor.
- The same contours and lighting that are not meant to change.
- Changes only in the parts authorized by the design.

Onion-skin overlays and difference blending can reveal object drift. Labels, smoke, glow, and other secondary layers should remain independently controlled and should not force the primary object to change scale between states.

Also test rapid repeated triggering for accumulated animation instances, duplicated layers, or residual intermediate frames.

### 23.4 Transparent assets, alpha, and white fringes

Use this module for PNG, WebP, cutouts, translucent illustration, and soft-edged assets.

An asset that “looks transparent” may not have a real alpha channel. A checkerboard can be baked into the image. Test on:

- A dark solid background.
- A light solid background.
- A realistic, visually complex page background.

When a white fringe or rectangular artifact appears:

1. Hide the primary object and effect layers separately.
2. Disable CSS filters, shadows, blend modes, and whole-image opacity.
3. Render at native size to eliminate scaling interpolation as a variable.
4. Confirm that the image actually contains alpha.
5. Inspect whether transparent pixels retain RGB values from the old background.

Do not repair a white fringe by lowering the entire image’s `opacity`. That only fades the correct object and the defect together.

### 23.5 Attachment and contact geometry

Use this module for connector lines, liquid, light beams, smoke, decorative strokes, and attached objects.

Opacity, blur, and glow cannot substitute for a correct contact point. First establish the start, end, and interface with a clear, high-contrast view; then restore the intended final effect.

Check for floating gaps, intersections, attachment to the wrong contour, and drift after scaling.

### 23.6 Multiple viewports, display scaling, and responsive evidence

Distinguish:

- Browser viewport size.
- Application-shell design size.
- Component-internal canvas size.
- Browser zoom and operating-system display scaling.

When supplying or comparing screenshots, record the viewport, scroll position, browser zoom, and whether the environment is an embedded or external browser whenever relevant. Do not overturn a layout based on one viewport screenshot alone.

Choose checks that fit the target product, such as a large desktop, a typical laptop, a narrow window, 125% or 150% display scaling, and high DPI. Not every project must test every environment mechanically.

Scrolling needs a named owner: the browser, application content area, floating panel, or internal list. Do not let multiple nested layers compete for the wheel.

### 23.7 Pointer-following effects, particles, lighting, and sound

Enable this module only when the project uses these effects.

A pointer-following layer should generally:

- Stay out of document layout.
- Avoid changing document dimensions or creating scrollbars.
- Use `pointer-events: none` so it does not block real controls.
- Bound particle count, lifetime, and memory use.
- Be tested during scrolling, zooming, and at viewport edges.

Do not unintentionally mix viewport, page, and component-local pointer coordinates. When an approved demo already exists, record the important algorithm and parameter values and verify consistency in the real product instead of retuning everything by feel.

Text fields, editors, selectors, disabled controls, and high-frequency actions generally should not play decorative sounds. Also respect mute and reduced-motion preferences.

### 23.8 Text, texture, and button hierarchy

Paper texture, grain, and glass effects belong to background or decoration layers. They should not make text embossed, blurry, or translucent.

Establish a typographic hierarchy across page title, primary guidance, secondary guidance, controls, status text, and metadata. Avoid resizing individual elements repeatedly without a coherent scale.

Button visual weight should reflect task importance, while visually small controls still need usable hit targets. Copy replacement should use the final approved wording and must not leave the old sentence elsewhere in the interface.

### 23.9 Automated checks versus human acceptance

Automation is well suited to checking:

- DOM, dimensions, and resource references.
- Whether state transitions occur.
- Which layer owns scrolling.
- Missing files and duplicate selectors.
- Requests, persistence, and state restoration after refresh.

Humans are better suited to judging:

- Whether the visual language is coherent.
- Whether visual balance, hierarchy, and reading rhythm feel coherent.
- Whether translucency and motion feel natural.
- Whether font size, line spacing, and reading effort are comfortable.
- Whether sound is intrusive.
- Whether the real browser experience obstructs the task.

Automated screenshots cannot replace all aesthetic judgment. When a human says something feels wrong, do not immediately start blind visual tweaking; first decide whether the problem is structural or aesthetic.

### 23.10 Risky changes and version rollback

Before re-cutting assets, restructuring multi-state imagery, refactoring responsiveness, or changing the overall layout, create a recoverable Git commit or version point when appropriate.

Do not move or overwrite a published tag. Create a new commit or version for corrections. Do not keep obsolete experiments in the production asset directory as “insurance”; use Git history or an explicitly separated reference archive.

---

## 24. Final reminders

```text
Visual creativity may be open-ended; implementation must not rely on concealment or stacked patches.

Professional terminology is welcome, but the model owns the responsibility to recommend and explain.

The user does not need to understand margin, display, or exact pixel values in advance. Use the real terms; when the user asks, explain them in plain language using the current design.

Zero-to-one work does not require an approved page or screenshot that does not yet exist. For major changes, prefer offering a draft first, while allowing the user to choose direct implementation.

When modifying an existing UI, if the old implementation still exists and the new one merely covers it, the work is not complete.

If the backend passes but the real control does not, the work is not complete.

If only an isolated component page was opened instead of the complete product, the work is not complete.
```
