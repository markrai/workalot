# Workalot

![Workalot Logo](logo.png)

a timeline visualization tool for tracking work history across multiple chart types.

## Features

- **Timeline View** - Interactive grid showing job history over time
- **Pie Chart** - Visual breakdown of time spent at each company
- **Gantt Chart** - Year-based project timeline view
- **Bar Chart** - Chronological duration comparison
- **File Upload** - Upload your own work history file (.txt)

## Usage

**Option 1 - Upload File:**
1. Click the folder icon (📁) in the top left to upload your work history file
2. Select a `.txt` file with your work history

**Option 2 - Edit File Manually:**
1. Edit `history.txt` with your work history in the format:
   ```
   Company Name MM/DD/YYYY - MM/DD/YYYY
   Company Name MM/DD/YYYY - Present
   ```

2. **Important**: Due to browser security restrictions, you need to serve the files from a local server:
   
   **Option A - Python (if installed):**
   ```bash
   python -m http.server 8000
   ```
   Then open `http://localhost:8000` in your browser
   
   **Option B - Node.js (if installed):**
   ```bash
   npx serve .
   ```
   
   **Option C - VS Code Live Server extension:**
   Right-click `index.html` → "Open with Live Server"

3. Switch between chart views using the icons in the top right

## Deployment

**Docker (Recommended):**
```bash
# Build and run with Docker Compose
docker-compose up -d

# Or build and run manually
docker build -t workalot .
docker run -p 8080:80 workalot
```

Then open `http://localhost:8080` in your browser.

**Cloudflare Pages**: This project works perfectly when deployed to Cloudflare Pages:

1. Push your code to a Git repository (GitHub, GitLab, etc.)
2. Connect your repository to Cloudflare Pages
3. Set build command to: `echo "No build required"`
4. Set output directory to: `/` (root)
5. Deploy!

The `fetch('history.txt')` call will work correctly when served over HTTPS from Cloudflare Pages.

## Data Format

Each line should follow this pattern:
- `Company Name Start Date - End Date`
- Use "Present", "Now", or "Current" for ongoing positions
- Dates should be in MM/DD/YYYY format

## Chart Types

- **Timeline**: Calendar grid with hover tooltips
- **Pie Chart**: Proportional time spent visualization
- **Gantt Chart**: Year-based timeline bars
- **Bar Chart**: Duration comparison with chronological ordering

## Quick Start with Docker

1. Clone the repository
2. Run `docker-compose up -d`
3. Open `http://localhost:8080`

## Requirements

- Docker and Docker Compose (for containerized deployment)
- Modern web browser
- Local server (Python, Node.js, or VS Code Live Server) for development

