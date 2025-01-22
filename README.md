
## **Day 3: API Integration and Data Migration for FurnitureHub Marketplace**

This documentation outlines the work completed on Day 3 of the FurnitureHub Marketplace hackathon. It includes custom migration, data integration from Sanity, schema design, and rendering data using GROQ queries in a Next.js application. Each section is supplemented with detailed code explanations and image references.

---

### **Sanity Product Schema**
**Image Reference: `product schema.PNG`**

The Sanity product schema defines the structure for storing furniture product data in the Sanity Content Management System (CMS). Here's a breakdown of its components:

1. **Title Field**:
   - **Type**: String
   - **Purpose**: Stores the name of the furniture item (e.g., "Harmony Modular Sectional").
   - **Validation**: Ensures this field is not left empty, as it's a required field for identifying the product.

2. **Slug Field**:
   - **Type**: Slug
   - **Purpose**: Creates a unique URL-friendly identifier for each product. For example, the title "Harmony Modular Sectional" might generate a slug like `harmony-modular-sectional`.
   - **Validation**: Includes validation to ensure uniqueness, preventing duplicate slugs in the database.

3. **Image Field**:
   - **Type**: Image
   - **Purpose**: Stores a single image of the product.
   - **Options**:
     - Supports the upload of high-resolution images.
     - Allows customization for alternative text for accessibility purposes.

4. **Description Field**:
   - **Type**: Text
   - **Purpose**: Provides a detailed description of the product, explaining its features, dimensions, and other details.

5. **Price Field**:
   - **Type**: Number
   - **Purpose**: Represents the cost of the product.
   - **Validation**: Ensures the price is a positive value (e.g., `greaterThan(0)`).

6. **Category Field** (Optional, if included in the schema):
   - **Type**: Reference or String
   - **Purpose**: Associates the product with a category (e.g., "Sofas", "Sectionals").
   - **Benefits**: Helps in filtering and organizing products based on their categories.

### **Explanation and Usage**:
- **Scalability**:
  The schema is designed for scalability, meaning additional fields (e.g., stock levels, dimensions, or materials) can easily be added without affecting the existing structure.

- **Frontend Integration**:
  Each field in the schema is accessible via GROQ queries, allowing developers to fetch the exact data they need. For example:
  ```groq
  *[_type == "product"] {
    title,
    slug,
    image,
    description,
    price
  }
  ```
  This ensures efficient data fetching and rendering on the frontend.

- **Validation Benefits**:
  The validation rules enforce clean and consistent data entry, reducing errors during the migration and rendering processes.

---

### **Other Sections (Previously Detailed)**:
1. **Custom Migration Code**
   - Handles transferring Sanity CMS data into the FurnitureHub database.
   - Includes mapping, validation, and insertion logic.

2. **Client Page Code**
   - Implements server-side rendering (SSR) using GROQ to fetch and display products.
   - Supports dynamic routing and responsive UI design.

3. **Schema Code**
   - Defines the structure of the FurnitureHub database, aligning with Sanity schemas.

4. **Item Card Code**
   - A reusable component for rendering furniture product information, including images, descriptions, and prices.

5. **Environment Variables**
   - Securely store sensitive configurations for API access and database connections.

6. **Sanity CMS Interface**
   - The interface allows users to manage products, including editing titles, uploading images, and adding descriptions.

---

### **Conclusion**
The Sanity product schema serves as the backbone of the FurnitureHub marketplace's content management. It ensures structured, validated, and scalable data storage while enabling seamless integration with Next.js using GROQ queries. By combining this schema with custom migration and rendering logic, the application provides a robust solution for managing and displaying e-commerce products.
