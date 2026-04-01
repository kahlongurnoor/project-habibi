# Project Habibi — Design System 2.0

## Developer Reference Guide

> **Source:** Figma Design System 2.0 — `Project Habibi Components` page
> **Font Family:** Unilever Desire (display/branding), Inter (UI/body)
> **Framework Target:** React + Tailwind CSS (utility-first)
> **Base Unit:** 16px (1rem)

---

## Table of Contents

1. [Design Tokens Overview](#1-design-tokens-overview)
2. [Color System](#2-color-system)
3. [Typography Scale](#3-typography-scale)
4. [Spacing System](#4-spacing-system)
5. [Buttons](#5-buttons)
6. [Cards](#6-cards)
7. [Modals & Dialogs](#7-modals--dialogs)
8. [Charts & Graphs](#8-charts--graphs)
9. [Dashboard Widgets](#9-dashboard-widgets)
10. [Smaller Widgets & Inputs](#10-smaller-widgets--inputs)
11. [Tailwind Config Reference](#11-tailwind-config-reference)

---

## 1. Design Tokens Overview

Design tokens are the foundational variables that drive every visual decision in the system. Think of them as the single source of truth — if you change a token, every component using it updates automatically.

### How Tokens Map to Code

| Figma Concept | React/CSS Concept | Tailwind Concept |
|---|---|---|
| Color Swatch | CSS Variable / const | `bg-brand-500`, `text-gray-700` |
| Font Size | `font-size` | `text-sm`, `text-base`, `text-lg` |
| Spacing | `padding` / `margin` / `gap` | `p-4`, `m-6`, `gap-3` |
| Border Radius | `border-radius` | `rounded-lg`, `rounded-xl` |
| Shadow | `box-shadow` | `shadow-sm`, `shadow-md` |

---

## 2. Color System

The color system is split into **Primary Colors** (used for the majority of the UI) and **Secondary Colors** (used sparingly for accents, pills, alerts, and labels).

Each color family uses a **25–900 shade scale**. Lower numbers = lighter. Higher numbers = darker.

### How to Read the Scale

- **25–100:** Backgrounds, subtle fills, hover states on light surfaces
- **200–300:** Borders, dividers, disabled states
- **400–500:** Icons, secondary text, mid-emphasis elements
- **600–700:** Primary interactive elements (buttons, links, focused inputs)
- **800–900:** High-contrast text, dark headers, darkest backgrounds

---

### 2.1 Primary Colors

#### Brand (Purple — Primary Interactive Color)

> Used across **all interactive elements**: buttons, links, inputs, focus rings, active states. This is the main personality color of the system.

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `brand-25` | `#FCFAFF` | `bg-brand-25` | Lightest background hover |
| `brand-50` | `#F9F5FF` | `bg-brand-50` | Selected row bg, subtle highlight |
| `brand-100` | `#F4EBFF` | `bg-brand-100` | Light badge bg, pill bg |
| `brand-200` | `#E9D7FE` | `border-brand-200` | Light border, focus ring tint |
| `brand-300` | `#D6BBFB` | `border-brand-300` | Active border state |
| `brand-400` | `#B692F6` | `text-brand-400` | Placeholder text, disabled icon |
| `brand-500` | `#9E77ED` | `bg-brand-500` | Mid-emphasis buttons, icons |
| `brand-600` | `#6941C6` | `bg-brand-600` | **Primary button fill**, links |
| `brand-700` | `#7F56D9` | `bg-brand-700` | Button hover, active links |
| `brand-800` | `#53389E` | `text-brand-800` | Dark emphasis text |
| `brand-900` | `#42307D` | `text-brand-900` | Headings on light bg |

**React Usage:**
```jsx
{/* Primary Button */}
<button className="bg-brand-600 hover:bg-brand-700 text-white px-4 py-2 rounded-lg">
  Approve Plan
</button>

{/* Subtle Badge */}
<span className="bg-brand-50 text-brand-700 px-2 py-1 rounded-full text-sm">
  Active
</span>
```

---

#### Gray (Neutral Foundation)

> **The backbone of UI design.** Used for text, form fields, backgrounds, dividers, borders — nearly everything that isn't interactive.

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `gray-25` | `#FCFCFD` | `bg-gray-25` | Page background (lightest) |
| `gray-50` | `#F9FAFB` | `bg-gray-50` | Card background, table row alt |
| `gray-100` | `#F2F4F7` | `bg-gray-100` | Input background, sidebar bg |
| `gray-200` | `#E4E7EC` | `border-gray-200` | Default borders, dividers |
| `gray-300` | `#D0D5DD` | `border-gray-300` | Input borders, stronger dividers |
| `gray-400` | `#98A2B3` | `text-gray-400` | Placeholder text, disabled text |
| `gray-500` | `#667085` | `text-gray-500` | Supporting text, labels, captions |
| `gray-600` | `#475467` | `text-gray-600` | Body text (secondary) |
| `gray-700` | `#344054` | `text-gray-700` | Body text (primary) |
| `gray-800` | `#1D2939` | `text-gray-800` | Headings, bold text |
| `gray-900` | `#101828` | `text-gray-900` | Display text, highest contrast |

**React Usage:**
```jsx
{/* Standard card layout */}
<div className="bg-white border border-gray-200 rounded-xl p-6">
  <h3 className="text-gray-900 text-lg font-semibold">Card Title</h3>
  <p className="text-gray-500 text-sm mt-1">Supporting text goes here</p>
  <div className="border-t border-gray-200 mt-4 pt-4">
    {/* Card footer content */}
  </div>
</div>
```

---

#### Error / Red

> Communicates **destructive actions, validation errors, and critical alerts.** Use sparingly for maximum impact.

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `error-50` | `#FEF3F2` | `bg-error-50` | Error message bg |
| `error-100` | `#FEE4E2` | `bg-error-100` | Error badge bg |
| `error-300` | `#FDA29B` | `border-error-300` | Error input border |
| `error-400` | `#F97066` | `text-error-400` | Error icon |
| `error-500` | `#F04438` | `bg-error-500` | Destructive button |
| `error-600` | `#D92D20` | `bg-error-600` | Destructive button hover |
| `error-700` | `#B42318` | `text-error-700` | Error text |
| `error-800` | `#912018` | `text-error-800` | Dark error emphasis |
| `error-900` | `#7A271A` | `text-error-900` | Darkest error text |

**React Usage:**
```jsx
{/* Error state input */}
<div>
  <input className="border border-error-300 focus:ring-error-500 rounded-lg px-3 py-2" />
  <p className="text-error-700 text-sm mt-1">This field is required</p>
</div>

{/* Destructive button */}
<button className="bg-error-600 hover:bg-error-700 text-white px-4 py-2 rounded-lg">
  Deactivate Account
</button>
```

---

#### Warning / Yellow-Orange

> Communicates **caution, pending states, and non-critical alerts.** Common in validation flows and status indicators.

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `warning-50` | `#FFFAEB` | `bg-warning-50` | Warning alert bg |
| `warning-100` | `#FEF0C7` | `bg-warning-100` | Warning badge bg |
| `warning-300` | `#FEC84B` | `border-warning-300` | Warning border |
| `warning-400` | `#FDB022` | `text-warning-400` | Warning icon |
| `warning-500` | `#F79009` | `bg-warning-500` | Warning indicator |
| `warning-600` | `#DC6803` | `text-warning-600` | Warning text |
| `warning-700` | `#B54708` | `text-warning-700` | Dark warning text |
| `warning-900` | `#93370D` | `text-warning-900` | Darkest warning |

---

#### Success / Green

> Communicates **confirmation, completion, and positive outcomes.** Used in toast notifications, success badges, and status pills.

| Token | Hex | Tailwind Class | Usage |
|---|---|---|---|
| `success-100` | `#D1FADF` | `bg-success-100` | Success badge bg |
| `success-200` | `#A6F4C5` | `bg-success-200` | Highlight bg |
| `success-300` | `#6CE9A6` | `border-success-300` | Success border |
| `success-400` | `#32D583` | `text-success-400` | Success icon |
| `success-500` | `#12B76A` | `bg-success-500` | Active status pill |
| `success-600` | `#039855` | `text-success-600` | Success text |
| `success-700` | `#027A48` | `text-success-700` | Dark success text |
| `success-800` | `#05603A` | `text-success-800` | Heading on success bg |
| `success-900` | `#054F31` | `text-success-900` | Darkest success |

---

### 2.2 Secondary Colors (Accents)

> These are used **sparingly** — for pills, labels, category indicators, data visualization, and anywhere you need color variety without overriding the primary brand.

#### Blue Gray

| Token | Hex | Usage |
|---|---|---|
| `bluegray-25` | `#FCFCFD` | Light bg |
| `bluegray-50` | `#F8F9FC` | Subtle fill |
| `bluegray-100` | `#EAECF5` | Borders |
| `bluegray-200` | `#D5D9EB` | Spacer/divider indicators |
| `bluegray-300` | `#AFB5D9` | Muted icons |
| `bluegray-400` | `#717BBC` | Secondary icons |
| `bluegray-500` | `#4E5BA6` | Text labels |
| `bluegray-600` | `#3E4784` | Strong labels |
| `bluegray-700` | `#363F72` | Dark text |
| `bluegray-800` | `#293056` | Heading text |
| `bluegray-900` | `#101323` | Display text, highest contrast |

#### Blue

| Token | Hex | Usage |
|---|---|---|
| `blue-25` | `#F5FAFF` | Info bg |
| `blue-50` | `#EFF8FF` | Badge bg |
| `blue-100` | `#D1E9FF` | Highlight |
| `blue-200` | `#B2DDFF` | Light border |
| `blue-300` | `#84CAFF` | Icon tint |
| `blue-400` | `#53B1FD` | Link text (light mode) |
| `blue-500` | `#2E90FA` | Chart accent, links |
| `blue-600` | `#1570EF` | Primary info elements |
| `blue-700` | `#175CD3` | Annotation labels, spacing guides |
| `blue-800` | `#1849A9` | Strong emphasis |
| `blue-900` | `#194185` | Dark heading |

#### Purple (Accent — distinct from Brand)

| Token | Hex | Usage |
|---|---|---|
| `purple-25` | `#FAFAFF` | Light bg |
| `purple-50` | `#F4F3FF` | Badge bg |
| `purple-100` | `#EBE9FE` | Highlight |
| `purple-200` | `#D9D6FE` | Border |
| `purple-300` | `#BDB4FE` | Icon |
| `purple-400` | `#9B8AFB` | Mid text |
| `purple-500` | `#7A5AF8` | Interactive |
| `purple-600` | `#6938EF` | Strong interactive |
| `purple-700` | `#5925DC` | Dark interactive |
| `purple-800` | `#4A1FB8` | Emphasis |
| `purple-900` | `#3E1C96` | Highest contrast |

---

### 2.3 Dark Mode Palette

The design system includes dark-themed components (visible on cards and dashboard screens). The dark theme uses:

| Role | Hex | Description |
|---|---|---|
| Dark Background | `#101323` / `#1D2939` | Main panel background |
| Dark Surface | `#293056` / `#344054` | Card surface on dark bg |
| Dark Border | `#363F72` / `#475467` | Subtle borders on dark surfaces |
| Dark Text Primary | `#FCFCFD` / `#F9FAFB` | White text on dark bg |
| Dark Text Secondary | `#D0D5DD` / `#98A2B3` | Muted text on dark bg |
| Dark Accent | `#7F56D9` / `#9E77ED` | Brand color on dark bg |

---

## 3. Typography Scale

**Primary Font:** `Inter` (UI, body, all functional text)
**Brand Font:** `Unilever Desire` (display headings, marketing copy)

### 3.1 Display Sizes

| Token | Size | Weight | Line Height | Letter Spacing | Tailwind | Usage |
|---|---|---|---|---|---|---|
| Display 2xl/Regular | 72px | 400 | 90px | -2% | `text-7xl font-normal` | Hero headings |
| Display 2xl/Bold | 72px | 700 | 90px | -2% | `text-7xl font-bold` | Bold hero headings |
| Display xl/Regular | 60px | 400 | 72px | -2% | `text-6xl font-normal` | Section headings |
| Display xl/Bold | 60px | 700 | 72px | -2% | `text-6xl font-bold` | Bold section headings |
| Display lg/Regular | 48px | 400 | 60px | -2% | `text-5xl font-normal` | Page titles |
| Display lg/Bold | 48px | 700 | 60px | -2% | `text-5xl font-bold` | Bold page titles |
| Display md/Regular | 36px | 400 | 44px | -2% | `text-4xl font-normal` | Subsection titles |
| Display md/Bold | 36px | 700 | 44px | -2% | `text-4xl font-bold` | Bold subsection titles |
| Display sm/Regular | 30px | 400 | 38px | 0 | `text-3xl font-normal` | Card/widget titles |
| Display sm/Bold | 30px | 700 | 38px | 0 | `text-3xl font-bold` | Bold card titles |
| Display xs/Semibold | 24px | 600 | 32px | 0 | `text-2xl font-semibold` | Panel headings, section labels |

### 3.2 Body / Functional Text

| Token | Size | Weight | Line Height | Tailwind | Usage |
|---|---|---|---|---|---|
| Text xl/Regular | 20px | 400 | 30px | `text-xl` | Large body text |
| Text xl/Semibold | 20px | 600 | 30px | `text-xl font-semibold` | Large bold label |
| Text lg/Regular | 18px | 400 | 28px | `text-lg` | Descriptions, supporting text |
| Text lg/Semibold | 18px | 600 | 28px | `text-lg font-semibold` | Sub-labels, form section headers |
| Text md/Regular | 16px | 400 | 24px | `text-base` | Default body text |
| Text md/Semibold | 16px | 600 | 24px | `text-base font-semibold` | Table headers, bold body |
| Text sm/Regular | 14px | 400 | 20px | `text-sm` | Table cells, form labels |
| Text sm/Semibold | 14px | 600 | 20px | `text-sm font-semibold` | Bold labels, badge text |
| Text xs/Regular | 12px | 400 | 18px | `text-xs` | Captions, footnotes, timestamps |
| Text xs/Semibold | 12px | 600 | 18px | `text-xs font-semibold` | Small bold indicators |

### 3.3 Font Weights Available

| Weight | Value | Tailwind | Available For |
|---|---|---|---|
| Regular | 400 | `font-normal` | Inter, Unilever Desire |
| Light | 300 | `font-light` | Inter, Unilever Desire |
| Semibold | 600 | `font-semibold` | Inter, Unilever Desire |
| Bold | 700 | `font-bold` | Inter, Unilever Desire |

### Typography in React — Quick Reference

```jsx
{/* Page heading */}
<h1 className="font-['Unilever_Desire'] text-4xl font-bold text-gray-900 tracking-tight">
  Dashboard Overview
</h1>

{/* Section heading */}
<h2 className="text-2xl font-semibold text-gray-900">
  Spacing system guides
</h2>

{/* Supporting text */}
<p className="text-lg text-bluegray-700 leading-7">
  These spacing system guides are useful for annotating designs...
</p>

{/* Body text */}
<p className="text-base text-gray-700 leading-6">
  Standard paragraph text used throughout the application.
</p>

{/* Caption / timestamp */}
<span className="text-xs text-gray-500">
  Last updated: 2 hours ago
</span>
```

---

## 4. Spacing System

The spacing system uses a **16px base** and follows standard rem increments. This maps 1:1 with default Tailwind spacing utilities.

### 4.1 Spacing Scale

| Token Name | Rem Value | Pixel Value | Tailwind Class | Common Usage |
|---|---|---|---|---|
| `spacing-1` | 0.25rem | 4px | `p-1`, `m-1`, `gap-1` | Inline icon gap, tight padding |
| `spacing-2` | 0.5rem | 8px | `p-2`, `m-2`, `gap-2` | Compact element gap |
| `spacing-3` | 0.75rem | 12px | `p-3`, `m-3`, `gap-3` | Button padding-x, badge padding |
| `spacing-4` | 1rem | 16px | `p-4`, `m-4`, `gap-4` | **Default internal padding**, card gap |
| `spacing-5` | 1.25rem | 20px | `p-5`, `m-5`, `gap-5` | Medium padding |
| `spacing-6` | 1.5rem | 24px | `p-6`, `m-6`, `gap-6` | **Default card padding**, section gap |
| `spacing-8` | 2rem | 32px | `p-8`, `m-8`, `gap-8` | Large internal spacing |
| `spacing-10` | 2.5rem | 40px | `p-10`, `gap-10` | Widget/section separation |
| `spacing-12` | 3rem | 48px | `p-12`, `gap-12` | Panel section breaks |
| `spacing-16` | 4rem | 64px | `p-16`, `gap-16` | **Major section dividers** |
| `spacing-20` | 5rem | 80px | `py-20` | Page section padding |
| `spacing-24` | 6rem | 96px | `py-24` | Hero section padding |
| `spacing-32` | 8rem | 128px | — | Large layout sections |
| `spacing-40` | 10rem | 160px | — | Full-page layout offset |
| `spacing-48` | 12rem | 192px | — | Sidebar widths |
| `spacing-56` | 14rem | 224px | — | Wide sidebar |
| `spacing-64` | 16rem | 256px | — | Maximum spacer width |

### 4.2 Spacing Gameplay — When to Use What

**Inside a component** (card, button, input):
```
Tight (4px–8px): Icon-to-text gaps, inline badge padding
Default (12px–16px): Button padding, input padding, list item gap
Roomy (20px–24px): Card internal padding, modal padding
```

**Between components** (sections, groups, layout):
```
Tight (8px–16px): Stacked form fields, table cell spacing
Default (24px–32px): Cards in a grid, widget sections
Spacious (48px–64px): Page sections, major content breaks
```

**React Pattern:**
```jsx
{/* Card with standard spacing */}
<div className="p-6 space-y-4">           {/* 24px padding, 16px gap between children */}
  <div className="flex items-center gap-3"> {/* 12px icon-to-text gap */}
    <Icon />
    <h3 className="text-lg font-semibold">Title</h3>
  </div>
  <p className="text-sm text-gray-500">Description</p>
  <div className="flex gap-3 pt-4">        {/* 16px top padding before buttons */}
    <button className="px-4 py-2">Action</button>
  </div>
</div>
```

---

## 5. Buttons

The button system covers **6 visual hierarchies × 3 sizes × multiple states**.

### 5.1 Button Hierarchy

| Variant | Visual Style | When to Use |
|---|---|---|
| **Primary** | `bg-brand-600` solid fill, white text | Main CTA — one per visible section max |
| **Secondary Color** | `bg-brand-50` light fill, `text-brand-700` | Supporting action alongside primary |
| **Secondary Gray** | `bg-white border border-gray-300`, `text-gray-700` | Default/neutral action |
| **Tertiary Color** | No bg, `text-brand-700` | Low-emphasis actions, links in context |
| **Tertiary Gray** | No bg, `text-gray-500` | Minimal emphasis, cancel/dismiss |
| **Destructive** | `bg-error-600` solid fill, white text | Delete, deactivate, remove actions |

### 5.2 Button Sizes

| Size | Padding | Font Size | Height | Tailwind |
|---|---|---|---|---|
| **sm** | `px-3 py-2` | 14px (text-sm) | ~36px | `px-3 py-2 text-sm` |
| **md** | `px-4 py-2.5` | 14px (text-sm) | ~40px | `px-4 py-2.5 text-sm` |
| **lg** | `px-4 py-2.5` | 16px (text-base) | ~44px | `px-4 py-2.5 text-base` |

### 5.3 Button States

| State | Change from Default |
|---|---|
| **Default** | Base styles |
| **Hover** | Darken bg by one shade (600→700) |
| **Focused** | Add `ring-4 ring-brand-100` (focus ring) |
| **Disabled** | `opacity-50 cursor-not-allowed` |

### 5.4 Button Sub-Variants

Buttons support optional decorations:

- **Text only** — just the label
- **Leading icon** — icon before text (`<Icon /> Label`)
- **Trailing icon** — icon after text (`Label <Icon />`)
- **Leading + Trailing** — icon on both sides
- **Icon only** — square button, just an icon (usually for toolbars)
- **Dot indicator** — small colored dot before the label (status buttons)

### 5.5 Button React Component Pattern

```jsx
// Button.jsx
const variants = {
  primary: 'bg-brand-600 text-white hover:bg-brand-700 focus:ring-4 focus:ring-brand-100',
  secondaryColor: 'bg-brand-50 text-brand-700 hover:bg-brand-100',
  secondaryGray: 'bg-white border border-gray-300 text-gray-700 hover:bg-gray-50',
  tertiaryColor: 'text-brand-700 hover:bg-brand-50',
  tertiaryGray: 'text-gray-500 hover:bg-gray-50 hover:text-gray-700',
  destructive: 'bg-error-600 text-white hover:bg-error-700 focus:ring-4 focus:ring-error-100',
};

const sizes = {
  sm: 'px-3 py-2 text-sm gap-2 rounded-lg',
  md: 'px-4 py-2.5 text-sm gap-2 rounded-lg',
  lg: 'px-4 py-2.5 text-base gap-2 rounded-lg',
};

function Button({ variant = 'primary', size = 'md', leadingIcon, trailingIcon, children, ...props }) {
  return (
    <button
      className={`inline-flex items-center justify-center font-semibold transition-colors
        ${variants[variant]} ${sizes[size]}
        disabled:opacity-50 disabled:cursor-not-allowed`}
      {...props}
    >
      {leadingIcon && <span className="w-5 h-5">{leadingIcon}</span>}
      {children}
      {trailingIcon && <span className="w-5 h-5">{trailingIcon}</span>}
    </button>
  );
}
```

### 5.6 Quick Filter Pills

A row of selectable pill-style buttons for filtering/tabs:

```jsx
{/* Quick Filters row */}
<div className="flex items-center gap-2">
  <button className="px-3 py-1.5 bg-brand-50 text-brand-700 text-sm font-medium rounded-full">
    Default
  </button>
  <button className="px-3 py-1.5 bg-white border border-gray-200 text-gray-600 text-sm rounded-full hover:bg-gray-50">
    Automatic
  </button>
</div>
```

---

## 6. Cards

Cards are the most-used container component. The system defines several card types.

### 6.1 Card Variants

| Card Type | Description | Key Visual |
|---|---|---|
| **Simple Card** | Title + description + optional footer | White bg, `border border-gray-200`, `rounded-xl` |
| **Card with Icon** | Icon left of the title row | 40px icon container, `gap-4` to text |
| **Card with Action** | Includes inline button/CTA | Footer with divider, button aligned right |
| **Stat Card** | Big number + label + optional trend icon | Number is `text-3xl font-semibold`, label is `text-sm text-gray-500` |
| **Proposed Plan Card** | Multi-line summary + approve/reject buttons | Has version badge, numbered list, dual CTA |
| **Agent Card** | Status indicator + name + pill | Status dot + pill component on the right |
| **Feedback Card** | Metric cards in a row (total, positive, negative, rating) | Icon top-right, metric is large, label below |

### 6.2 Base Card Structure

```jsx
{/* Base Card */}
<div className="bg-white border border-gray-200 rounded-xl shadow-sm">
  {/* Card Header */}
  <div className="px-6 py-5">
    <div className="flex items-center justify-between">
      <h3 className="text-lg font-semibold text-gray-900">Card Title</h3>
      <button className="text-gray-400 hover:text-gray-600">
        {/* info/menu icon */}
      </button>
    </div>
    <p className="text-sm text-gray-500 mt-1">Supporting description text</p>
  </div>

  {/* Card Body */}
  <div className="px-6 py-4">
    {/* content */}
  </div>

  {/* Card Footer (optional) */}
  <div className="px-6 py-4 border-t border-gray-200 flex items-center justify-end gap-3">
    <button className="text-sm text-gray-500">Cancel</button>
    <button className="bg-brand-600 text-white px-4 py-2 rounded-lg text-sm font-semibold">
      Confirm
    </button>
  </div>
</div>
```

### 6.3 Stat Card Pattern

These are used in dashboard rows (typically 3–5 per row).

```jsx
{/* Stat Card */}
<div className="bg-white border border-gray-200 rounded-xl p-6 min-w-[160px]">
  <div className="flex items-center justify-between mb-2">
    <p className="text-sm text-gray-500 font-medium">Total Conversations</p>
    <InfoIcon className="w-4 h-4 text-gray-400" />
  </div>
  <p className="text-3xl font-semibold text-gray-900">48</p>
</div>
```

**Grid layout for stat rows:**
```jsx
<div className="grid grid-cols-3 gap-6">
  <StatCard label="Total Conversations" value="48" />
  <StatCard label="Total Time" value="288" />
  <StatCard label="Correlation Rate" value="3.9M" />
</div>
```

### 6.4 Proposed Plan Card (Agent-specific)

A unique card used in the Nexus agent workflow:

```jsx
<div className="bg-white border border-gray-200 rounded-xl">
  <div className="px-6 py-5 flex items-center justify-between">
    <div className="flex items-center gap-2">
      <span className="text-xs text-gray-500">4:15 p.m.</span>
      <span className="text-sm font-semibold text-gray-900">Proposed Plan</span>
    </div>
    <span className="text-xs bg-brand-50 text-brand-700 px-2 py-0.5 rounded-full">
      Version 1
    </span>
  </div>
  <div className="px-6 pb-4">
    <ol className="list-decimal list-inside text-sm text-gray-700 space-y-2">
      <li>Cards can include buttons and interactive elements.</li>
      <li>Cards can include buttons and interactive elements.</li>
    </ol>
  </div>
  <div className="px-6 py-4 border-t border-gray-200 flex justify-end gap-3">
    <button className="px-4 py-2 bg-white border border-gray-300 text-gray-700 text-sm font-semibold rounded-lg">
      Edit Plan
    </button>
    <button className="px-4 py-2 bg-brand-600 text-white text-sm font-semibold rounded-lg flex items-center gap-2">
      Approve Plan <CheckIcon className="w-4 h-4" />
    </button>
  </div>
</div>
```

---

## 7. Modals & Dialogs

### 7.1 Modal Types

| Type | Description |
|---|---|
| **Data Table Modal** | Scrollable table inside a modal (e.g., Event Type Distribution) |
| **Date Picker Modal** | Calendar grid with range selection |
| **Feedback Details Modal** | Key-value details view with status badges |
| **Form Modal** | Input fields + submit (e.g., Red Team Test creation) |
| **Confirmation Dialog** | Icon + title + description + dual buttons (success/destructive) |
| **Create/Task Modal** | Sidebar-style modal with form fields and structured inputs |

### 7.2 Base Modal Structure

```jsx
{/* Modal Backdrop */}
<div className="fixed inset-0 bg-gray-900/60 flex items-center justify-center z-50">
  {/* Modal Container */}
  <div className="bg-white rounded-xl shadow-xl w-full max-w-lg mx-4">
    {/* Modal Header */}
    <div className="px-6 py-5 border-b border-gray-200 flex items-center justify-between">
      <h2 className="text-lg font-semibold text-gray-900">Modal Title</h2>
      <button className="text-gray-400 hover:text-gray-600">
        <CloseIcon className="w-5 h-5" />
      </button>
    </div>

    {/* Modal Body */}
    <div className="px-6 py-5">
      {/* content */}
    </div>

    {/* Modal Footer */}
    <div className="px-6 py-4 border-t border-gray-200 flex justify-end gap-3">
      <button className="px-4 py-2 border border-gray-300 text-gray-700 text-sm font-semibold rounded-lg">
        Cancel
      </button>
      <button className="px-4 py-2 bg-brand-600 text-white text-sm font-semibold rounded-lg">
        Confirm
      </button>
    </div>
  </div>
</div>
```

### 7.3 Confirmation Dialogs (Success / Destructive)

```jsx
{/* Success Confirmation */}
<div className="bg-white rounded-xl p-6 max-w-sm text-center">
  <div className="mx-auto w-12 h-12 bg-success-100 rounded-full flex items-center justify-center mb-4">
    <CheckIcon className="w-6 h-6 text-success-600" />
  </div>
  <h3 className="text-lg font-semibold text-gray-900">Payment successful</h3>
  <p className="text-sm text-gray-500 mt-2">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
  </p>
  <button className="mt-6 w-full px-4 py-2 bg-brand-600 text-white font-semibold rounded-lg">
    Go to Dashboard
  </button>
</div>

{/* Destructive Confirmation */}
<div className="bg-white rounded-xl p-6 max-w-sm text-center">
  <div className="mx-auto w-12 h-12 bg-error-100 rounded-full flex items-center justify-center mb-4">
    <AlertIcon className="w-6 h-6 text-error-600" />
  </div>
  <h3 className="text-lg font-semibold text-gray-900">Deactivate account</h3>
  <p className="text-sm text-gray-500 mt-2">
    Are you sure? This action cannot be undone.
  </p>
  <div className="mt-6 flex gap-3">
    <button className="flex-1 px-4 py-2 border border-gray-300 text-gray-700 font-semibold rounded-lg">
      Cancel
    </button>
    <button className="flex-1 px-4 py-2 bg-error-600 text-white font-semibold rounded-lg">
      Deactivate
    </button>
  </div>
</div>
```

---

## 8. Charts & Graphs

The design system defines chart building blocks, content patterns, and multiple chart types.

### 8.1 Chart Types Available

| Chart Type | Usage | Data Shape |
|---|---|---|
| **Line Chart** | Trends over time | x: time, y: numeric |
| **Area Chart** | Volume over time | x: time, y: numeric (filled) |
| **Vertical Bar Chart** | Category comparison | x: category, y: numeric |
| **Horizontal Bar Chart** | Ranked comparisons | x: numeric, y: category |
| **Pie Chart** | Proportional breakdown | label + value |
| **Donut Chart** | Proportional with center label | label + value, center text |
| **Radar Chart** | Multi-dimensional comparison | axes + values |
| **Stacked Bar** | Composition over categories | x: category, y: stacked values |

### 8.2 Chart Color Palette

Charts use the **Blue** secondary palette as the primary data color:

| Series | Color | Hex |
|---|---|---|
| Series 1 (primary) | Blue-600 | `#1570EF` |
| Series 2 | Blue-400 | `#53B1FD` |
| Series 3 | Blue-200 | `#B2DDFF` |
| Accent / highlight | Brand-600 | `#6941C6` |
| Negative / error | Error-500 | `#F04438` |
| Positive / success | Success-500 | `#12B76A` |

For pie charts, additional colors cycle through: `#1570EF`, `#F04438`, `#F79009`, `#12B76A`, `#6941C6`.

### 8.3 Chart Building Blocks

| Element | Description | Style |
|---|---|---|
| **Chart Container** | White card wrapper | `bg-white border border-gray-200 rounded-xl p-6` |
| **Horizontal Axis** | Bottom labels | `text-xs text-gray-500`, ticks at `gray-200` |
| **Vertical Axis** | Left labels | `text-xs text-gray-500`, gridlines at `gray-100` |
| **Legend** | Color dot + label pairs | `flex gap-4`, dot is `w-2 h-2 rounded-full` |
| **Chart Tooltip** | Hover detail box | `bg-gray-900 text-white px-3 py-2 rounded-lg text-xs shadow-lg` |

### 8.4 Chart Card Pattern

```jsx
<div className="bg-white border border-gray-200 rounded-xl">
  <div className="px-6 py-5 flex items-center justify-between">
    <div>
      <h3 className="text-base font-semibold text-gray-900">LLM Calls Over Time</h3>
      <p className="text-sm text-gray-500 mt-0.5">Total: 12 Requests</p>
    </div>
    <button className="text-gray-400">
      <InfoIcon className="w-5 h-5" />
    </button>
  </div>
  <div className="px-6 pb-6 h-[240px]">
    {/* Recharts / D3 chart renders here */}
  </div>
</div>
```

---

## 9. Dashboard Widgets

Dashboard widgets are the complex composite components used in Nexus agent dashboards.

### 9.1 Widget Types

| Widget | Description |
|---|---|
| **Chat Input** | Text input with attachment + code + mic icons |
| **System Variation Table** | Two-column table (orchestrator name + ID) |
| **Available Agents Table** | Name + status pill per row |
| **Red Team Test Card** | Empty state + CTA, or test list view |
| **Agent Turn Card** | Expandable turn with role label + expand button |
| **Notification Banner** | Full-width colored banner with icon + dismiss |
| **Info Tile** | Title + body + optional tag |
| **Metric Row** | 4-5 stat cards in a horizontal row |
| **Feedback Panel** | Total/positive/negative/rating/satisfaction stat cards |

### 9.2 Chat Input Widget

```jsx
<div className="bg-white border border-gray-200 rounded-xl">
  <div className="px-4 py-3">
    <input
      type="text"
      placeholder="What would you like to know?"
      className="w-full text-sm text-gray-900 placeholder-gray-400 focus:outline-none"
    />
  </div>
  <div className="px-4 py-2 border-t border-gray-100 flex items-center gap-3">
    <button className="text-gray-400 hover:text-gray-600"><AttachIcon className="w-5 h-5" /></button>
    <button className="text-gray-400 hover:text-gray-600"><CodeIcon className="w-5 h-5" /></button>
    <button className="text-gray-400 hover:text-gray-600"><MicIcon className="w-5 h-5" /></button>
    <div className="flex-1" />
    <button className="bg-brand-600 text-white p-2 rounded-lg">
      <SendIcon className="w-4 h-4" />
    </button>
  </div>
</div>
```

### 9.3 Available Agents Table

```jsx
<div className="bg-white border border-gray-200 rounded-xl">
  <div className="px-6 py-4 flex items-center justify-between border-b border-gray-200">
    <h3 className="text-sm font-semibold text-gray-900">Available Agents</h3>
    <span className="text-xs text-gray-500">Past 20 Seconds</span>
  </div>
  <div className="divide-y divide-gray-100">
    {agents.map(agent => (
      <div key={agent.name} className="px-6 py-3 flex items-center justify-between">
        <span className="text-sm text-gray-700">{agent.name}</span>
        <span className={`text-xs font-medium px-2.5 py-0.5 rounded-full
          ${agent.status === 'Active'
            ? 'bg-success-50 text-success-700'
            : 'bg-error-50 text-error-700'
          }`}>
          {agent.status}
        </span>
      </div>
    ))}
  </div>
</div>
```

---

## 10. Smaller Widgets & Inputs

### 10.1 Text Input / Textarea

```jsx
{/* Standard Input */}
<div>
  <label className="block text-sm font-medium text-gray-700 mb-1.5">
    Your message:
  </label>
  <input
    type="text"
    placeholder="Type your message here"
    className="w-full px-3.5 py-2.5 border border-gray-300 rounded-lg text-sm text-gray-900
               placeholder-gray-400 focus:border-brand-300 focus:ring-4 focus:ring-brand-100
               focus:outline-none transition-colors"
  />
  <p className="text-sm text-gray-500 mt-1.5">
    Your message will be copied to the support team.
  </p>
</div>

{/* Textarea */}
<div>
  <label className="block text-sm font-medium text-gray-700 mb-1.5">
    Your message:
  </label>
  <textarea
    rows={4}
    placeholder="Type your message here"
    className="w-full px-3.5 py-2.5 border border-gray-300 rounded-lg text-sm text-gray-900
               placeholder-gray-400 focus:border-brand-300 focus:ring-4 focus:ring-brand-100
               resize-none"
  />
</div>
```

### 10.2 Email Subscribe Input

```jsx
<div className="flex gap-2">
  <div className="flex-1">
    <label className="block text-sm font-medium text-gray-700 mb-1.5">Email</label>
    <input
      type="email"
      placeholder="Enter your email address"
      className="w-full px-3.5 py-2.5 border border-gray-300 rounded-lg text-sm"
    />
  </div>
  <button className="self-end px-4 py-2.5 bg-brand-600 text-white text-sm font-semibold rounded-lg">
    Subscribe
  </button>
</div>
```

### 10.3 Dropdown / Select Menu

```jsx
<div className="bg-white border border-gray-200 rounded-lg shadow-lg py-1 min-w-[200px]">
  <div className="px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 cursor-pointer flex items-center justify-between">
    <span>Keyword</span>
    <span className="text-xs text-gray-400">⌘1</span>
  </div>
  <div className="px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 cursor-pointer flex items-center justify-between">
    <span>Reword</span>
    <span className="text-xs text-gray-400">⌘2</span>
  </div>
  <div className="border-t border-gray-100 my-1" />
  <div className="px-3 py-2 text-sm text-gray-700 hover:bg-gray-50 cursor-pointer">
    More Tools
  </div>
</div>
```

### 10.4 Tabs / Navigation Pills

```jsx
{/* Underline Tabs */}
<div className="flex border-b border-gray-200">
  <button className="px-4 py-3 text-sm font-semibold text-brand-600 border-b-2 border-brand-600">
    Getting started
  </button>
  <button className="px-4 py-3 text-sm text-gray-500 hover:text-gray-700">
    Components
  </button>
  <button className="px-4 py-3 text-sm text-gray-500 hover:text-gray-700">
    Documentation
  </button>
</div>

{/* Pill Tabs */}
<div className="flex gap-2 p-1 bg-gray-100 rounded-lg">
  <button className="px-3 py-1.5 text-sm font-medium bg-white text-gray-900 rounded-md shadow-sm">
    Default
  </button>
  <button className="px-3 py-1.5 text-sm text-gray-500 rounded-md">
    Automatic
  </button>
</div>
```

### 10.5 Toggle / Radio

```jsx
{/* Toggle Group */}
<div className="flex items-center gap-4">
  <label className="flex items-center gap-2 cursor-pointer">
    <div className="relative">
      <input type="radio" name="mode" className="sr-only peer" defaultChecked />
      <div className="w-4 h-4 rounded-full border-2 border-gray-300 peer-checked:border-brand-600 peer-checked:border-[5px]" />
    </div>
    <span className="text-sm text-gray-700">Allowance mode</span>
  </label>
  <label className="flex items-center gap-2 cursor-pointer">
    <div className="relative">
      <input type="radio" name="mode" className="sr-only peer" />
      <div className="w-4 h-4 rounded-full border-2 border-gray-300 peer-checked:border-brand-600 peer-checked:border-[5px]" />
    </div>
    <span className="text-sm text-gray-700">Allowance mode</span>
  </label>
</div>
```

### 10.6 Checkbox

```jsx
<label className="flex items-start gap-3 cursor-pointer">
  <input type="checkbox" className="mt-0.5 w-4 h-4 rounded border-gray-300 text-brand-600 focus:ring-brand-500" />
  <div>
    <p className="text-sm font-medium text-gray-700">Accept terms and condition</p>
    <p className="text-sm text-gray-500">
      You agree to our Terms of Service and Privacy Policy.
    </p>
  </div>
</label>
```

### 10.7 Badge / Pill Component

```jsx
{/* Status Badges */}
<span className="inline-flex items-center gap-1 px-2 py-0.5 text-xs font-medium rounded-full bg-success-50 text-success-700">
  <span className="w-1.5 h-1.5 rounded-full bg-success-500" />
  Active
</span>

<span className="inline-flex items-center gap-1 px-2 py-0.5 text-xs font-medium rounded-full bg-error-50 text-error-700">
  <span className="w-1.5 h-1.5 rounded-full bg-error-500" />
  Inactive
</span>

<span className="inline-flex items-center gap-1 px-2 py-0.5 text-xs font-medium rounded-full bg-brand-50 text-brand-700">
  Version 1
</span>
```

---

## 11. Tailwind Config Reference

Below is the `tailwind.config.js` extension to register all of the design tokens above so that you can use them as native utility classes.

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        display: ['"Unilever Desire"', 'serif'],
        sans: ['Inter', 'system-ui', 'sans-serif'],
      },
      colors: {
        brand: {
          25:  '#FCFAFF',
          50:  '#F9F5FF',
          100: '#F4EBFF',
          200: '#E9D7FE',
          300: '#D6BBFB',
          400: '#B692F6',
          500: '#9E77ED',
          600: '#6941C6',
          700: '#7F56D9',
          800: '#53389E',
          900: '#42307D',
        },
        gray: {
          25:  '#FCFCFD',
          50:  '#F9FAFB',
          100: '#F2F4F7',
          200: '#E4E7EC',
          300: '#D0D5DD',
          400: '#98A2B3',
          500: '#667085',
          600: '#475467',
          700: '#344054',
          800: '#1D2939',
          900: '#101828',
        },
        error: {
          25:  '#FFFBFA',
          50:  '#FEF3F2',
          100: '#FEE4E2',
          200: '#FECDCA',
          300: '#FDA29B',
          400: '#F97066',
          500: '#F04438',
          600: '#D92D20',
          700: '#B42318',
          800: '#912018',
          900: '#7A271A',
        },
        warning: {
          25:  '#FFFCF5',
          50:  '#FFFAEB',
          100: '#FEF0C7',
          200: '#FEDF89',
          300: '#FEC84B',
          400: '#FDB022',
          500: '#F79009',
          600: '#DC6803',
          700: '#B54708',
          800: '#93370D',
          900: '#7A2E0E',
        },
        success: {
          25:  '#F6FEF9',
          50:  '#ECFDF3',
          100: '#D1FADF',
          200: '#A6F4C5',
          300: '#6CE9A6',
          400: '#32D583',
          500: '#12B76A',
          600: '#039855',
          700: '#027A48',
          800: '#05603A',
          900: '#054F31',
        },
        bluegray: {
          25:  '#FCFCFD',
          50:  '#F8F9FC',
          100: '#EAECF5',
          200: '#D5D9EB',
          300: '#AFB5D9',
          400: '#717BBC',
          500: '#4E5BA6',
          600: '#3E4784',
          700: '#363F72',
          800: '#293056',
          900: '#101323',
        },
        blue: {
          25:  '#F5FAFF',
          50:  '#EFF8FF',
          100: '#D1E9FF',
          200: '#B2DDFF',
          300: '#84CAFF',
          400: '#53B1FD',
          500: '#2E90FA',
          600: '#1570EF',
          700: '#175CD3',
          800: '#1849A9',
          900: '#194185',
        },
        purple: {
          25:  '#FAFAFF',
          50:  '#F4F3FF',
          100: '#EBE9FE',
          200: '#D9D6FE',
          300: '#BDB4FE',
          400: '#9B8AFB',
          500: '#7A5AF8',
          600: '#6938EF',
          700: '#5925DC',
          800: '#4A1FB8',
          900: '#3E1C96',
        },
      },
      borderRadius: {
        'xs': '4px',
        'sm': '6px',
        'md': '8px',
        'lg': '12px',
        'xl': '16px',
        '2xl': '20px',
        'full': '9999px',
      },
      boxShadow: {
        'xs': '0px 1px 2px rgba(16, 24, 40, 0.05)',
        'sm': '0px 1px 3px rgba(16, 24, 40, 0.1), 0px 1px 2px rgba(16, 24, 40, 0.06)',
        'md': '0px 4px 8px -2px rgba(16, 24, 40, 0.1), 0px 2px 4px -2px rgba(16, 24, 40, 0.06)',
        'lg': '0px 12px 16px -4px rgba(16, 24, 40, 0.08), 0px 4px 6px -2px rgba(16, 24, 40, 0.03)',
        'xl': '0px 20px 24px -4px rgba(16, 24, 40, 0.08), 0px 8px 8px -4px rgba(16, 24, 40, 0.03)',
      },
    },
  },
};
```

### CSS Variables Alternative (for non-Tailwind setups)

```css
:root {
  /* Brand */
  --color-brand-600: #6941C6;
  --color-brand-700: #7F56D9;
  --color-brand-50: #F9F5FF;

  /* Gray */
  --color-gray-900: #101828;
  --color-gray-700: #344054;
  --color-gray-500: #667085;
  --color-gray-300: #D0D5DD;
  --color-gray-200: #E4E7EC;
  --color-gray-50: #F9FAFB;

  /* Spacing */
  --spacing-1: 0.25rem;  /* 4px */
  --spacing-2: 0.5rem;   /* 8px */
  --spacing-3: 0.75rem;  /* 12px */
  --spacing-4: 1rem;     /* 16px */
  --spacing-6: 1.5rem;   /* 24px */
  --spacing-8: 2rem;     /* 32px */
  --spacing-16: 4rem;    /* 64px */

  /* Typography */
  --font-display: 'Unilever Desire', serif;
  --font-body: 'Inter', system-ui, sans-serif;
}
```

---

## Quick Cheat Sheet

| What You Need | Tailwind Classes |
|---|---|
| Primary button | `bg-brand-600 hover:bg-brand-700 text-white px-4 py-2.5 text-sm font-semibold rounded-lg` |
| Secondary button | `bg-white border border-gray-300 text-gray-700 hover:bg-gray-50 px-4 py-2.5 text-sm font-semibold rounded-lg` |
| Destructive button | `bg-error-600 hover:bg-error-700 text-white px-4 py-2.5 text-sm font-semibold rounded-lg` |
| Card container | `bg-white border border-gray-200 rounded-xl shadow-sm` |
| Card padding | `p-6` (24px) |
| Section gap | `space-y-6` or `gap-6` |
| Body text | `text-base text-gray-700 leading-6` |
| Supporting text | `text-sm text-gray-500` |
| Page heading | `text-3xl font-bold text-gray-900` |
| Input field | `w-full px-3.5 py-2.5 border border-gray-300 rounded-lg text-sm focus:ring-4 focus:ring-brand-100 focus:border-brand-300` |
| Status badge (success) | `bg-success-50 text-success-700 px-2 py-0.5 text-xs font-medium rounded-full` |
| Status badge (error) | `bg-error-50 text-error-700 px-2 py-0.5 text-xs font-medium rounded-full` |
| Modal overlay | `fixed inset-0 bg-gray-900/60 flex items-center justify-center z-50` |
| Modal container | `bg-white rounded-xl shadow-xl w-full max-w-lg` |

---

*Generated from Figma Design System 2.0 — Project Habibi Components page. For questions, reach out to the design team or reference the Figma file directly.*
