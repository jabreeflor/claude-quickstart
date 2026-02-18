# ASCII Mockup

Create an ASCII wireframe/mockup for **$ARGUMENTS** before writing any UI code.

## Why ASCII First

- **Forces clarity** — Can't hide behind pretty pixels
- **Fast iteration** — Change layout in seconds
- **Universal** — Works in any terminal, any editor
- **Improves output** — Claude generates better UI code when it can "see" the target
- **Reveals structure** — Exposes component hierarchy naturally

## Mockup Syntax

### Containers & Layout
```
┌─────────────────────────────────────┐
│  Box with single border             │
└─────────────────────────────────────┘

╔═════════════════════════════════════╗
║  Box with double border (emphasis)  ║
╚═════════════════════════════════════╝

┌──────────┬──────────┬──────────┐
│  Col 1   │  Col 2   │  Col 3   │  ← Grid layout
└──────────┴──────────┴──────────┘
```

### Common Components
```
[  Button  ]              ← Button
[  Primary Action  ✓]     ← Primary button
[  Cancel  ✗]             ← Destructive button

[___________________]     ← Text input
[_email@example.com_]     ← Input with placeholder/value

[▼ Select option    ]     ← Dropdown
[○ Option 1         ]     ← Radio unselected
[● Option 2         ]     ← Radio selected
[☐ Checkbox         ]     ← Checkbox unchecked
[☑ Checkbox         ]     ← Checkbox checked

( Toggle OFF )            ← Toggle switch off
( ●━━━━ ON  )            ← Toggle switch on

[=====>        ] 45%      ← Progress bar

─────────────────────     ← Divider/separator

← Back   Title   ⋮ →      ← Navigation header

🔍 [__Search...__]        ← Search input

⚠️  Warning message        ← Alert
✅  Success message        
❌  Error message
ℹ️  Info message
```

### Page Structure
```
┌─────────────────────────────────────────────────┐
│  🏠 Logo          Nav 1  Nav 2  Nav 3   [Login] │  ← Header
├─────────────────────────────────────────────────┤
│ ┌─────────┐  ┌────────────────────────────────┐ │
│ │ Sidebar │  │                                │ │
│ │         │  │         Main Content           │ │
│ │ • Link  │  │                                │ │
│ │ • Link  │  │                                │ │
│ │ • Link  │  │                                │ │
│ └─────────┘  └────────────────────────────────┘ │
├─────────────────────────────────────────────────┤
│              Footer © 2024                      │  ← Footer
└─────────────────────────────────────────────────┘
```

### Cards & Lists
```
┌─────────────────────────────┐
│ 📷                          │  ← Image placeholder
│ ─────────────────────────── │
│ Card Title                  │
│ Description text here...    │
│                [Action]     │
└─────────────────────────────┘

┌─────────────────────────────────────┐
│ ☐  Task item with checkbox          │
├─────────────────────────────────────┤
│ ☑  Completed task item              │
├─────────────────────────────────────┤
│ ☐  Another task                     │
└─────────────────────────────────────┘
```

### Modal/Dialog
```
     ┌────────────────────────────┐
     │ ✕                          │
     │      Confirm Delete?       │
     │                            │
     │  Are you sure you want to  │
     │  delete this item?         │
     │                            │
     │   [Cancel]  [Delete ✗]     │
     └────────────────────────────┘
```

### Mobile Layout
```
┌──────────────────┐
│ ← Title        ⋮ │
├──────────────────┤
│                  │
│  Mobile Content  │
│                  │
│                  │
├──────────────────┤
│ 🏠   📱   👤   ⚙️  │  ← Bottom nav
└──────────────────┘
```

## Workflow

1. **Describe** the UI you need
2. **I'll create** ASCII mockup showing layout and components  
3. **You review** and request changes
4. **Iterate** until the structure is right
5. **Then build** — I'll implement matching the mockup exactly

## Annotations

Add notes outside the mockup:
```
┌─────────────────────────┐
│  User Profile Card      │ ← Component name
├─────────────────────────┤
│  👤 Avatar    [Edit]    │ ← 48px circle, right-aligned button
│  John Doe               │ ← text-xl font-bold  
│  john@email.com         │ ← text-sm text-muted
└─────────────────────────┘
    ↑ 
    Tailwind: rounded-lg shadow-md p-4
```

## Pro Tips

- **Start big, then detail** — Overall layout first, then zoom into components
- **One viewport at a time** — Desktop, then mobile variant
- **Name everything** — Makes the code conversation easier
- **Note interactions** — Hover states, click behaviors, transitions

## Tools

For complex mockups, try:
- **monosketch.io** — Browser-based ASCII drawing
- **asciiflow.com** — Simple flowcharts and boxes
- **textik.com** — Quick diagrams

## Begin

Let's mockup **$ARGUMENTS**:

1. What's the primary purpose of this UI?
2. Who's the user?
3. What are the key actions?
