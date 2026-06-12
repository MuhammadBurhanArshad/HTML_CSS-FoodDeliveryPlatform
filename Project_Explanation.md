# Project Explanation: A to Z Guide

Welcome to the Food Delivery Platform! Since you are new to this project, this document breaks down exactly how the application works from A to Z. 

## 1. Overall Architecture
This is a **Frontend-Only Application**. It does not have a real backend server (like Node.js or Python) or a real database (like MySQL or MongoDB). Instead, it uses **Vanilla JavaScript** to handle logic and the browser's **localStorage** to save data temporarily so it doesn't disappear when you refresh the page.

The application is split into multiple HTML pages:
- `index.html`: The home page showing restaurants.
- `cart.html`: The shopping cart.
- `tracking.html`: The live order tracking page.
- `history.html`: The past orders page.

## 2. Styling (CSS)
Instead of putting all CSS in one giant file, the styling is broken down:
- **`styles/global.css`**: Contains styles that are shared across *all* pages. This includes the top Navigation Bar, the font setup (`Outfit` font), base colors, and the Toast notification animations.
- **Page-Specific CSS (`index.css`, `cart.css`, etc.)**: Each HTML file links to its specific stylesheet to keep the code organized and prevent styles from clashing.
- **No CSS Variables**: Hardcoded Hex colors (like `#ff4b2b` for orange/red and `#f8f9fa` for backgrounds) are used directly to keep it incredibly simple.

## 3. How the JavaScript Works (`scripts/app.js`)
The `app.js` file is the brain of the project. It is linked at the bottom of every HTML file. Here is how it is structured:

### A. Global Image Fallback
At the very top of `app.js`, there is an `error` event listener. If the HTML tries to load an image from the `images/` folder but the image doesn't exist, this script catches the error and instantly replaces the broken image with a nice grey placeholder from the internet.

### B. Mock Data (`const restaurants`)
Instead of fetching data from an API, we have a hardcoded array of objects called `restaurants`. Each object represents a restaurant and contains its name, rating, delivery time, cover image, and an array of `menu` items. 
- To add a new restaurant, you simply add another object to this array.
- To update images, you change the `image` property to point to your `images/filename.jpeg`.

### C. State Management (`localStorage`)
When you add a Biryani to your cart, the JavaScript pushes that item into a `cart` array. It then saves this array into the browser using `localStorage.setItem('craveCart', JSON.stringify(cart))`. 
Because it's in `localStorage`, when you navigate from `index.html` to `cart.html`, the script reads `localStorage.getItem('craveCart')` and reconstructs your cart perfectly.

### D. Page Specific Logic
Since `app.js` runs on every page, it checks which page you are currently on by looking for specific HTML IDs:

- **If it finds `restaurantGrid` (Index Page)**: 
  It loops through the `restaurants` array and creates HTML cards for each restaurant dynamically. It also handles the Search bar and the Category filter buttons.
  
- **If it finds `restaurantModal` (Index Page Modal)**:
  When you click a restaurant card, it opens a popup (modal). The script takes the specific menu array for that restaurant and generates the menu item cards. When you click "+", it triggers the `addToCart` function.

- **If it finds `cartContainer` (Cart Page)**:
  It loops through your saved `cart` array and creates the cart UI. It calculates the subtotal, adds a fixed delivery fee (Rs. 150), and calculates an 8% tax. Clicking "Proceed to Checkout" packages your cart into a new "Order" object, saves it to `localStorage`, clears the cart, and redirects you to `tracking.html`.

- **If it finds `trackingContent` (Tracking Page)**:
  It retrieves the active order. It uses a `setInterval` timer (running every 10 seconds) to simulate the order moving from "Accepted" -> "Preparing" -> "On the Way" -> "Delivered". Once delivered, it moves the order into the History list.

- **If it finds `historyList` (History Page)**:
  It pulls all completed orders from `localStorage` and lists them out, showing the order ID, date, total price, and the items you bought.

## 4. How to Modify the Project
- **Adding Images**: Place your `.jpeg` or `.png` files in the `images/` folder. Then, open `app.js` and update the `image: "images/your-image.jpeg"` strings inside the `restaurants` mock data array.
- **Changing Prices/Text**: Open `app.js` and change the text or prices inside the `restaurants` array.
- **Changing Colors**: Open the CSS files inside the `styles/` folder and use "Find and Replace" to swap out the hex codes (e.g., replacing `#ff4b2b` with a new color).

You are now fully equipped to understand, manage, and expand this platform!
