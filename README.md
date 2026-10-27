# Campus Canteen – React Ordering App

A mobile-first web app where students browse today's canteen menu, open an item and build an order.

## Run
    npm install
    npm run dev        # development server
    npm run build      # production build in /dist

## Requirement checklist
| Requirement | Where |
|---|---|
| Responsive (phone / tablet / desktop), semantic HTML, Grid + Flexbox, media queries | `src/index.css` (breakpoints 600px, 960px) |
| Reusable components with props + `useState` | `MenuList`, `ItemCard`, `Cart` in `src/components/` |
| Search, category filter, favourites toggle | `src/pages/Menu.jsx`, `ItemCard.jsx` |
| `useEffect` + `fetch` + `async/await` for `menu.json`, loading and error states | `src/App.jsx` (with retry button) |
| React Router: Menu, Item details, Cart | `src/App.jsx`, `src/pages/` |
| Cart shared with Context; header count and total update without reload | `src/context/CartContext.jsx` |

## Structure
    public/menu.json            menu data (edit this to change the menu)
    src/context/CartContext     cart state, count, total
    src/hooks/useLocalStorage   keeps cart and favourites after refresh
    src/components/             MenuList, ItemCard, Cart
    src/pages/                  Menu, ItemDetails, CartPage

## Notes
- Cart and favourites are saved in `localStorage`.
- Accessibility: labelled controls, `aria-pressed` on toggles, live regions for status messages, visible focus.

## Premium redesign
- Look: Multan-tile blue, saffron and chilli accents; Bricolage Grotesque + Figtree (bundled via @fontsource, no internet needed); automatic dark mode.
- Every dish has an original illustrated plate in `src/components/DishArt.jsx`, chosen by the `"art"` key in `public/menu.json`.
- Cards show a quantity stepper once a dish is in the cart; the details page lists more dishes from the same category.

## Using real photos
Put photos in `public/images/` (square, about 800px) and add an `"image"` key to the dish in `public/menu.json`:

    { "id": 1, "name": "Chicken Biryani", ..., "art": "biryani", "image": "images/biryani.jpg" }

The photo replaces the illustration everywhere (cards, details, cart). If a photo is missing or fails to load, the illustration is shown instead.
