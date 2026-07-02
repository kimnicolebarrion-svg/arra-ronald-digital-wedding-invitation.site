# Wedding Website

This site is a static HTML website and can be published publicly using GitHub Pages.

## Publish steps

1. Create a GitHub repository and upload these files:
   - [index.html](index.html)
   - [google-sheets-setup.md](google-sheets-setup.md)
   - [.github/workflows/deploy.yml](.github/workflows/deploy.yml)

2. In GitHub, go to your repository Settings > Pages.

3. Under Source, choose GitHub Actions.

4. Commit and push your files to the main branch.

5. Wait a few minutes for GitHub Pages to build and publish the site.

6. Open the published URL:
   - https://<your-github-username>.github.io/<your-repository-name>/

## Notes

- The site does not need a server because it is plain HTML, CSS, and JavaScript.
- If you want the RSVP form to work, connect it to Google Sheets using [google-sheets-setup.md](google-sheets-setup.md).
