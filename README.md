# Beginner's Guide to Using the ASOS API via RapidAPI
This API is listed on [RAPIDAPI](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/asos-api6) -> https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/asos-api6

## Introduction
Welcome to the ASOS API! This guide will help you get started with making your first API requests. Whether you're new to APIs or just getting started with our service, we'll walk you through everything step by step.

## Prerequisites
Before you begin, you'll need:
- A RapidAPI account (free to create)
- A subscription to the ASOS API
- Basic knowledge of any programming language
- A code editor or development environment
- (Optional) API testing tool like Postman

## Getting Started

### Step 1: Create a RapidAPI Account
1. Go to [RapidAPI's website](https://rapidapi.com)
2. Click on "Sign Up" in the top right corner
3. Complete the registration process
4. Verify your email address

### Step 2: Subscribe to the API
1. Visit the ASOS API page on RapidAPI
2. Click on the "Pricing" tab
3. Choose your preferred subscription plan
4. Complete the subscription process

### Step 3: Get Your API Key
1. Once subscribed, click on the "Security" tab
2. Find your API key (it should look like a long string of letters and numbers)
3. Keep this key secure and never share it publicly

## Making Your First API Request

### Authentication
All requests must include your RapidAPI key in the headers. Here's how to set it up in different programming languages:

```javascript
// JavaScript (using fetch)
const options = {
  method: 'GET',
  headers: {
    'X-RapidAPI-Key': 'YOUR_API_KEY',
    'X-RapidAPI-Host': 'asos-api6.p.rapidapi.com'
  }
};
```

```python
# Python (using requests)
headers = {
    'X-RapidAPI-Key': 'YOUR_API_KEY',
    'X-RapidAPI-Host': 'asos-api6.p.rapidapi.com'
}
```

### Example Request
Here's a basic example of how to make a request:

```javascript
// JavaScript
fetch('https://asos-api6.p.rapidapi.com/product/similar', options)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

```python
# Python
import requests

response = requests.get('https://asos-api6.p.rapidapi.com/product/search', headers=headers)
data = response.json()
print(data)
```

## Common Issues and Solutions

### Error: Invalid API Key
- Double-check that you've copied your API key correctly
- Ensure the key is properly included in your request headers
- Verify your subscription is active

### Error: Rate Limit Exceeded
- Check your current subscription plan limits
- Implement request throttling in your code
- Consider upgrading your plan if you need more requests

## Best Practices
1. Always store your API key securely (use environment variables)
2. Implement error handling in your code
3. Cache responses when appropriate to minimize API calls
4. Monitor your API usage to stay within rate limits

## Getting Help
If you encounter any issues:
1. Check the API documentation on RapidAPI
2. Look for error messages in your response
3. Contact support through RapidAPI's platform
4. Review your code for common mistakes

## Next Steps
Once you're comfortable with basic requests:
1. Explore all available endpoints
2. Implement error handling
3. Add rate limiting to your requests
4. Consider caching frequently used data

Remember to replace `'YOUR_API_KEY'` with your actual RapidAPI key and update the endpoint URLs according to your specific API documentation.

# ASOS API Documentation

## Endpoints

### 1. Product Search
**Endpoint:** `/product/search`

**Description:** Search for products based on a query.

**Method:** GET

**Query Parameters:**
- `query` (string, required): The search term.
- `page` (string, optional, default: `1`): The page number for pagination.
- `perPage` (string, optional, default: `24`): The number of items per page.
- `currency` (string, optional, default: `USD`): The currency for the results.
- `countryISO` (string, optional, default: `US`): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of products */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 2. Similar Products
**Endpoint:** `/product/similar`

**Description:** Retrieve similar products based on a product ID.

**Method:** GET

**Query Parameters:**
- `produtId` (string, required): The product ID to find similar products.
- `perPage` (string, optional, default: `18`): Number of similar items to retrieve.
- `currency` (string, optional, default: `USD`): The currency for the results.
- `countryISO` (string, optional, default: `PT`): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of similar products */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 3. Products by Category
**Endpoint:** `/product/bycategory`

**Description:** Retrieve products under a specific category.

**Method:** GET

**Query Parameters:**
- `categoryId` (string, required): The category ID.
- `page` (string, optional, default: `1`): The page number for pagination.
- `perPage` (string, optional, default: `24`): The number of items per page.
- `currency` (string, optional, default: `USD`): The currency for the results.
- `countryISO` (string, optional, default: `US`): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of products */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 4. Search Autocomplete
**Endpoint:** `/product/search/autocomplete`

**Description:** Retrieve autocomplete suggestions for a search query.

**Method:** GET

**Query Parameters:**
- `query` (string, required): The search term.
- `limit` (string, optional, default: `18`): The number of suggestions to retrieve.
- `countryISO` (string, optional, default: `PT`): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of suggestions */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 5. Product Discount
**Endpoint:** `/product/discount`

**Description:** Check for discounts on a specific product.

**Method:** GET

**Query Parameters:**
- `productId` (string, required): The product ID to check.
- `currency` (string, optional, default: `USD`): The currency for the results.
- `countryISO` (string, optional, default: `US`): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": {/* discount details */},
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 6. Countries List
**Endpoint:** `/countries/list`

**Description:** Retrieve a list of supported countries.

**Method:** GET

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of countries */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 7. Store Currency Codes
**Endpoint:** `/stores/codes/currency`

**Description:** Retrieve currency codes for stores based on the country.

**Method:** GET

**Query Parameters:**
- `countryIso` (string, required): The country ISO code.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of store codes */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---

### 8. Men's Categories
**Endpoint:** `/categories/men`

**Description:** Retrieve products from men's categories.

**Method:** GET

**Query Parameters:**
- `page` (string, optional, default: `1`): The page number for pagination.
- `perPage` (string, optional, default: `22`): The number of items per page.

**Response:**
- **Success:**
  ```json
  {
      "message": null,
      "data": [/* array of men's products */],
      "error": null
  }
  ```
- **Error:**
  ```json
  {
      "message": "Error message",
      "data": null,
      "error": "Error code"
  }
  ```

---
## **Endpoint: Get Women's Categories**

**URL:** `/categories/women`

**Method:** `GET`

### Query Parameters
| Parameter | Type   | Default | Required | Description                  |
|-----------|--------|---------|----------|------------------------------|
| `page`    | number | 1       | Yes      | The page number to retrieve. |
| `perPage` | number | 22      | Yes      | Number of items per page.    |

### Responses
#### Success Response:
- **Status Code:** `200`
- **Body:**
```json
{
  "message": null,
  "data": [
    // Array of categories
  ],
  "error": null
}
```

#### Error Responses:
- **Status Code:** `400`
```json
{
  "message": "Please provide the page!",
  "data": null,
  "error": "MISSING_PARAMETERS"
}
```
- **Status Code:** `500`
```json
{
  "message": "Something went wrong: {error_message}",
  "data": null,
  "error": "INTERNAL_ERROR"
}
```

---

## **Endpoint: Get Product Short Description**

**URL:** `/product/description/short`

**Method:** `GET`

### Query Parameters
| Parameter   | Type   | Default      | Required | Description                     |
|-------------|--------|--------------|----------|---------------------------------|
| `productId` | string | "206868950" | Yes      | The ID of the product.         |

### Responses
#### Success Response:
- **Status Code:** `200`
- **Body:**
```json
{
  "message": null,
  "data": {
    "description": "Short product description."
  },
  "error": null
}
```

#### Error Responses:
- **Status Code:** `400`
```json
{
  "message": "Query Missing. Please provide the productId!",
  "data": null,
  "error": "MISSING_PARAMETERS"
}
```
- **Status Code:** `500`
```json
{
  "message": "Something went wrong: {error_message}",
  "data": null,
  "error": "INTERNAL_ERROR"
}
```

---

## **Endpoint: Get Men's News**

**URL:** `/news/men`

**Method:** `GET`

### Query Parameters
| Parameter      | Type   | Default  | Required | Description                              |
|----------------|--------|----------|----------|------------------------------------------|
| `page`         | number | 1        | Yes      | The page number to retrieve.            |
| `perPage`      | number | 15       | Yes      | Number of items per page (max: 15).     |
| `languageCode` | string | "en-GB" | Yes      | Language code for the news content.     |

### Responses
#### Success Response:
- **Status Code:** `200`
- **Body:**
```json
{
  "message": null,
  "data": [
    // Array of news articles
  ],
  "error": null
}
```

#### Error Responses:
- **Status Code:** `400`
```json
{
  "message": "perPage can't be greater than 15!",
  "data": null,
  "error": "BAD_REQUEST"
}
```
- **Status Code:** `500`
```json
{
  "message": "Something went wrong: {error_message}",
  "data": null,
  "error": "INTERNAL_ERROR"
}
```

---

## **Endpoint: Get Women's News**

**URL:** `/news/women`

**Method:** `GET`

### Query Parameters
| Parameter      | Type   | Default  | Required | Description                              |
|----------------|--------|----------|----------|------------------------------------------|
| `page`         | number | 1        | Yes      | The page number to retrieve.            |
| `perPage`      | number | 15       | Yes      | Number of items per page (max: 15).     |
| `languageCode` | string | "en-GB" | Yes      | Language code for the news content.     |

### Responses
#### Success Response:
- **Status Code:** `200`
- **Body:**
```json
{
  "message": null,
  "data": [
    // Array of news articles
  ],
  "error": null
}
```

#### Error Responses:
- **Status Code:** `400`
```json
{
  "message": "perPage can't be greater than 15!",
  "data": null,
  "error": "BAD_REQUEST"
}
```
- **Status Code:** `500`
```json
{
  "message": "Something went wrong: {error_message}",
  "data": null,
  "error": "INTERNAL_ERROR"
}
```

---

## **Endpoint: Get Product Summary Description**

**URL:** `/product/description/summary`

**Method:** `GET`

### Query Parameters
| Parameter   | Type   | Default  | Required | Description                            |
|-------------|--------|----------|----------|----------------------------------------|
| `productId` | string |          | Yes      | The ID of the product.                |
| `currency`  | string | "USD"   | Yes      | Currency for the product price.       |
| `countryISO`| string | "US"    | Yes      | ISO code of the country.              |

### Responses
#### Success Response:
- **Status Code:** `200`
- **Body:**
```json
{
  "message": null,
  "data": {
    // Product summary description
  },
  "error": null
}
```

#### Error Responses:
- **Status Code:** `400`
```json
{
  "message": "Please provide the productId!",
  "data": null,
  "error": "MISSING_PARAMETERS"
}
```
- **Status Code:** `500`
```json
{
  "message": "Something went wrong: {error_message}",
  "data": null,
  "error": "INTERNAL_ERROR"
}
```
---


---

### Endpoint: Search Marketplace Products
**GET** `/marketplace/product/search`

Search for products in the ASOS marketplace.

#### Query Parameters
- **query** *(required)*: Search term for the products.
- **page** *(optional)*: Page number for pagination (default: `1`).
- **perPage** *(optional)*: Number of items per page (default: `24`).

#### Responses
- **200 OK**: Returns the search results.
  ```json
  {
    "message": null,
    "data": [/* Array of products */],
    "error": null
  }
  ```
- **400 Bad Request**: Missing or invalid query parameters.
  ```json
  {
    "message": "query Missing. Please provide the query!",
    "data": null,
    "error": "MISSING_PARAMETERS"
  }
  ```

---

### Endpoint: Get Boutique Products
**GET** `/marketplace/boutique/product`

Retrieve products from a specific boutique in the ASOS marketplace.

#### Query Parameters
- **boutiqueId** *(required)*: The ID of the boutique (default: `goose-goose`).
- **page** *(optional)*: Page number for pagination (default: `1`).

#### Responses
- **200 OK**: Returns boutique products.
  ```json
  {
    "message": null,
    "data": [/* Array of products */],
    "error": null
  }
  ```
- **400 Bad Request**: Missing or invalid query parameters.
  ```json
  {
    "message": "query Missing. Please provide the boutiqueId!",
    "data": null,
    "error": "MISSING_PARAMETERS"
  }
  ```

---

### Endpoint: Get Products by Category
**GET** `/marketplace/product/bycategory`

Retrieve products from a specific category.

#### Query Parameters
- **categoryId** *(required)*: The ID of the category (e.g., `men/coats-jackets`).
- **page** *(optional)*: Page number for pagination (default: `1`).
- **perPage** *(optional)*: Number of items per page (default: `24`).

#### Responses
- **200 OK**: Returns products in the specified category.
  ```json
  {
    "message": null,
    "data": [/* Array of products */],
    "error": null
  }
  ```
- **400 Bad Request**: Missing or invalid query parameters.
  ```json
  {
    "message": "query Missing. Please provide the categoryId!",
    "data": null,
    "error": "MISSING_PARAMETERS"
  }
  ```

---

### Endpoint: Get Boutique IDs
**GET** `/marketplace/boutique/IDS`

Retrieve a list of boutique IDs.

#### Query Parameters
- **page** *(optional)*: Page number for pagination (default: `1`).

#### Responses
- **200 OK**: Returns boutique IDs.
  ```json
  {
    "message": null,
    "data": [/* Array of boutique IDs */],
    "error": null
  }
  ```
- **400 Bad Request**: Missing or invalid query parameters.
  ```json
  {
    "message": "Please provide the page!",
    "data": null,
    "error": "MISSING_PARAMETERS"
  }
  ```

---

### Endpoint: Get Men's Categories
**GET** `/marketplace/categories/men`

Retrieve available categories for men's products.

#### Responses
- **200 OK**: Returns men's categories.
  ```json
  {
    "message": null,
    "data": [/* Array of men's categories */],
    "error": null
  }
  ```
- **500 Internal Server Error**: An unexpected error occurred.
  ```json
  {
    "message": "Something went wrong: &lt;error_message&gt;",
    "data": null,
    "error": "INTERNAL_ERROR"
  }
  ```

---

### Endpoint: Get Women's Categories
**GET** `/marketplace/categories/women`

Retrieve available categories for women's products.

#### Responses
- **200 OK**: Returns women's categories.
  ```json
  {
    "message": null,
    "data": [/* Array of women's categories */],
    "error": null
  }
  ```
- **500 Internal Server Error**: An unexpected error occurred.
  ```json
  {
    "message": "Something went wrong: &lt;error_message&gt;",
    "data": null,
    "error": "INTERNAL_ERROR"
  }
  ```


