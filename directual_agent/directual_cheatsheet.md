# 📋 DIRECTUAL TECHNICAL CHEAT SHEET
## Быстрый справочник ключевых принципов и команд

---

## 🏗 АРХИТЕКТУРНЫЕ ПРИНЦИПЫ

### Правило MVP-Scale
```
1. START SIMPLE → 2-3 объекта в базе, базовый API, простой UI
2. ADD LOGIC → Scenarios для автоматизации, интеграции 
3. OPTIMIZE → Сложные workflows, performance tuning
4. SCALE → Multiple environments, team collaboration
```

### Иерархия планирования проекта
```
БАЗА → ЛОГИКА → ИНТЕРФЕЙС → ИНТЕГРАЦИИ
   ↓        ↓         ↓          ↓
Database  API    Scenarios   UI    Webhooks
Objects   CRUD   Automation  Pages External
```

---

## 🗄️ DATABASE PATTERNS

### Типовые структуры объектов:

#### User Management System
```
Users: {id, email, name, role, status, created_date}
Roles: {id, name, permissions}
Sessions: {id, user_id, token, expires_at}
```

#### E-commerce Base
```
Products: {id, name, price, category_id, stock, images}
Categories: {id, name, parent_id}
Orders: {id, user_id, total, status, created_date}
Order_Items: {id, order_id, product_id, quantity, price}
```

#### CRM Foundation
```
Contacts: {id, name, email, company_id, status, tags}
Companies: {id, name, industry, size, website}
Deals: {id, contact_id, amount, stage, probability}
Activities: {id, contact_id, type, date, notes}
```

### Связи между объектами:
```
- ONE-TO-MANY: User → Orders, Company → Contacts
- MANY-TO-MANY: Products ↔ Categories, Users ↔ Roles  
- ONE-TO-ONE: User → Profile, Order → Payment
```

---

## ⚡ SCENARIOS COOKBOOK

### Event-Based Triggers
```
ON CREATE object → Welcome email, Initial setup
ON UPDATE object → Notifications, Data sync
ON DELETE object → Cleanup tasks, Archive data
```

### Scheduled Scenarios
```
DAILY: Reports, Data cleanup, Reminders
WEEKLY: Analytics, Backups, Summaries  
MONTHLY: Billing, Performance reviews
CUSTOM CRON: Every 15 minutes, First Monday, etc.
```

### HTTP Integration Pattern
```
1. HTTP REQUEST step
2. JSON PARSE response
3. CONDITION check (success/error)
4. CREATE/UPDATE objects with data
5. ERROR HANDLING (retry logic)
```

### Email Automation Template
```
TRIGGER → GET user data → COMPOSE email content → 
SEND via integration → LOG activity → ERROR handling
```

---

## 🎨 UI COMPONENT GUIDE

### Data Display Components
```
TABLE: 
- Best for: Lists, CRUD operations, filtering
- Config: API endpoint, columns, actions, pagination

CARDS:
- Best for: Visual catalogs, dashboards  
- Config: Template design, data binding, click actions

KANBAN:
- Best for: Task management, status tracking
- Config: Columns (statuses), card template, drag-drop
```

### Form Components
```
SIMPLE FORM:
- Single object create/edit
- Field types: text, select, file, date
- Validation: required, format, custom

MULTI-STEP FORM:
- Complex data entry
- Conditional steps, progress indicator
- Save draft functionality
```

### Navigation Patterns
```
PUBLIC AREA: Landing, About, Contact, Login
AUTHENTICATED: Dashboard, Profile, Main features  
ADMIN AREA: User management, Settings, Analytics
```

---

## 🔗 INTEGRATION PATTERNS

### Webhook Setup Flow
```
1. CREATE webhook in API section
2. COPY webhook URL  
3. CONFIGURE external service (Stripe, GitHub, etc.)
4. CREATE scenario to PROCESS incoming data
5. TEST with real payload
```

### External API Integration
```
1. GET API credentials (key, secret, tokens)
2. CREATE HTTP request scenario step
3. ADD authentication headers
4. PARSE JSON response  
5. MAP data to Directual objects
6. HANDLE errors and rate limits
```

### Common Integration Examples
```
PAYMENT: Stripe webhooks → Order updates
EMAIL: Resend/SendGrid → Transactional emails  
COMMUNICATION: Telegram Bot API → Customer support
STORAGE: Google Drive API → File management
ANALYTICS: Google Analytics → Usage tracking
```

---

## 📊 PERFORMANCE OPTIMIZATION

