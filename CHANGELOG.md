# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [Unreleased]

### Added
- `index.html`: Homepage skeleton với cấu trúc semantic HTML5 (`<nav>`, `<section>`)
- `style.css`: Stylesheet toàn cục với CSS variables và reset
- **Navbar module**
  - Logo placeholder (`div.nav-logo`) nằm ở main start
  - 3 nav links: "Sản phẩm", "Lịch sử", "Về chúng tôi" nằm ở main end
  - Layout: Flexbox với `justify-content: space-between`
  - Background color: Sea blue (`#006994`)
  - Item background: Smoke white 30% transparent (`rgba(245, 245, 245, 0.70)`)
  - Margin đều 4 cạnh cho logo và từng nav item (`margin: 10px`)
  - Hover states cho logo và nav links
- **Hero section** (homepage placeholder)
  - Headline, subtext, CTA button
  - Visual placeholder cards (sea blue + accent gold)
  - Responsive typography với `clamp()`
- Google Fonts: Playfair Display (display) + DM Sans (body)

### Changed
- **Mobile First** applied via CSS Container Queries (`@container`)
  - `div.navbar-wrapper` và `div.hero-wrapper` bọc ngoài làm container context
  - Navbar base (mobile): `flex-wrap: wrap`, links xuống dòng, căn center, full width
  - Navbar `@container navbar (min-width: 600px)`: links về main end, single row
  - Hero base (mobile): stack dọc, text căn center, visual cards ẩn
  - Hero `@container hero (min-width: 640px)`: visual cards hiện, vẫn stack
  - Hero `@container hero (min-width: 900px)`: layout 2 cột side-by-side, text căn trái
- **Logo positioning** refactored via flex column zone
  - Bọc `div.nav-logo` trong `div.nav-logo-zone`
  - `nav-logo-zone`: `flex-direction: column`, `justify-content: flex-start` (main start = top), `align-items: center` (center cross axis = giữa ngang), `width: 100%` trên mobile
  - Logo hiển thị top-center của navbar trên mobile

### Fixed
- **Navbar tablet+ layout** — reset mobile styles bị rò rỉ sang breakpoint ≥600px
  - `.nav-logo-zone`: thêm `width: auto` và `align-items: flex-start` tại `@container navbar (min-width: 600px)` → logo về main start (trái)
  - `.nav-links`: thêm `flex-wrap: nowrap` tại tablet+ → 3 links luôn trên 1 hàng

## [Unreleased — v3]

### Added
- **Footer module** — cùng style design với navbar
  - Layout: `display: flex; justify-content: space-between; align-items: center; min-height: var(--footer-min-height)`
  - 3 section theo thứ tự: `footer-contact` (gmail + SĐT) | `footer-copyright` (logo placeholder + © text) | `footer-brand` (logo placeholder)
  - `footer-item`: smoke-white bg, `border-radius: 6px`, hover state — cùng pattern navbar links
  - `footer-copy`: smoke-white bg, font-size nhỏ hơn (`0.78rem`)
  - `footer-wrapper`: `box-shadow: 0 -2px 16px` để tạo depth từ dưới lên
- **CSS variables mới** trong `:root`
  - `--smoke-border: rgba(245, 245, 245, 0.50)` — dùng cho border logo placeholder
  - `--footer-min-height: 25vh` — chiều cao tối thiểu footer
  - `--footer-padding: 0 1.5rem` — padding footer

### Changed
- **`.logo-placeholder`** — class dùng chung thay thế `.nav-logo`
  - Border đổi từ `dashed` → `solid var(--smoke-border)` (data-driven)
  - Áp dụng cho: navbar logo, footer copyright logo frame, footer brand logo
- `nav-logo` div trong HTML đổi class → `logo-placeholder`

## [Unreleased — v2]

### Changed
- **Hero section** refactored sang Desktop First, 3-column Grid Layout
  - Xóa `div.hero-visual` (+ `.hero-card`, `.hero-card--sm`) khỏi HTML và CSS
  - `section.hero`: chuyển từ `display: flex` → `display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem`
  - Đổi `div.hero-content` → `div.hero-content1`; thêm `div.hero-content2`, `div.hero-content3` (trống, chờ fill)
  - Xóa toàn bộ `@container hero` breakpoint blocks cũ (mobile responsive để feature sau)

### Added
- **Hero col 2 & col 3** — fill nội dung và mobile responsive
  - `hero-content2`: chủ đề "Cam kết chất lượng" — label, title, sub, CTA
  - `hero-content3`: chủ đề "Dịch vụ tận tâm" — label, title, sub, CTA
  - Mobile `@container hero (max-width: 639px)`: `grid-template-columns: 1fr` — 3 cột collapse thành 3 hàng, gutter giữ nguyên `1.5rem`
### Fixed
- **Hero desktop layout** — căn giữa nội dung và thu nhỏ font size h1
  - `.hero-content1/2/3`: thêm `text-align: center` và `align-items: center` → h1 và CTA căn giữa cột
  - `.hero-cta`: đổi `align-self: flex-start` → `align-self: center`
  - `.hero-title`: đổi `font-size` từ `clamp(2.4rem, 8vw, 5.5rem)` → `clamp(1.8rem, 2.8vw, 2.8rem)` — vừa với 3-col layout, không wrap

- **Hero column dividers & CTA alignment**
  - Mỗi `hero-content*`: `display: flex; flex-direction: column; position: relative`
  - `::after` pseudo-element trên `hero-content1`, `hero-content2`: line `1.5px` màu `var(--accent)` nằm chính giữa gutter (`right: -0.75rem`)
  - Desktop: line dọc (`width: 1.5px; height: 100%`)
  - Mobile: override thành line ngang (`width: 100%; height: 1.5px; bottom: -0.75rem`)
  - `.hero-cta`: `margin-top: auto` — đẩy CTA xuống đáy mỗi col, align cùng hàng ngang nhau
