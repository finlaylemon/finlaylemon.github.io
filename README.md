# Finlay Lemon — Portfolio

Personal portfolio site: featured projects, a résumé page, and a wind tunnel image gallery.
It is a single static page (`index.html`) with no build step.

## Structure

```
index.html              Page, styles and scripts
assets/
  img/                  Project images and the video poster frame
  video/                Wind tunnel flow clip (WebM, with MP4 fallback)
  models/llr.glb        Lunar Logistics Rover model for the 3D viewer
  docs/                 Résumé and MSRR design report (PDF)
.nojekyll               Tells GitHub Pages to serve files as-is
```

The 3D viewer uses three.js r128, loaded from cdnjs and jsDelivr. Fonts come from Google Fonts.

## Publish on GitHub Pages

1. Create a repository (for a site at `https://<username>.github.io`, name it `<username>.github.io`).
2. Upload everything in this folder to the root of the repository, including `.nojekyll`.
3. In the repository, go to **Settings → Pages**. Under **Build and deployment**, set **Source** to
   **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. The site is live a minute or two later at the address shown on that page.

### Custom domain (optional)

1. In **Settings → Pages → Custom domain**, enter the domain (for example `finlaylemon.ca`) and save.
   GitHub adds a `CNAME` file to the repository.
2. At your domain registrar, add DNS records:
   - For the bare domain: four `A` records pointing to `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153` and `185.199.111.153`.
   - For `www`: a `CNAME` record pointing to `<username>.github.io`.
3. Once DNS has updated, tick **Enforce HTTPS** in the Pages settings.

Check GitHub's Pages documentation for the current IP addresses before adding the records.

## Preview locally

The 3D model loads with `fetch`, so open the page through a local server rather than double-clicking the file:

```
python3 -m http.server
```

Then visit `http://localhost:8000`.

## Updating content

- **Images:** replace a file in `assets/img/` with one of the same name, or change the `src` in `index.html`.
  Update the `width` and `height` attributes to the new image's size.
- **3D model:** export from SolidWorks as glTF Binary (`.glb`), keep it small (ideally under 2 MB), and replace `assets/models/llr.glb`.
- **Résumé:** replace `assets/docs/Finlay-Lemon-Resume.pdf`. Everything in this repository is public, so leave
  phone numbers and home addresses out of the PDF.
- **LLR report:** when it is ready, add the PDF to `assets/docs/` and replace the "Coming soon" button in the
  Lunar Logistics Rover section with a link, matching the MSRR "Read the design report" button.
