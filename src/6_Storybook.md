# Storybook : 

- An interactive **directory** of your UI components and their stories.
- Storybook is packaged as a small, development-only, workshop that lives alongside your app.
- It helps you focus development on each variation of a component, even the hard-to-reach edge cases.
- Jump straight to working on a UI component in a specific state.
- Build and test individual components outside of the main development environment of the project.
- Can quickly create real product scenarios without having to build that functionality out for real.
  - *Like What does the dashboard look like if the user is brand new vs a veteran user? What does the logged in header look like vs logged out header?*

## Stories ?

> Capture UI variations as “stories”

- When developing a component variation in isolation, save it as a story. 
- 'Stories are a declarative syntax for *supplying props and mock data* to simulate component variations. 
- Each component can have *multiple stories*. 
- Each story allows you to demonstrate a *specific variation* of that component to verify appearance and behavior.
- You write stories for granular UI component variation and then use those stories in development, testing, and documentation.
- Storybook is the single source of truth for your UI. 
- Stories index all your components and their various states, making it easy for your team to find and reuse existing UI patterns. 
- Storybook also auto-generates *documentation* from those stories.
- Each story is exported as a JavaScript function enabling you to reuse it with other tools. 