### Database Optimization
```
- Use FILTERS in API calls (don't load everything)
- PAGINATE large datasets (50-100 items per page)
- INDEX frequently queried fields
- ARCHIVE old data instead of deleting
```

### Scenario Optimization  
```
- MINIMIZE HTTP requests per scenario
- USE batch operations when possible
- CACHE frequently accessed data
- OPTIMIZE scenario execution order
```

### UI Performance
```
- LAZY LOAD heavy components
- OPTIMIZE images (compress, appropriate sizes)
- MINIMIZE API calls per page
- USE real-time updates sparingly
```

---

## 🚨 COMMON ERRORS & FIXES

### "API returns 403 Forbidden"
```
CHECK:
- API endpoint permissions (public/role-based)
- User authentication status
- Correct API headers (Authorization, Content-Type)
```

### "Scenario doesn't trigger"
```
CHECK:
- Object permissions for scenario execution
- Trigger conditions (event type, filters)
- Scenario is ACTIVE status
- Debug logs for error details
```

### "Data not showing in UI"
```
CHECK:  
- Component data source configuration
- API endpoint returns data (test in API section)
- Component filters and conditions
- User permissions for data access
```

### "Webhook not receiving data"
```
CHECK:
- Webhook URL is correct and active
- External service webhook configuration
- Payload format matches expected structure
- Firewall/security settings
```

---

## 💰 PLAN LIMITATIONS GUIDE

### Free Plan
```
LIMITS:
- 1,000 API calls/month
- 1 GB storage  
- Basic integrations only
- Directual subdomain only

BEST FOR: Prototyping, learning, simple MVPs
```

### Startup Plan ($29/month)
```
LIMITS:
- 10,000 API calls/month
- 10 GB storage
- Custom domain
- All integrations

BEST FOR: Small apps, side projects, early startups
```

### Pro Plan ($99/month)
```
LIMITS:
- 100,000 API calls/month
- 100 GB storage  
- Team collaboration
- Advanced analytics

BEST FOR: Growing businesses, production apps
```

---

## 🎯 BEST PRACTICES CHECKLIST

### Security
```
☐ Use role-based permissions properly
☐ Validate all user inputs
☐ Store sensitive data securely (no plain text passwords)
☐ Use HTTPS for all endpoints
☐ Implement proper authentication
```

### Performance
```
☐ Optimize database queries with filters
☐ Use pagination for large datasets
☐ Cache frequently accessed data
☐ Minimize scenario complexity
☐ Monitor API usage limits
```

### User Experience  
```
☐ Clear navigation structure
☐ Responsive design for mobile
☐ Fast loading times
☐ Intuitive forms and interfaces
☐ Proper error messages
```

### Development Process
```
☐ Start with MVP, iterate quickly
☐ Test scenarios with real data
☐ Document complex logic
☐ Use version control mindset
☐ Plan for scalability from start
```

---

## 🔧 DEBUGGING TOOLKIT

### Scenario Debugging
```
1. Use DEBUG mode in scenario builder
2. Check LOGS for each step execution
3. Test with MANUAL trigger first
4. Verify object PERMISSIONS
5. Check JSON SYNTAX in complex steps
```

### API Debugging
```
1. Test endpoints in BUILT-IN tester
2. Check RESPONSE format and status codes
3. Verify REQUEST headers and body
4. Use EXTERNAL tools (Postman) for validation
5. Check AUTHENTICATION requirements
```

### UI Debugging
```
1. Check BROWSER console for errors
2. Verify DATA SOURCE connections  
3. Test COMPONENT filters and conditions
4. Check USER permissions and roles
5. Validate RESPONSIVE design on devices
```

---

## 🚀 QUICK START TEMPLATES

### Internal Tool (30 min setup)
```
1. Create Users object + basic fields
2. Create main entity object (Tasks, Tickets, etc.)
3. Set up CRUD API endpoints
4. Build simple table view + form
5. Add basic user authentication
```

### E-commerce MVP (2 hour setup)
```
1. Create Products, Categories, Orders objects
2. Set up product catalog API
3. Build product listing + detail pages
4. Create shopping cart functionality  
5. Integrate payment gateway (Stripe)
```

### Telegram Bot (1 hour setup)
```
1. Create Bot via BotFather
2. Set up webhook in Directual
3. Create message processing scenario
4. Add bot commands logic
5. Test with real Telegram messages
```

---

**Сохраните этот cheat sheet для быстрого доступа к ключевой информации при работе с Directual!**