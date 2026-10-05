# Deploying FF Battle Arena on Render

This is a Node.js/Express app with a SQLite database and payment-proof image uploads. Deploy it as a **web service with persistent disk**, not as a static site (GitHub Pages cannot run its API).

## Render setup

[Start the Render deployment](https://render.com/deploy?repo=https%3A%2F%2Fgithub.com%2Ftaharandhawa328%2FFF-BATTLEARENA%2Ftree%2Farena%2F01a10abe-ff-battlearena), sign in to Render, and approve access to the GitHub repository. The setup page will show the resources and any charges before you approve deployment.

1. Confirm the repository and `arena/01a10abe-ff-battlearena` branch in Render's setup flow. If opening the dashboard manually, choose **New > Blueprint** and connect that branch.
2. Review the Singapore web service and 5 GB persistent disk mounted at `/var/data`. Render may charge for the service and disk; check the displayed price before approving.
3. Set `ADMIN_USERNAME` and `ADMIN_PASSWORD` when Render prompts for the unsynced variables. Use strong, unique values and keep them in Render's environment settings—never commit them to Git or share them in chat.
4. After deployment, Render provides the public URL. Check `<your-service-url>/api/status`; the admin page is at `<your-service-url>/admin.html`.

The SQLite database, database backups, and uploaded payment-proof images are all stored under `/var/data` so they survive redeploys. The service must stay as a single instance when using SQLite and a disk.
