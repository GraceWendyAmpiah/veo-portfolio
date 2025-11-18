# Veo 3 Prompt Portfolio

This is a simple, static portfolio website designed to showcase the results of Veo 3 text-to-video prompts, combining an input image, the prompt text, and the resulting video.

The project is built with plain HTML, CSS, and JavaScript for the public-facing site, and uses **Decap CMS** (formerly Netlify CMS) for a serverless, Git-based admin panel.

## Features

*   **Public Site:** A clean, responsive gallery that loads data from `data/portfolio.json`. Clicking a card opens a modal with the full details.
*   **Admin Panel:** A dedicated interface (`/admin/`) that allows authenticated users to add new portfolio items (image, video, prompt) and commit the changes directly to the Git repository via Netlify's Git Gateway.

## Deployment to Netlify

Follow these steps to deploy your portfolio and set up the admin panel.

### 1. Project Setup

1.  **Clone the Repository:** Clone this project to your local machine or fork it on GitHub.
2.  **Create a New Netlify Site:** Connect your repository to Netlify.
3.  **Build Settings:**
    *   **Base directory:** (Leave blank)
    *   **Build command:** (Leave blank or use `echo "No build step"`)
    *   **Publish directory:** `/` (The root of the repository)

### 2. Configure Netlify Identity

The admin panel requires Netlify Identity for user authentication.

1.  In your Netlify site dashboard, go to **Site settings** > **Identity**.
2.  Click **Enable Identity**.
3.  Under **Registration**, set the option to **Invite only** to restrict who can sign up for the admin panel.
4.  Under **Services** > **Git Gateway**, click **Enable Git Gateway**. This allows Decap CMS to commit changes to your repository.
5.  **Invite Users:** Go to the **Identity** tab in your Netlify dashboard and invite yourself (and any other administrators) to the site. You will receive an email to set your password.

### 3. Accessing the Admin Panel

1.  Once deployed and Identity is configured, navigate to the admin URL: `[YOUR_NETLIFY_URL]/admin/`
2.  Log in using the credentials you set up via the invitation email.
3.  The Decap CMS interface will load, allowing you to manage the "Portfolio Items" collection.

### 4. Using the Admin Panel

1.  In the CMS, select **Portfolio Items**.
2.  Click **New Portfolio Data** (or similar button, depending on the CMS version).
3.  You will see a list of existing items. Click **Add Projects** to add a new item.
4.  **ID:** A unique ID will be generated automatically.
5.  **Input Image:** Upload your reference image. This will be stored in `public/uploads`.
6.  **Prompt Text:** Enter the full text of your Veo 3 prompt.
7.  **Generated Video:** Upload the resulting video file. This will also be stored in `public/uploads`.
8.  Click **Publish** (or **Save**) to commit the changes to your repository.

**Note:** Each time you publish a change, Netlify will automatically trigger a new build/deploy to update your live site with the new `portfolio.json` data.

## File Structure

```
/
├── admin/
│   ├── config.yml      # Decap CMS configuration
│   └── index.html      # Decap CMS entry point
├── data/
│   └── portfolio.json  # Portfolio data source
├── public/
│   └── uploads/        # Uploaded images and videos
├── index.html          # Public portfolio gallery and modal
├── netlify.toml        # Netlify configuration
└── README.md           # This file
```
