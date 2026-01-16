# Austin Ginder's Slides

A lightweight, single-page archive of my presentations given at WordPress Meetups and WordCamps since 2015. This static site provides a searchable interface to browse slides by date, location, or title.

## 🚀 Features

* **Instant Search:** Real-time filtering of presentations by title, date, or venue.
* **Dark Mode:** Built-in dark/light mode toggle with smooth transitions.
* **Responsive Design:** Fully mobile-friendly interface.
* **Zero Build Step:** Runs entirely in the browser using CDN-hosted libraries.

## 🛠️ Tech Stack

* **HTML5**
* **[Tailwind CSS](https://tailwindcss.com/):** Utility-first CSS framework (loaded via CDN).
* **[Alpine.js](https://alpinejs.dev/):** Lightweight JavaScript framework for reactive behavior (search & filtering).
* **Google Fonts:** Inter font family.

## 📦 Installation & Usage

Because this project relies on CDNs for its dependencies, no package manager (npm/yarn) or build process is required.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/austinginder/slides.git
    cd slides
    ```

2.  **Run locally:**
    Simply open `index.html` in any modern web browser.

    *Optional:* You can run a simple local server if preferred:
    ```bash
    # Python 3
    python3 -m http.server
    
    # PHP
    php -S localhost:8000
    ```

## 📝 Adding New Slides

To add a new presentation, open `index.html` and locate the `slidesApp()` function in the `<script>` tag at the bottom of the file. Add a new object to the `items` array:

```javascript
{ 
    date: "Month Day, Year", 
    place: "Event Name", 
    title: "Presentation Title", 
    href: "Folder-Name/" 
},

```

## 📄 License

MIT License

Copyright (c) 2026 Austin Ginder

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.