# Online Book Store 📚🛒

## 📌 Introduction

**Online Book Store** is a Java EE web application that provides a complete bookstore experience with account management, catalog browsing, search, cart, checkout, book details, comments/ratings, and past order viewing.

The UI is implemented using JSP + JSTL with jQuery-based dynamic sections, while business operations are exposed through servlet endpoints configured in deployment descriptors.

**Key Features:**
- ✅ User registration and login/logout
- ✅ Profile update in My Account section
- ✅ Browse books by category
- ✅ Search books by title, author, and category
- ✅ Book details view with AJAX loading
- ✅ Add rating/comment flow via dedicated endpoint
- ✅ Session-based shopping cart with total calculation
- ✅ Checkout with shipping address validation
- ✅ Past order viewing
- ✅ SQL schema and seed data initializer provided

---

## 🔄 Process / Flow

**User Flow:**
1. User lands on `index.jsp` and category list is loaded asynchronously.
2. Guest can register (`register.jsp`) or login (`login.jsp`).
3. User browses by category or searches books from `search.jsp`.
4. Book details are fetched via `GetBookDetails` and shown on `details.jsp`.
5. User adds books to cart and reviews cart via `ViewShoppingCart`.
6. Checkout requires authenticated user and non-empty cart (`checkout.jsp`).
7. Shipping address is submitted to `CheckOut` endpoint.
8. User can open My Account and view past orders via `ViewPastOrders`.

**Backend Endpoint Flow (from deployment config):**
1. Catalog: `ListCategories`, `ListCategoryBooks`, `SearchBooks`, `GetBookDetails`
2. User: `Register`, `Login`, `UpdateProfile`
3. Engagement: `AddComment`
4. Cart & Orders: `ViewShoppingCart`, `UpdateCart`, `CheckOut`, `ViewPastOrders`

---

## 🛠️ Technology Used

| Component | Technology |
|-----------|-----------|
| **Backend** | Java EE (Servlets, JSP) |
| **View Layer** | JSP + JSTL (`c`, `fmt`) |
| **Frontend Scripting** | JavaScript, jQuery, jQuery UI |
| **UI Utilities** | Lightbox, Scriptaculous, Prototype |
| **Database** | Relational DB via SQL schema (`users`, `book`, `orders`, etc.) |
| **App Server** | GlassFish (deployment descriptors included) |
| **Build/Deploy Metadata** | Ant `build.xml`, `application.xml`, `web.xml` |

---

## 🎓 Skills Gained

**Java EE Web Development:**
- ✅ Configuring servlet mappings and web descriptors
- ✅ Building JSP pages with JSTL and session-aware rendering
- ✅ Integrating EJB reference declarations in web config

**E-Commerce Flow Implementation:**
- ✅ Session cart handling and currency formatting
- ✅ Checkout validation and order history retrieval
- ✅ User lifecycle flows (register, login, profile update)

**Database Design:**
- ✅ Designing relational schema for users, books, comments, orders, and order lines
- ✅ Preparing database seed scripts for local setup/testing

---

## 📂 Project Structure

```
Online_Book_Store/
├── README.md                          # Primary project documentation
├── README.txt                         # Deployment notes and implemented features list
├── build.xml                          # Ant build configuration
├── application.xml                    # Enterprise app descriptor
├── web.xml                            # Servlet mappings, session config, EJB refs
├── glassfish-web.xml                  # GlassFish web deployment settings
├── glassfish-application.xml          # GlassFish app-level deployment settings
├── sun-web.xml                        # Sun/GlassFish specific web config
├── sun-application.xml                # Sun/GlassFish application config
├── database_initializer.sql           # DB schema + sample data
├── index.jsp                          # Home page and cart/category initialization
├── category.jsp                       # Book category browsing view
├── search.jsp                         # Search form + result loading
├── details.jsp                        # Book details page with AJAX content fetch
├── cart.jsp                           # Cart page with async cart details
├── checkout.jsp                       # Checkout form (address + confirmation)
├── login.jsp                          # Login form with client-side validation
├── register.jsp                       # Registration form with validation and date picker
├── myaccount.jsp                      # Profile update view for logged-in users
├── past_oders.jsp                     # Past orders page loading order history
├── get_book_details.jsp               # Book detail fragment/template response page
├── list_categories.jsp                # Category list fragment/template response page
├── list_category_books.jsp            # Category books fragment/template response page
├── shopping_cart.jsp                  # Shopping cart fragment/template response page
├── view_past_orders.jsp               # Past orders fragment/template response page
├── effects.js                         # UI effect scripts
├── java.js                            # Custom JavaScript utilities
├── style.css                          # Core stylesheet
├── jquery-1.5.1.min.js               # jQuery library
├── jquery-ui-1.8.12.custom.min.js    # jQuery UI script
├── jquery-ui-1.8.12.custom.css       # jQuery UI styles
├── prototype.js                       # Prototype library
├── scriptaculous.js                   # Scriptaculous library
├── lightbox.js                        # Lightbox behavior
├── lightbox.css                       # Lightbox styles
├── tag_libs.tld                       # Custom JSP tag library descriptor
├── about.jsp                          # About page
├── contact.jsp                        # Contact page
├── terms.html                         # Terms and conditions page
└── logout.jsp                         # Session logout page
```

---

## ⚙️ Setup Instructions

### Prerequisites:
- JDK 8+
- NetBeans IDE (recommended by project notes)
- GlassFish Server (project notes mention GlassFish 3.x)
- SQL database compatible with provided initializer script

### Step-by-Step Setup:

**1. Import/Open the enterprise project in NetBeans**
- Open the full enterprise application (not isolated modules).

**2. Initialize database**
- Execute `database_initializer.sql` in your DB.

**3. Configure server and deploy**
- Deploy the whole application to GlassFish.

**4. Verify server port/EJB lookup if needed**
- If `ejb/BookStoreManager` lookup fails, check IIOP listener port in GlassFish `domain.xml` (project note indicates `3700` may be required).

**5. Run the application**
- Start from deployed app and open the welcome page (`index.jsp`).
