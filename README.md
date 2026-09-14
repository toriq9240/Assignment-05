# 🧱 Dev Stack — Build Your Ideal Development Stack

Dev Stack is a responsive landing page that helps developers explore frontend, backend, database, and tooling options and put together a personalized "stack" for their next project. Technologies are loaded dynamically from a JSON file and rendered as interactive cards; visitors can add favorites to a "Your Stack" panel, remove them individually, or clear the whole stack at once — all with toast notifications for feedback.

🔗 **Live Site:** https://assignment-05-nine-zeta.vercel.app/
🔗 **GitHub Repository:** https://github.com/toriq9240/Assignment-05

---

## 🛠️ Technology Used

- **HTML5** — semantic page structure
- **CSS3** — custom styling, responsive layout, and the shared orange → pink → violet gradient theme
- **JavaScript (Vanilla ES6+)** — DOM rendering, state handling (stack array), and event listeners
- **Fetch API** — loads technology data from `data.json` asynchronously
- **JSON** — stores the technology catalog (id, name, category, description, icon, rating, difficulty, badge)
- **Google Fonts** — Manrope & Inter for typography
- **Vercel** — deployment and hosting

---

## ✨ Features

1. **Sticky, Responsive Navbar** — A fixed navbar with brand logo, center nav links, and Sign In/Sign Up actions on desktop, collapsing to a hamburger-menu layout on mobile.
2. **Dynamic Technology Catalog with Loading State** — Technology cards (icon, badge, description, category, difficulty, rating) are fetched from `data.json` at runtime rather than hardcoded, with a loading spinner shown while the data loads.
3. **Interactive Stack Builder** — Clicking "Add to Stack" moves a technology into the "Your Stack" sidebar, disables its button, and shows a toast; duplicate adds are blocked with a warning toast, individual items can be removed with the ✕ button, and "Remove All" clears the stack in one click.

---

## ❓ React Concepts — Answered in My Own Words

> Note: this project was built with **plain HTML, CSS, and vanilla JavaScript** rather than React. The answers below explain each concept conceptually, with a note on the equivalent pattern used in this project.

**1. What is JSX, and why is it used in React?**
JSX is a syntax extension that lets you write HTML-like markup directly inside JavaScript code. React uses it because it makes UI code easier to read and write — you can describe what the UI should look like using familiar tags, and JSX gets compiled into regular JavaScript function calls under the hood.

**2. What is the difference between props and state?**
Props are data passed *into* a component from its parent — they're read-only from the child's perspective. State is data a component manages *internally* and can change over time, usually in response to user interaction. In short: props flow down and are fixed by the parent; state lives inside a component and can update itself.

**3. What does the `useState` hook do, and where did you use it in this project?**
`useState` lets a React component keep and update its own piece of data, re-rendering the UI automatically whenever that data changes. This project doesn't use React, but the same idea appears in the plain-JS version: the `technologies` and `stack` variables act like state — whenever they're updated (e.g. after adding or removing a technology), `renderTechGrid()` and `renderStack()` are called manually to re-draw the UI, which is what `useState` would trigger automatically in React.

**4. What does the `useEffect` hook do, and why did you need it to load the JSON data?**
`useEffect` runs side effects (like data fetching) after a component renders, and can be configured to run once, on every render, or when specific values change. It's needed for loading JSON because fetching data is asynchronous and shouldn't block the initial render. In this project, the equivalent is the `fetch('data.json')` call that runs once when the page loads, populates the `technologies` array, and then renders the grid — the same "load data after initial render" pattern `useEffect` is designed for.

**5. Why does every item in a `.map()` list need a unique `key` prop?**
A unique key lets React tell items in a list apart so it can efficiently update, reorder, or remove just the items that changed instead of re-rendering the whole list. Without stable keys, React can mix up which DOM element belongs to which data item, causing bugs or lost UI state. In this project's vanilla-JS version, each technology's unique `id` is used the same way — as `data-id` attributes on cards and buttons — so the right item is always targeted when adding or removing it.

**6. What is conditional rendering? Show one place you used it (example: the empty stack message).**
Conditional rendering means showing different UI depending on some condition (like data being empty, loading, or present). In this project, the "Your Stack" panel checks whether the stack array is empty: if it is, it shows "No technologies selected yet." / "Your stack is empty."; otherwise, it renders the list of selected technologies and reveals the "Remove All" button.

**7. How do you pass data from a parent component to a child component, and how does a child send something back to the parent?**
A parent passes data down to a child through props — for example, a parent might pass a technology object into a `<TechCard technology={tech} />` component. To send data back up, the parent passes a *function* down as a prop (e.g. `onAdd`), and the child calls that function when something happens (like a button click), effectively "reporting back" to the parent. In this project's vanilla-JS equivalent, each button's `data-id` is read by an event listener attached after rendering, which then calls `addToStack(id)` / `removeFromStack(id)` — those functions play the role a parent's callback prop would play in React.

---

## 📤 Submission

- **GitHub Repository Link:** https://github.com/toriq9240/Assignment-05
- **Live Site Link:** https://assignment-05-toriqul.vercel.app
