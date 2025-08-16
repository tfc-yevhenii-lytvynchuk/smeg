# SMEG B2B Product Portal

A lightweight, responsive HTML/CSS implementation of the SMEG B2B Product Portal, designed for future integration with .NET backend.

## Design System

### Colors
- Primary: `#2779C4`
- Success: `#006800`
- Warning: `#EB6F25`
- Background: `#F0F3F6`

### Components
- Navigation
- Product Cards
- Category Cards
- Search Forms
- Buttons
- Breadcrumbs

## Notes for .NET Developers

### Dynamic Content Areas
The following sections are designed to be populated dynamically:

1. **Product Categories**
   - Located in the main product categories section
   - Each category card is wrapped in an `<a>` tag
   - Images are stored in `assets/images/categories/`

2. **Best Sales Section**
   - Tab navigation for different product categories
   - Product cards will be dynamically populated
   - Current implementation uses placeholder content

3. **Search Functionality**
   - Search form in the banner section
   - Navigation search form
   - Both forms are ready for .NET integration

### Integration Points

1. **Forms**
   - Product search form: `id="product-search-form"`
   - Navigation search form: `id="nav-search-form"`
   - Newsletter subscription form `id="newsletter-form"`

2. **Dynamic Content Classes**
   - Product cards: `smeg-product-card`
   - Category cards: `liebher-product-category-card`
   - Navigation items: `nav-link`

3. **Image Handling**
   - Product images should maintain aspect ratio
   - Category images are set to `object-fit: contain`
   - Banner images use `object-fit: cover`

## CSS Architecture

The project uses a combination of:
- Custom CSS reset
- Bootstrap 5 for grid and components
- Custom utility classes
- Component-specific styles

### CSS Organization Strategy
- `styles.css`: Contains only global styles, utility classes, and shared components
- Page-specific styles: Included directly in the respective HTML files using `<style>` tags
  - This approach clearly indicates which styles are specific to each page
  - Makes it easier to identify and maintain page-specific styles
  - New pages will follow the same pattern with their own scoped styles

### Key CSS Files
- `styles.css`: Main stylesheet for global styles
- `bootstrap.min.css`: Bootstrap framework
- `smeg-fonts.css`: Custom font definitions
- `bootstrap-icons.css`: Icon library

## Responsive Design

The implementation is fully responsive with breakpoints at:
- Mobile: < 768px
- Tablet: 768px - 991px
- Desktop: > 992px

## Range Slider Implementation

The project includes a custom range slider component for price filtering, implemented on the `products-list.html` and `search-results.html` pages.

### Files
- `assets/css/range-input.css`: Custom styling for the range slider
- `assets/js/input-range.js`: JavaScript functionality for the range slider
- HTML implementation: Found in products filtering sections

### Usage
To implement the range slider on a page:

1. **HTML Structure**:
```html
<div class="smeg-range-slider" id="price-range-slider">
  <input type="number" class="min-price" name="points-range-min">
  <input type="number" class="max-price" name="points-range-max">
  <div class="smeg-range-slider-range">
    <input type="range" class="min-input">
    <input type="range" class="max-input">
    <div class="smeg-range-slider-slider">
      <div class="smeg-range-slider-slider-progress" style="width: 100%; left: 0%;"></div>
    </div>
  </div>
</div>
```

2. **CSS Include**:
```html
<link rel="stylesheet" href="assets/css/range-input.css">
```

3. **JavaScript Include**:
```html
<script src="assets/js/input-range.js"></script>
```

4. **Initialization**:
```javascript
document.addEventListener('DOMContentLoaded', function() {
  initRangeSlider({
    containerId: 'price-range-slider',
    min: 0,
    max: 5000,
    initialMin: 2000,
    initialMax: 5000
  });
});
```

### Features
- **Dual Range Selection**: Allows setting both minimum and maximum values
- **Number Input Integration**: Displays current values in number inputs
- **Drag to Move**: Progress bar can be dragged to move the entire range
- **Form Reset Support**: Resets to initial values when form is reset
- **Responsive Design**: Works on both desktop and mobile devices
- **Boundary Validation**: Ensures values stay within defined min/max bounds

### Configuration Options
- `containerId`: ID of the container element
- `min`: Minimum value (default: 0)
- `max`: Maximum value (default: 9999)
- `initialMin`: Initial minimum value (default: min)
- `initialMax`: Initial maximum value (default: max)

### Integration with .NET
The range slider form inputs are ready for backend integration:
- `min-price` and `max-price` inputs contain the selected range values
- Form submission will include these values for server-side processing
- Values are automatically validated on the client side

## Future Considerations

3. **SEO**
   - Add meta descriptions