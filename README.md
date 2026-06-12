# Food Delivery Platform

A fully functional, front-end only Food Delivery Platform built using pure HTML, CSS, and Vanilla JavaScript. It features a modern, premium user interface, a cart system, order history, and simulated live tracking—all persisting locally in your browser.

## Features
- **Restaurant Listings**: Browse authentic Pakistani restaurants and dishes.
- **Search & Filter**: Search restaurants by name or filter them by categories (Desi, BBQ, Rice, Desserts).
- **Restaurant Details Modal**: Click on any restaurant to view its specific menu and prices.
- **Cart System**: Add items to your cart, adjust quantities, and calculate totals (including delivery fee and taxes).
- **Checkout & Tracking**: Simulate placing an order which redirects you to a live tracking page showing order progression.
- **Order History**: View your past orders categorized by their completion status.
- **Image Fallback System**: A built-in JavaScript handler ensures that any missing image degrades gracefully to a consistent placeholder.

## Technologies Used
- **HTML5**: For semantic page structure.
- **Vanilla CSS3**: Pure CSS styling with modern layout techniques (Grid/Flexbox) and no preprocessors or frameworks. Styles are separated page-by-page.
- **Vanilla JavaScript (ES6)**: For DOM manipulation, mock data management, and state persistence using `localStorage`.

## Screenshots

*(Paste your screenshot images in the `images` folder and update the filenames below if necessary)*

### Home Page
![Home Page Screenshot](images/screenshot-home.png)

### Cart Page
![Cart Page Screenshot](images/screenshot-cart.png)

### Order Tracking
![Tracking Page Screenshot](images/screenshot-tracking.png)

### Order History
![History Page Screenshot](images/screenshot-history.png)

## Installation & Usage
1. Clone or download this repository.
2. Ensure you have the `images` folder created in the root directory for your pictures.
3. Open `index.html` in any modern web browser to start using the platform. No backend server or build steps are required.

## File Structure
- `index.html` - The main restaurant listing page.
- `cart.html` - The user's shopping cart and checkout page.
- `history.html` - Displays the user's past orders.
- `tracking.html` - The live order tracking interface.
- `styles/` - Contains separated CSS files for each HTML page (`global.css`, `index.css`, `cart.css`, etc.).
- `scripts/app.js` - Contains the mock data, application logic, and state management.
- `images/` - Directory for all image assets.
