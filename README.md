# ArchiTech

# Project Overview

Welcome to the **3D Asset Dashboard and Viewer** project. This platform enables users to:

- **Upload and manage 3D model and point cloud files**
- **View 3D meshes using a Three.js (Threepipe) viewer**
- **Visualize point clouds with a Potree-based viewer**
- **Collaborate through comments, ratings, and file sharing**
- **Prepare for future integration of AI-powered tools**

The application follows a modular architecture, allowing each component—**frontend dashboard**, **backend APIs**, **3D/point cloud viewers**—to be independently developed, deployed, and maintained.

## Architecture at a Glance

**Main Components:**

- **Backend (Cursor AI):**  
  - Provides a REST API for file uploads, metadata retrieval, authentication, and collaboration features.
  - Handles database connections (MongoDB/PostgreSQL) and integrates with cloud storage (e.g., AWS S3).
  
- **Frontend Dashboard (Replit AI):**  
  - A React.js application (built with Vite) that provides a user interface for uploading files, browsing assets, and opening viewers.
  - Connects to the backend via REST APIs for file management and metadata display.
  
- **Viewers (Bolt AI):**  
  - **Three.js Viewer:** Renders mesh models (GLTF, FBX, IFC) using Three.js with Threepipe enhancements (LOD, reflections, compression).
  - **Potree Viewer:** Visualizes large point cloud datasets (LAS, E57) as a standalone microservice or embedded component.
  - Both viewers integrate with the dashboard via embed links or API calls.

## Agent Responsibilities

### Cursor AI (Backend)

**Tasks:**
- Set up a Node.js + Express server.
- Implement file upload endpoints (`POST /api/upload`) and store files in AWS S3 (or GCP).
- Save file metadata (name, type, size, URL) in MongoDB or PostgreSQL.
- Create endpoints for fetching file lists (`GET /api/files`) and file details.
- Implement user authentication (Firebase Auth tokens or JWTs).
- Provide CRUD operations for comments, ratings, and collaboration features.

**Goals:**
- Deliver a stable, documented REST API.
- Make all endpoints and expected response formats clear in this README or a separate `API.md`.

### Replit AI (Frontend Dashboard)

**Tasks:**
- Build a React-based dashboard using Vite.
- Create UI components for:
  - File upload form.
  - File gallery with thumbnails, metadata display, and filtering.
  - Sidebar and navbar for navigation (links to “3D Viewer,” “Point Clouds,” “Settings,” “AI Tools”).
- Integrate backend endpoints to display real-time data.
- Add buttons or links to open the selected file in the appropriate viewer (Three.js or Potree).

**Goals:**
- Provide a user-friendly interface.
- Ensure navigation and state management are smooth.
- Test the dashboard by uploading files and verifying they appear with correct metadata.

### Bolt AI (Viewers)

**Tasks:**
- Develop a **Three.js Viewer** component using Threepipe:
  - Support GLTF, FBX, IFC models.
  - Add interactive controls (pan, zoom, rotate).
  - Enable visual enhancements (reflections, shadows, LOD).
- Set up a **Potree Viewer** service for point clouds:
  - Support LAS, E57 point clouds.
  - Implement controls for point density, lighting, and navigation.
- Provide integration methods (embed code, iframes, or React components) for the dashboard to use.

**Goals:**
- Deliver standalone viewers that accept a file URL and render it.
- Optimize performance and loading times.
- Document how the frontend can pass file URLs or configuration parameters to the viewers.

## Getting Started

### Prerequisites

- **Node.js & npm/yarn:** For backend and frontend builds.
- **AWS Credentials:** If using AWS S3 for file storage.
- **MongoDB or PostgreSQL:** For file metadata and user data.
- **Firebase Auth (optional):** For user authentication tokens.

### Repository Structure

A suggested structure (adjust as needed):

```
project-root/
├── backend/           # Backend code by Cursor AI
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── models/
│   │   └── server.js
│   └── package.json
├── frontend/          # Frontend code by Replit AI
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── App.js
│   │   └── index.js
│   ├── vite.config.js
│   └── package.json
└── viewers/           # Viewer code by Bolt AI
    ├── three-viewer/
    │   ├── src/
    │   └── package.json
    └── potree-viewer/
        ├── src/
        └── package.json
```

### Development Steps

1. **Cursor AI Starts with Backend:**
   - Implement `/api/upload` and `/api/files` endpoints.
   - Configure database schemas.
   - Commit code to `backend/` folder.
   - Document endpoints in `backend/README.md` or `API.md`.

2. **Replit AI Integrates Frontend:**
   - After backend endpoints are available, build the React dashboard in `frontend/`.
   - Fetch file lists from `/api/files`.
   - Implement file upload UI to POST to `/api/upload`.

3. **Bolt AI Sets up Viewers:**
   - In `viewers/three-viewer/`, create a component that accepts a `fileUrl` prop and loads a 3D model.
   - In `viewers/potree-viewer/`, configure Potree to load a given point cloud URL.
   - Provide `index.html` or embed instructions so Replit AI can integrate the viewers into the dashboard.

### Integration and Testing

- **Test Upload:** Upload a file via the dashboard. Confirm it appears in the file list.
- **Open in Viewer:** Select a 3D model file and ensure it opens in the Three.js Viewer. Repeat with a point cloud file in the Potree Viewer.
- **Commenting and Collaboration (Optional at First):** Once the basics work, add collaboration features and verify that they reflect properly in the dashboard UI.

### Deployment

- **Backend:** Deploy to AWS EC2 or GCP. Set environment variables for DB connections and AWS keys.
- **Frontend:** Deploy to Vercel or Netlify. Point the frontend at the backend’s public URL.
- **Viewers:** Deploy the viewer services independently (e.g., Potree Viewer on AWS EC2) or embed the Three.js Viewer directly in the frontend build.

## Contributing

- **Branching and Pull Requests:**  
  Each AI agent should work in a feature branch and submit pull requests for integration.
- **Code Reviews:**  
  Review code changes before merging to ensure consistency and stability.
- **Continuous Integration (Optional):**  
  Add CI/CD pipelines (GitHub Actions) to run tests and linting on each pull request.

## Contact

- **Project Lead:** [Your Name or Org]  
  Email: [Your Contact Email]

- **For Technical Issues:**  
  Use GitHub Issues to report bugs or request features.

---

By following these guidelines, the three agents—Cursor, Replit, and Bolt—can coordinate effectively to build and maintain a robust, scalable, and user-friendly 3D asset management and viewing platform.
