# Qriza - Dynamic QR Content Platform

**A modern Flutter-based SaaS platform that lets any business (hotels, restaurants, sweet shops, electronics stores, retail, clinics, gyms, etc.) create beautiful, dynamic QR codes linked to digital menus, fillable forms, instruction guides, and rich content pages.**

Built entirely with **Flutter** (web + mobile) + **Supabase** in 2026.

**Tagline**: Scan the Horizon

---

## 🎯 Overview

Qriza solves the problem of outdated paper-based materials in businesses. Shop owners can instantly update menus, prices, instructions, or forms without reprinting anything. Customers simply scan a QR code placed on tables, products, packaging, or receipts and get a fast, branded, mobile-optimized experience.

**Core Idea**: One dynamic QR code → Always up-to-date digital content that opens a new horizon of engagement.

**Target Users**:
- Hotel & Restaurant owners
- Sweet shops & Cafes
- Electronics & Gadget stores
- Retail shops
- Service centers, clinics, gyms, schools, and more

---

## ✨ Key Features

### For Business Owners (Dashboard)
- **Beautiful Dashboard** built in Flutter Web
- **AI-Powered Content Generator** (generate full menus, forms, or instructions from a simple text prompt)
- **Drag & Drop Menu Builder** (dishes, categories, prices, photos, allergens, customizations)
- **Advanced Form Builder** (feedback, lead capture, service requests, warranty registration, quick orders)
- **Rich Instruction Pages** (step-by-step guides, videos, images, PDFs, checklists)
- **Dynamic QR Code Generator** with custom branding, colors, logo, and shapes
- **Multiple QR Types**:
  - Table QR (menu + order form)
  - Product QR (manual + warranty form)
  - Room QR (hotel instructions + service request)
  - General QR (any custom page)
- **Real-time Analytics** (scans, locations, form submissions, popular items)
- **Multi-language Support** (AI auto-translation)
- **Custom Domain** & White-label (premium plans)
- **Team & Organization Management**

### For Customers (After Scanning QR)
- Lightning-fast **Progressive Web App (PWA)** experience
- Offline support for menus and instructions
- Beautiful, fully responsive design that matches the business branding
- Fillable forms with real-time validation
- Image galleries, embedded videos, and rich text
- One-tap actions (WhatsApp, Call, Directions)
- Dark/Light mode + accessibility features

---

## 🛠 Tech Stack (2026 Best Practices)

| Layer                | Technology                                      | Reason |
|----------------------|--------------------------------------------------|--------|
| **Frontend**         | **Flutter 3.29+** (Impeller + Wasm)             | Single codebase for Web, Android, iOS, Desktop |
| **State Management** | Riverpod 2.5+                                   | Scalable, testable, and performant |
| **Routing**          | GoRouter + Deep Linking                         | Perfect for QR deep links |
| **Backend**          | **Supabase** (PostgreSQL + Auth + Storage + Edge Functions) | Open-source, SQL power, realtime |
| **UI Components**    | Custom widgets + `flutter_form_builder`, `flutter_quill`, `syncfusion_flutter_charts` | Rich forms, editor, analytics |
| **QR Generation**    | `qr_flutter` + `qr_code_styling`                | Beautiful branded QRs |
| **AI Integration**   | Grok API (xAI) / Gemini 2.0 / OpenAI            | Smart content generation & translation |
| **Payments**         | Stripe + Supabase Edge Functions                | Subscription billing |
| **Analytics**        | Supabase + PostHog                              | Privacy-friendly tracking |
| **Deployment**       | - Web → Vercel / Firebase Hosting<br>- Mobile → App Store + Play Store<br>- PWA → Cloudflare | Global edge performance |
| **Authentication**   | Supabase Auth + Social & Magic links            | Organizations & multi-tenant support |

---

## 📊 Database Schema (Supabase)

**Main Tables**:

- `organizations` (id, name, logo, plan, custom_domain)
- `users` (Supabase auth + organization_id)
- `qr_codes` (id, organization_id, title, type, slug, is_active, settings JSONB)
- `content_pages` (id, qr_code_id, title, content JSONB, version)
- `menus` (id, organization_id, categories JSONB, items JSONB)
- `forms` (id, organization_id, schema JSONB)
- `form_responses` (id, form_id, data JSONB, scanned_from_qr)
- `analytics_scans` (qr_code_id, timestamp, location, device_info)
- `subscriptions` (organization_id, stripe_id, status, plan)

All tables use Row Level Security (RLS) for secure multi-tenant isolation.

---

## 📁 Project Folder Structure

```bash
qriza/
├── lib/
│   ├── core/                  # Constants, themes, extensions, config
│   ├── features/
│   │   ├── auth/
│   │   ├── dashboard/
│   │   ├── qr_generator/
│   │   ├── menu_builder/
│   │   ├── form_builder/
│   │   ├── content_editor/
│   │   ├── analytics/
│   │   └── public/            # Public QR pages (menu, form, instructions)
│   ├── shared/                # Reusable widgets, models, services
│   ├── providers/             # Riverpod providers
│   └── main.dart
├── supabase/
│   ├── migrations/
│   └── functions/             # Edge Functions (Stripe, AI calls)
├── assets/
│   ├── images/
│   └── icons/
├── web/                       # Web-specific (manifest, index.html)
├── test/
├── analysis_options.yaml
├── pubspec.yaml
└── README.md