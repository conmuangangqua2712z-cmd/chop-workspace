---
name: "frontend-design-guidance"
description: "Design guidance for distinctive frontend UI — avoid generic AI aesthetics"
---

# frontend-design-guidance

Tạo frontend UI distinctive, production-grade, không generic AI.

## Trigger

Use this skill when working on frontend code, designing UI, creating web interfaces.
Trigger phrases: "build UI", "create frontend", "design interface", "make it look good", "web design", "frontend"

## Core Principles

### Avoid AI-Generic Aesthetics
- Không dùng gradient pastel mặc định
- Không dùng card trắng bo tròn + shadow kiểu mặc định
- Không dùng màu xanh primary #3B82F6 hoặc slate backgrounds
- Typography phải có cá tính, không dùng system font stack mặc định

### Typography
- Font chữ có personality (Inter, JetBrains Mono, Fraunces, DM Sans...)
- Size scale rõ ràng (12/14/16/20/24/32/48...)
- Line-height: 1.5 cho body, 1.1-1.2 cho headings
- Letter-spacing cho headings: -0.02em đến -0.01em

### Color
- Bảng màu có chủ đích, không random
- Neutral colors ấm hoặc lạnh hẳn (không pure gray #888)
- Accent color nên unique, có personality
- Dark mode phải được design, không invert tự động

### Spacing & Layout
- Dùng consistent spacing scale (4/8/12/16/24/32/48/64/96)
- Content width có giới hạn (640-800px cho text, 1200px cho layouts)
- Negative space là bạn — đừng sợ空白

### Animations
- Subtle micro-interactions (hover, focus, transitions)
- Không animation rẻ tiền (spin, flash, rainbow)
- Duration: 150-300ms cho micro, 300-500ms cho transitions
- Easing: ease-out cho UI, ease-in-out cho overlays

### Details That Matter
- Focus states rõ ràng cho accessibility
- Loading states (skeleton > spinner)
- Empty states có illustration hoặc message
- Error states friendly, actionable

## Code Patterns

### CSS Strategy
```css
/* Dùng CSS custom properties cho theme */
:root {
  --font-sans: 'Inter', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --color-bg: #faf9f8;
  --color-text: #1a1a1a;
  --color-accent: #6c5ce7;
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 48px;
  --radius: 6px;
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
}
```

### Component Structure
```tsx
// Mỗi component: 1 file, rõ ràng, có loading/error states
interface ButtonProps {
  variant: 'primary' | 'secondary' | 'ghost';
  size: 'sm' | 'md' | 'lg';
  children: React.ReactNode;
  loading?: boolean;
  disabled?: boolean;
  onClick?: () => void;
}
```
