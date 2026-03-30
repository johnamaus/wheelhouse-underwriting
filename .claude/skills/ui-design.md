---
name: ui-design
description: Build UI components following the Wheelhouse design system. Use when creating or modifying any frontend component, page, form, card, table, or visual element in this project.
user-invocable: true
allowed-tools: Read, Glob, Grep, Edit, Write
---

# Wheelhouse UI Design System

You are building UI for a Wheelhouse product. Follow these rules exactly. Do not deviate from the color palette, typography scale, or component patterns described below.

## Color System

All colors use CSS custom properties exposed as Tailwind `wh-*` utilities.

**NEVER use Tailwind's default gray palette** (`gray-100`, `slate-200`, `zinc-300`, etc.). Always use `wh-neutral-*`.

### Brand Colors
- `wh-primary` (#D926D2) — Primary brand magenta. Use for focus rings, primary links, active indicators
- `wh-primary-light` (#F6CBF4) — Hover states, subtle brand backgrounds
- `wh-primary-subtle` (#FFB8D9) — Chart accents, highlight fills
- `wh-dark` (#400B3E) — Dark brand variant, footer backgrounds

### Status Colors
- `wh-positive` (#22C55E) — Success, positive trends, connected states
- `wh-negative` (#ed4b3c) — Errors, destructive actions, negative trends
- `wh-warning` (#F59E0B) — Warnings, caution states

### Neutral Scale (use for ALL grays)
| Utility | Hex | Usage |
|---------|-----|-------|
| `wh-neutral-10` | #fafafb | Page backgrounds, subtle fills |
| `wh-neutral-25` | #f7f7f7 | Card hover fills, input icon backgrounds |
| `wh-neutral-50` | #efeeee | Inner dividers, subtle borders |
| `wh-neutral-100` | #e5e4e4 | Card borders, input borders, table dividers |
| `wh-neutral-200` | #cbcaca | Checkbox borders, disabled borders |
| `wh-neutral-300` | #b1afb0 | Placeholder text, muted icons |
| `wh-neutral-400` | #727072 | Captions, labels, secondary descriptions |
| `wh-neutral-500` | #646264 | Body text (secondary emphasis) |
| `wh-neutral-600` | #595759 | Body text (standard), table cell values |
| `wh-neutral-700` | #4e4c4e | Secondary headings, form label text |
| `wh-neutral-800` | #343234 | Primary headings, strong text, input values |
| `wh-neutral-900` | #282528 | Near-black, rarely used |

### Accent Colors (for categorized data)
Use standard Tailwind accents for multi-category data cards:
- **amber** — Primary accent (event data, CTAs, selected/active states, primary action buttons)
- **indigo** — Sign-in/email-gated features, auth prompts
- **blue** — "Week Before" or "previous" comparison data
- **teal** — "Week After" or "next" comparison data
- **purple** — "Same Time Last Year" or historical comparison data
- **emerald** — Success confirmations, connected/matched indicators

### Chart Colors
`--chart-1` (#FFB8D9), `--chart-2` (#D926D2), `--chart-3` (#9333EA), `--chart-4` (#7C2D8C), `--chart-5` (#22C55E)

---

## Typography

**Font:** Geist sans-serif (loaded via `next/font/google`, applied as `font-sans`)
**Letter spacing:** `-0.008em` on body (set in globals.css)

### Font Size Scale

**NEVER use Tailwind's default text sizes** (`text-sm`, `text-base`, `text-lg`, etc.). Always use bracket notation:

| Class | Usage |
|-------|-------|
| `text-[8px]` | Micro badges, uppercase tags ("EVENT", "SAVED", "RECURRING") |
| `text-[9px]` | Chrome labels, mini-dashboard decorations |
| `text-[10px]` | Pill labels, small CTAs, status badges, metric category labels, action links |
| `text-[11px]` | Secondary captions, meta row text, filter labels, trend annotations |
| `text-[12px]` | Form labels, body captions, table cells, descriptions, error messages |
| `text-[13px]` | Input text, form fields, button text, card body descriptions |
| `text-[14px]` | Card titles, list item headings, results count |
| `text-[15px]` | Modal section headings, gated-content titles |
| `text-[18px]` | Component-level headings ("Event Pulse", tool titles) |
| `text-[20px]` | Detail view headings (selected item name) |
| `text-[22px]` | Large metric values (occupancy %, dollar amounts) |

### Font Weight
- `font-medium` — Labels, secondary text with emphasis
- `font-semibold` — Card titles, section headings, button text, form labels
- `font-bold` — Large metric values, primary headings, event names

---

## Spacing & Layout

- **Border radius:** `rounded-xl` for cards/containers, `rounded-lg` for inputs/buttons/inner elements, `rounded-full` for pills/circular indicators
- **Card structure:** `border border-wh-neutral-100 rounded-xl bg-white overflow-hidden`
- **Section gaps:** `space-y-4` or `space-y-5` between sections
- **Card body padding:** `p-5`
- **Card header padding:** `px-5 py-4` (with `border-b border-wh-neutral-100`)
- **Inline gaps:** `gap-1.5` (tight icon+text), `gap-2` (standard), `gap-3` (comfortable), `gap-4` (loose)

---

## Component Templates

### Card with header
```jsx
<div className="border border-wh-neutral-100 rounded-xl bg-white overflow-hidden">
  <div className="px-5 py-4 border-b border-wh-neutral-100">
    <h2 className="text-[18px] font-semibold text-wh-neutral-800">Title</h2>
    <p className="text-[12px] text-wh-neutral-400 mt-0.5">Subtitle text</p>
  </div>
  <div className="p-5">
    {/* Content */}
  </div>
</div>
```

### Accent-colored data card
```jsx
<div className="border border-amber-200 rounded-xl bg-white overflow-hidden">
  <div className="px-5 py-3 bg-amber-50 flex items-center justify-between">
    <div className="flex items-center gap-2">
      <div className="w-7 h-7 rounded-lg bg-amber-100 flex items-center justify-center">
        <Icon className="w-4 h-4 text-amber-600" />
      </div>
      <div>
        <h3 className="text-[13px] font-semibold text-amber-700">Section Title</h3>
        <p className="text-[10px] text-wh-neutral-400">Subtitle</p>
      </div>
    </div>
  </div>
  <div className="px-5 py-4">{/* Metrics / data */}</div>
</div>
```
Replace `amber` with `blue`, `teal`, `purple`, `indigo` for other categories.

### Text input
```jsx
<div className="space-y-1.5">
  <label className="text-[12px] font-medium text-wh-neutral-700">Label</label>
  <input
    className="w-full px-3 py-2 text-[13px] text-wh-neutral-800 placeholder:text-wh-neutral-300 bg-white border border-wh-neutral-100 rounded-lg outline-none focus:border-wh-primary transition-colors"
    placeholder="Placeholder"
  />
</div>
```

### Input with icon prefix
```jsx
<div className="flex items-center border border-wh-neutral-100 rounded-lg overflow-hidden focus-within:border-wh-primary transition-colors">
  <div className="px-2.5 py-2 bg-wh-neutral-25 border-r border-wh-neutral-100">
    <Icon className="w-3.5 h-3.5 text-wh-neutral-300" />
  </div>
  <input className="flex-1 px-3 py-2 text-[13px] text-wh-neutral-800 placeholder:text-wh-neutral-300 bg-transparent border-0 outline-none" />
</div>
```

### Select dropdown
```jsx
<select className="w-full px-3 py-2 text-[13px] text-wh-neutral-800 bg-white border border-wh-neutral-100 rounded-lg outline-none focus:border-wh-primary transition-colors appearance-none cursor-pointer">
  <option value="">Choose...</option>
</select>
```

### Primary CTA button
```jsx
<button className="px-6 py-2 bg-amber-500 text-white text-[13px] font-semibold rounded-full hover:bg-amber-600 transition-colors disabled:opacity-50 flex items-center gap-2">
  <Icon className="w-3.5 h-3.5" />
  Label
</button>
```

### Secondary / outline button
```jsx
<button className="flex items-center gap-1.5 px-3 py-1.5 text-[11px] font-medium text-wh-neutral-600 border border-wh-neutral-100 rounded-lg hover:bg-wh-neutral-25 transition-colors disabled:opacity-30 disabled:cursor-not-allowed">
  <Icon className="w-3 h-3" />
  Label
</button>
```

### Small action button (colored)
```jsx
<button className="flex items-center gap-1 px-2.5 py-1 rounded-lg bg-amber-500/10 text-amber-600 text-[10px] font-semibold hover:bg-amber-500/20 transition-colors">
  <Icon className="w-3 h-3" />
  Action
</button>
```

### Badge / pill
```jsx
{/* Neutral pill */}
<span className="px-2 py-0.5 rounded-full bg-wh-neutral-25 text-[10px] font-medium text-wh-neutral-500">Category</span>

{/* Colored uppercase badge */}
<span className="px-1.5 py-0.5 rounded bg-amber-100 text-amber-600 text-[8px] font-bold uppercase">SAVED</span>

{/* Status dot + text */}
<div className="flex items-center gap-1.5 px-2.5 py-1 bg-emerald-50 border border-emerald-200/50 rounded-full">
  <div className="w-1.5 h-1.5 rounded-full bg-emerald-500" />
  <span className="text-[10px] font-medium text-emerald-700">Connected</span>
</div>
```

### Large metric display
```jsx
<div>
  <p className="text-[10px] text-wh-neutral-400 font-medium uppercase tracking-wide">Avg Occupancy</p>
  <p className="text-[22px] font-bold text-wh-neutral-800 leading-tight mt-1">72.3%</p>
</div>
```

### Trend indicator
```jsx
{/* Positive */}
<div className="flex items-center gap-1 text-emerald-600">
  <TrendingUp className="w-3 h-3" />
  <span className="text-[10px] font-medium">+5.2pp vs event</span>
</div>

{/* Negative */}
<div className="flex items-center gap-1 text-wh-negative">
  <TrendingDown className="w-3 h-3" />
  <span className="text-[10px] font-medium">-$12 vs event</span>
</div>
```

### Data table
```jsx
<table className="w-full text-[11px]">
  <thead>
    <tr className="border-b border-wh-neutral-100">
      <th className="text-left py-2 px-2 font-medium text-wh-neutral-400">Date</th>
      <th className="text-right py-2 px-2 font-medium text-wh-neutral-400">Value</th>
    </tr>
  </thead>
  <tbody>
    <tr className="border-b border-wh-neutral-50">
      <td className="py-1.5 px-2 text-wh-neutral-700 font-medium">Mar 28</td>
      <td className="py-1.5 px-2 text-right text-wh-neutral-600">$150</td>
    </tr>
    {/* Highlight row */}
    <tr className="border-b border-wh-neutral-50 bg-amber-50/50">
      <td className="py-1.5 px-2 text-wh-neutral-700 font-medium">
        Mar 30 <span className="ml-1 text-[8px] text-amber-600 font-bold uppercase">Event</span>
      </td>
      <td className="py-1.5 px-2 text-right font-semibold text-wh-neutral-800">$210</td>
    </tr>
  </tbody>
</table>
```

### Loading state
```jsx
<div className="flex flex-col items-center justify-center py-12 gap-3">
  <Loader2 className="h-6 w-6 animate-spin text-amber-500" />
  <p className="text-[12px] text-wh-neutral-400">Loading...</p>
</div>
```

### Error state
```jsx
<div className="border border-wh-negative/20 bg-wh-negative/5 rounded-xl p-4 flex items-start gap-3">
  <AlertCircle className="w-4 h-4 text-wh-negative mt-0.5 shrink-0" />
  <p className="text-[13px] text-wh-negative">Something went wrong. Please try again.</p>
</div>
```

### Success / info banner
```jsx
<div className="flex items-center gap-2 px-3 py-2 bg-emerald-50 border border-emerald-200/50 rounded-lg">
  <Check className="w-3.5 h-3.5 text-emerald-600" />
  <span className="text-[11px] font-medium text-emerald-700">Successfully connected</span>
</div>
```

### Gated content card (email/auth wall)
```jsx
<div className="border border-indigo-200 rounded-xl bg-gradient-to-br from-indigo-50 to-white overflow-hidden">
  <div className="p-5">
    <div className="flex items-start gap-3">
      <div className="w-10 h-10 rounded-xl bg-indigo-100 flex items-center justify-center shrink-0">
        <Lock className="w-5 h-5 text-indigo-600" />
      </div>
      <div className="flex-1">
        <h3 className="text-[15px] font-semibold text-wh-neutral-800">Unlock Feature</h3>
        <p className="text-[12px] text-wh-neutral-500 mt-1">Description of what signing in unlocks.</p>
        {/* Auth form goes here */}
      </div>
    </div>
  </div>
</div>
```

---

## Icons

Use **Lucide React** exclusively. Import icons individually:
```jsx
import { Search, MapPin, Loader2, AlertCircle, Check } from "lucide-react"
```

Standard icon sizes by context:
- `w-3 h-3` — Inside small buttons, inline with text-[10px]/text-[11px]
- `w-3.5 h-3.5` — Inside inputs, standard inline icons, with text-[12px]/text-[13px]
- `w-4 h-4` — Card header icons, section indicators, error/status icons
- `w-5 h-5` — Gated content hero icons (inside the 10x10 rounded container)
- `w-6 h-6` — Empty state placeholders (inside larger containers)
- `w-8 h-8` — Large empty state illustrations

---

## Rules

1. **No dark mode.** Light mode only. Never add `dark:` variants.
2. **No default grays.** Use `wh-neutral-*` for every gray value.
3. **No default text sizes.** Use `text-[Npx]` bracket notation only.
4. **All transitions use** `transition-colors` or `transition-all`. Keep durations default (150ms).
5. **All interactive elements** need hover and disabled states.
6. **Use `cn()` from `@/lib/utils`** for conditional class merging (clsx + tailwind-merge).
7. **Named exports only.** Never use `export default`.
8. **One component per feature file.** Sub-components go at the bottom of the same file.
9. **Minimal comments.** Only comment non-obvious logic. Never add JSDoc or docstrings.
