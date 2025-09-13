

Here is the finalized implementation plan to update the project from its current state to the new interactive photo gallery.

-----

### \#\# 📝 **Step 1: Update the Data Structure**

**Goal**: Modify the embedded `locations` data in `index.html` to support a list of photos for a gallery.

In the `<script>` section of `index.html`, you will modify the `locations` array. For each location object, you need to:

1.  Remove the `coverImageUrl` field.
2.  Add a new field called `photos`, which will be an array `[]` containing direct links to each image.

**Before (from `index.html`):**

```javascript
{
    "coordinates": "54°59'08.0\"N 24°00'01.7\"E",
    "text": "Yra kilnojamas namelis...",
    "albumUrl": "https://photos.app.goo.gl/...",
    "coverImageUrl": "https://photos.app.goo.gl/...", // This will be removed
    "googleMapsUrl": "http://googleusercontent.com/..."
}
```

**After:**

```javascript
{
    "coordinates": "54°59'08.0\"N 24°00'01.7\"E",
    "text": "Yra kilnojamas namelis...",
    "albumUrl": "https://photos.app.goo.gl/...",
    "googleMapsUrl": "http://googleusercontent.com/...",
    "photos": [ // This is the new array
        "https://direct-link-to-image1.jpg",
        "https://direct-link-to-image2.jpg",
        "https://direct-link-to-image3.jpg"
    ]
}
```

-----

### \#\# 🖼️ **Step 2: Update the Modal's HTML Content**

**Goal**: Change the `showModal` function to build the new gallery instead of the old "Google Photos Preview" block.

You will rewrite the `showModal(location)` function. Instead of creating the current preview, it will now dynamically generate the HTML for a main image and clickable thumbnails.

**Modify `showModal(location)` to generate this structure inside the `modal-body`:**

```html
<div class="location-text">${location.text}</div>
<div class="coordinates">${location.coordinates}</div>

<div id="gallery-container">
    <img id="modal-main-image" src="${location.photos[0]}" alt="Main gallery image">
    <div id="modal-thumbnails">
        </div>
</div>

<div class="action-buttons">
    </div>
```

-----

### \#\# ✨ **Step 3: Implement the Gallery JavaScript Logic**

**Goal**: Add the JavaScript logic to the `showModal` function to make the gallery interactive.

1.  **Set the Main Image**: When the modal opens, the `src` of the `#modal-main-image` should be set to the first URL in the `location.photos` array.
2.  **Build Thumbnails**: Loop through the `location.photos` array. For each URL:
      * Create a new `<img>` element.
      * Give it a class (e.g., `thumbnail`).
      * Add a `click` event listener. When a thumbnail is clicked, it must update the `src` of the `#modal-main-image`.
      * Append this new thumbnail to the `#modal-thumbnails` container.

-----

### \#\# 🎨 **Step 4: Add CSS for the Gallery**

**Goal**: Add new CSS rules to style the gallery elements.

In the `<style>` section of `index.html`, add the following CSS to ensure the gallery is visually appealing and functional.

```css
/* Styles for the new gallery */
#gallery-container {
    margin-top: 15px;
    margin-bottom: 20px;
}

#modal-main-image {
    width: 100%;
    height: auto;
    border-radius: 8px;
    margin-bottom: 10px;
}

#modal-thumbnails {
    display: flex;
    flex-wrap: wrap;
    gap: 8px; /* Space between thumbnails */
}

.thumbnail {
    width: 80px;
    height: 80px;
    object-fit: cover; /* Prevents images from stretching */
    border-radius: 4px;
    cursor: pointer;
    border: 2px solid transparent;
    transition: border-color 0.2s;
}

.thumbnail:hover {
    border-color: #007bff; /* Highlight on hover */
}
```