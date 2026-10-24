# Island Rail Stand-In

A web photo stand-in for the Restore Island Rail Society. Visitors upload a photo, line their face up in the hole on the Salish Express sign, and download the finished picture.

Everything runs in the browser. Photos never leave the visitor's device.

## Files

- `index.html` — the whole app (HTML, CSS and JavaScript in one file)
- `boards/salish-express.jpg` — the board artwork (the face hole is cut in code)

## Publish with GitHub Pages

1. Create a repository and upload both files, keeping the `boards` folder.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then **Save**.
4. After a minute the app is live at `https://<your-username>.github.io/<repo-name>/`.

## Changing the board

Replace `boards/salish-express.jpg` with a new 2400×1350 image, then update the `hole` values (centre `x`, `y` and radii `rx`, `ry`, in pixels) in the `SCENES` list near the top of the script in `index.html`.

More at [restoreislandrail.com](https://restoreislandrail.com).
