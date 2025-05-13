<h1>
  <span class="headline">Pre-Selenium: CSS Selectors and Attributes</span>
  <span class="subhead">Instructor Guide</span>
</h1>

## Basic CSS Selectors

**How to best deliver this microlesson:**

- Encourage learners to “think like the browser” and to verbally explain, in their own words, what each selector accomplishes.
- When facilitating the hands-on selector exercise, circulate (or check in online) to support learners in using DevTools and help clarify the difference between element, class, and id selectors.
- Use global analogies—such as filters on e-commerce websites or labels on items in an inventory—to ground discussions about selectors.
- Emphasize real-time feedback: let learners see immediately in DevTools what their input does.

**Knowledge check answers:**

- First question: C. `#submit-btn` (IDs should be unique, so this selector matches a single element)

## HTML Attributes in Selectors

### How to best deliver this microlesson

- Encourage learners to explain in their own words what attributes do and how selectors can be layered for precision.
- If presenting live, demonstrate selector testing in DevTools and narrate each step and its outcome.
- Highlight the value of global, non-culture-bound analogies—like spreadsheets and address systems—to clarify attribute selectors for all learners.
- Emphasize that the attribute scavenger hunt is not just about finding the right selector syntax, but developing a habit of experimenting, analyzing, and reasoning about selector outcomes in both DevTools and Selenium scripts.
- If teaching remotely, share your screen while demonstrating selector entry and element highlighting; ask learners to post screenshots or selector results in your collaborative platform for feedback and discussion.
- Use inclusive, neutral names and data throughout, and avoid region-specific or idiomatic examples.

### Knowledge check answers

- First question: B. `[data-analytics^="promo"]` (the "^=" operator matches attribute values that _start with_ the provided value).
- Second question: D. Input fields whose name ends with "password".

---

## Advanced Selector Combinations

**How to best deliver this microlesson:**

- Connect new concepts to the previous lessons: reinforce how compound and combinator selectors build on learners’ understanding of element, class, and attribute selectors.
- Use a live demo in Chrome DevTools, narrating each step as selectors are tested, and highlight the effect of changing HTML structure on selector results.
- Draw analogies between selectors and real-world navigation strategies (such as directions in a building or filtering data in a spreadsheet) to reinforce understanding.
- Encourage learners to verbalize the logic behind each selector and to predict what will be matched—this supports deeper comprehension, especially for those new to CSS.
- For remote or asynchronous instruction, prompt learners to post screenshots or a list of selectors and their matches in a collaborative space. Offer feedback emphasizing both accuracy and any clever approaches discovered.
- Avoid culturally specific terminology or analogies—opt for globally relatable, neutral examples in explanation and activities.

**Knowledge check answers:**

- First question: B. `form > button` (matches only buttons that are immediate/direct children of a form, not nested deeper).
- Second question: C. Any checkbox input that comes immediately after a label.

---

## Selector Testing and Refinement with DevTools

**How to best deliver this microlesson:**

- Begin with a live demonstration of Chrome DevTools. Show both the Elements and Console panels, explaining their roles as you go.
- Emphasize the narrative: Draw parallels between using DevTools and “translating” Python automation logic to understand the browser’s structure.
- Relate new concepts back to prior lessons: Connect the hands-on activity to the learner’s recent experiments with basic selectors, attribute selectors, and advanced selector patterns.
- When leading the activity, encourage learners to say or write “why” each selector was chosen and describe the element it matches.
- Remind learners that editing HTML in DevTools is temporary. Encourage experimentation without fear of “breaking” anything.
- Use the discussion prompt to foster a mindset of continuous refinement and planning for future page changes—skills that will serve well in real-world automation scenarios.
- For remote delivery, have learners share screenshots or tables of their selector refinements in a class workspace.
- Highlight globally relevant, culturally neutral examples throughout.

---

🏗️ **Under Construction**

We are constantly working to improve our resources for instructors and students.

**Have something to contribute to this Instructor Guide?** [Let us know](https://pages.git.generalassemb.ly/modular-curriculum-all-courses/universal-resources-internal/module-feedback.html).
