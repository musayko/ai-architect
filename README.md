# ai-architect
An all-in-one platform for AI-powered image generation, enhancement, and editing using multiple specialized APIs.

## User Stories

1. As an architect, I want to generate design concepts from text descriptions so that I can quickly iterate and explore multiple ideas.
2. As an interior designer, I want to refine room layouts and materials based on sketches so that I can present high-quality visualizations to clients.
3. As a real estate developer, I want to enhance and edit property renders so that I can create compelling marketing materials.
4. As an architect, I want to generate images based on both a text prompt and a reference image so that I can maintain stylistic consistency while creating new design variations.
5. As a user, I want to save and track the history of my image creations and edits so that I can revisit previous creations and manage multiple projects.

# AI Architect - Quick Start Guide

This guide provides the essential steps to set up and run the AI Architect application.

---

## I. Prerequisites

- **Git**
- **Docker Desktop** (or Docker Engine with Docker Compose CLI plugin)
- **Google Cloud Platform (GCP) Account:**
  - A GCP Project.
  - Vertex AI API enabled within the project.
  - A Service Account with **"Vertex AI User"** role (or equivalent permissions).
  - The JSON key file for this Service Account downloaded.

---

## II. Setup Instructions

### 1. Create a parent directory and clone the main project:

```bash
mkdir my-ai-architect-setup
cd my-ai-architect-setup
git clone https://github.com/musayko/ai-architect.git
cd ai-architect
```

### 2. Clone the Backend & Frontend Repositories:

> Ensure you are inside the `ai-architect` directory for these commands.

#### Backend:  
(https://github.com/musayko/ai-architect-backend.git)

```bash
# If ai-architect-backend folder doesn't exist or is empty:
# mkdir -p ai-architect-backend 
git clone <your_backend_repo_url> ai-architect-backend
```

#### Frontend:  
(https://github.com/musayko/ai-architect-frontend.git)

```bash
# If ai-architect-frontend folder doesn't exist or is empty:
# mkdir -p ai-architect-frontend
git clone <your_frontend_repo_url> ai-architect-frontend
```

### 3. Configure GCP Credentials:

- Place your downloaded GCP Service Account JSON key file into the `config/` directory (relative to the `ai-architect` root).
- Rename the key file to:

```
gcp-vertex-ai-credentials.json
```

> The expected path is:  
> `ai-architect/config/gcp-vertex-ai-credentials.json`

### 4. Configure GCP Project ID:

- Open the file:  
  `ai-architect-backend/src/main/resources/application.properties`

- Set the `gcp.project.id` property to your GCP Project ID:

```properties
gcp.project.id=YOUR_GCP_PROJECT_ID_HERE
```

---

## III. Running the Application

- Navigate to the project root directory (`ai-architect`, where `docker-compose.yml` is located).
- Build and start all services:

```bash
docker-compose up --build
```

> The first build may take several minutes.

---

## IV. Accessing the Application

- **Frontend UI:** [http://localhost:3000](http://localhost:3000)  
- **Backend API Base URL (for direct testing if needed):** [http://localhost:8080/api](http://localhost:8080/api)

---

## V. Key Features to Test

1. Navigate to the frontend UI: [http://localhost:3000](http://localhost:3000)
2. Perform **Project CRUD operations**:
   - Create
   - View List
   - View Detail
   - Update
   - Delete
3. On a Project Detail page, test **Text-to-Image** generation:
   - Enter a prompt.
   - Click **"Generate Image."**
   - Verify the image appears in the **"Image Creation History."**
   - View details of the generated image.
4. Check the `media_files/output/{projectId}/` directory on your host machine for saved images.

---

## VI. Stopping the Application

- In the terminal where `docker-compose` is running, press `Ctrl+C`.

**Optional:** To remove containers and networks, run:

```bash
docker-compose down
```
