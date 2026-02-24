# SideQuest Landing v2

## Design Agent Profile

This project uses the **Ultimate Design Agent** (`/ultimate-design`) as the primary design workflow. When ANY design or UI work is requested, follow this agent profile:

### Automatic Behaviors

1. **For ANY UI/design task**: Run `/ultimate-design` to activate the full composite workflow
2. **Before ANY creative work**: Run `/brainstorming` first — no exceptions
3. **After ANY build**: Run `/critique` to self-review before showing the user
4. **Before ANY commit of UI changes**: Run `/design-review`

### Design Stack

- **Framework**: Tailwind CSS v4 (reference: `/tailwindcss-v4`)
- **Components**: shadcn/ui (reference: `/shadcn-ui`)
- **Animations**: Framer Motion (reference: `/framer-motion`)
- **Design System**: Generated via `/ui-ux-pro-max`
- **Visual QA**: Playwright screenshot iteration loops (`/playwright-skill`)

### Design Quality Standards

- NEVER use generic fonts (Inter, Roboto, Arial)
- NEVER use purple gradients on white backgrounds
- NEVER skip the Playwright screenshot iteration loop
- ALWAYS run craft critique before presenting work
- ALWAYS design for both light and dark mode
- ALWAYS test responsive at 375px, 768px, 1024px, 1440px
- Every design choice must have an explainable WHY

### iOS Design (when applicable)

When building for iOS or mobile-first:
- Follow Apple HIG (Human Interface Guidelines)
- Use SF system font scale (Large Title 34pt → Caption 2 11pt)
- Minimum 44x44pt tap targets
- Respect safe area insets
- Use iOS semantic colors and grouped backgrounds
- Support both light and dark appearance

### Workflow Sequence

```
/brainstorming → /ui-ux-pro-max → Design Direction → Build → Screenshot Loop → /critique → /design-review → Ship
```
