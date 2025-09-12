Of course. Here is the complete and final set of requirements for the Interactive Map Gallery project, incorporating all of our discussions and decisions.

-----

## **Final Feature Requirements: Interactive Map Gallery Project**

**Project Date**: September 12, 2025
**Version**: 1.0

### **Project Summary**

The project's objective is to create a simple, responsive web application that displays an interactive map. The map will feature a small number of clickable points. When a user clicks a point, a modal window will appear, showing descriptive text and a cover image for a photo gallery. Clicking this image will open a public Google Photos album in a new browser tab.

| **Component** | **Specification** |
| :--- | :--- |
| **Mapping Library** | Leaflet.js |
| **Primary Feature** | Interactive map with modal pop-ups |
| **Data Source** | Single, static JSON file |
| **Max Data Points**| 10 |
| **Modal Content** | Text + Clickable Cover Image linking to a photo album |
| **Data Management** | Manual file replacement (annual) |

-----

### **1. Core Functionality**

  * **Map Display**: The application will display a navigable (pan, zoom) world map as the main interface.
  * **Point Rendering**: A maximum of 10 locations, defined in the JSON file, will be displayed on the map as clickable markers.
  * **Modal Interaction**: When a user clicks on a map marker, a modal (pop-up) window must appear over the map.
  * **Modal Content Display**: The modal will display two elements:
    1.  A short descriptive text.
    2.  A single, clickable cover image representing a photo gallery.
  * **External Gallery Link**: Clicking the cover image within the modal will open the linked Google Photos album in a new browser tab.
  * **Modal Closure**: The user must have a clear way to close the modal, such as an "X" button or by clicking outside the modal area.

### **2. Data Requirements**

  * **Data Source**: All map points and associated content will be managed in a single, static **JSON file**.

  * **JSON Structure**: The file will contain a list of location objects. Each object must include the following five fields:

      * `latitude`: The geographic latitude (Number).
      * `longitude`: The geographic longitude (Number).
      * `text`: The descriptive text for the modal (String).
      * `albumUrl`: The full, public URL to the Google Photos album (String).
      * `coverImageUrl`: A direct link to the single image to be used as the gallery's cover photo (String).

  * **Example JSON Object**:

    ```json
    {
      "latitude": 54.8985,
      "longitude": 23.9036,
      "text": "Photos from our trip to Kaunas Old Town.",
      "albumUrl": "https://photos.app.goo.gl/your-album-link",
      "coverImageUrl": "https://your-direct-link-to-a-cover-image.jpg"
    }
    ```

  * **Data Maintenance**: The content in the JSON file is expected to be updated **manually once per year**. No content management system or admin interface is required.

### **3. Error Handling & Data Integrity**

  * **Strict Validation**: The application must handle data errors robustly. If the JSON file fails to load for any reason, or if it contains any invalid or malformed data for even a single point (e.g., a missing field), **no points will be displayed on the map**.
  * **User Notification**: In any of the failure conditions described above, the application will display the message "**ask Dainius**" followed by a simple technical error description for debugging purposes.

### **4. User Experience (UX) and Design**

  * **Responsive Design**: The website, including the map and modals, must be fully functional and visually appealing on both desktop and mobile devices.
  * **Usability**: All interactions (panning the map, clicking a marker, closing the modal) should be intuitive, smooth, and immediate.
  * **Visual Clarity**: Map markers must be easily distinguishable. The text and image within the modal must be legible and well-formatted.

### **5. Technical Specifications & Performance**

  * **Mapping Library**: The project will be built using the **Leaflet.js** library, chosen for its lightweight nature, simplicity, and lack of cost.
  * **Performance**: Given the maximum of 10 data points, performance risks are negligible. Standard web performance is sufficient, and no special optimizations are required.
  * **Browser Compatibility**: The website must function correctly on the latest versions of major web browsers, including Chrome, Firefox, Safari, and Edge.