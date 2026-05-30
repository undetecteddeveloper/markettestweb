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
