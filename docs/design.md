# Architectural Blueprint: Portfolio Web Application
**Project Name:** Maker Portfolio
**Target Environment:** GitHub Pages (Static Hosting)
**Architecture Type:** Serverless Single-Page Application (SPA)

## 1. Core Directives & Tech Stack
*   **Zero Build-Step Constraint:** The project must run perfectly in a browser by opening `index.html`. No Node.js, no Webpack, no NPM installs. 
*   **Tech Stack:** HTML5, Vanilla JavaScript (ES6+), and CSS. You may use Tailwind CSS via CDN for rapid styling, but no frameworks like React or Vue. 
*   **Data-Driven DOM:** The HTML body should remain mostly empty. The DOM (grid, modals, filter buttons) must be injected by JavaScript, reading from a central `const portfolioData = [...]` array at the top of the script.

## 2. Visual Language & Typography
*   **Aesthetic Theme:** "Utilitarian Blueprint." Sleek, minimalist, high-contrast, and strictly functional. 
*   **Color Palette:** Grayscale. 
    *   Background: Stark white (`#FFFFFF`) or ultra-light cool gray (`#F8F9FA`).
    *   Text & Borders: Crisp black (`#111827`) or deep charcoal.
    *   No heavy drop shadows, no gradients. Use thin (1px) solid borders to define hierarchy.
*   **Typography:**
    *   *Headers & Descriptions:* Clean sans-serif (e.g., `Inter`, `Helvetica Neue`).
    *   *Metadata, Tags, & UI Elements:* Monospaced technical font (e.g., `Roboto Mono`, `JetBrains Mono`) to reinforce the engineering/machining aesthetic.

## 3. Data Architecture (JSON Schema)
The JavaScript must rely on this exact object structure:
```javascript
{ 
  id: "item-001", 
  imageSrc: "images/fully_desk_2021_01.jpg", 
  title: "Executive Standing Desk", 
  company: "Fully", 
  description: "Custom ergonomic workstation prototype highlighting structural stability.", 
  tags: { 
    process: ["3-Axis CNC", "CAM Programming"], 
    material: ["Baltic Birch", "6061 Aluminum"], 
    itemType: ["Desk", "Prototyping"] 
  } 
}
4. UI Components & Layout
A. The Filter Console (Header Area)

    Location: Sticky at the top of the viewport.

    Functionality: The JS must dynamically parse the portfolioData array, extract all unique tags, and generate filter buttons grouped by category: Company, Process, Material, Item Type.

    Styling: Tags should look like stamped industrial labels (transparent background, 1px solid black border, uppercase monospaced font). Active state inverts the color (black background, white text).

    Interaction: Clicking tags instantly filters the Masonry Grid.

B. The Masonry Grid (Main View)

    Layout: A CSS or lightweight JS Masonry layout. Images have varying aspect ratios; they must lock together seamlessly without awkward vertical gaps.

    Vibe: "Random but thought out." Polished professional photos and raw shop photos share the same grid space to show the full scope of the maker process.

    Hover State: On hover, the image slightly dims (opacity shift) and a sharp, minimalist overlay appears at the bottom of the image containing the title and company in monospaced text.

C. The Lightbox Modal (Detail View)

    Trigger: Clicking any grid item.

    Layout: A full-screen modal that prevents background scrolling.

        Left Pane (70%): The high-resolution image, scaled to fit within the viewport without cropping.

        Right Pane (30%): A clean metadata sidebar containing the Title, Company, Description, and a categorized list of the item's tags.

    Interaction: Must include a close button ([ X ]) and support clicking outside the content box to close.