# Connectly Prototype — deployment notes

## What changed
- Preserved the existing page structure and styling; added only the requested OpenAlex search field and loading state.
- Added client-side PDF text extraction using `pdfjs-dist`. Uploaded CV/profile PDF bytes are read in the browser and are not sent to a server.
- Added working Manual Paste candidate import and PDF profile import with the actual filename and source tags.
- Added keyword-responsive mock OpenAlex results (no API proxy and no LinkedIn scraping).
- Added relevance scoring using the current networking goal, target roles, experience, headline, and locally extracted CV text. Shortlist ranking updates when the goal is changed.
- Finalize now opens Discover with the highest-ranked candidates (up to five; smaller pools remain smaller).

## Deploy with Vercel
1. Extract this ZIP and create a GitHub repository with the project files.
2. Import the repository into Vercel.
3. Framework preset: Vite. Build command: `npm run build`. Output directory: `dist`.
4. Deploy. Vercel will install dependencies from `package.json`, including `pdfjs-dist`.
5. Share the generated `https://<project>.vercel.app` URL.

No environment variables are required for this mock prototype. OpenAlex is mock-only. PDF extraction is browser-side only.

## Local run
```bash
npm install
npm run dev
```

## Notes
- PDF text extraction works with text-based PDFs. Scanned/image-only PDFs require OCR before upload.
- The OpenAlex results are explicitly mock records for demo purposes, not real researcher records.
