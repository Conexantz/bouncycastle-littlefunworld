# LittleFunWorld

Bouncy castle rental website for LittleFunWorld, Singapore. One static page (`index.html`) with five sections: Home, Book, Gallery, Reviews and Terms.

## How it works

- **Enquiries:** the Book form saves each enquiry to the Supabase table `bc_enquiries`, then opens WhatsApp (web.whatsapp.com on a computer, the app on a phone) with the details filled in for +65 8115 7896. The customer presses Send.
- **Castles:** loaded from `bc_castles` (name, tagline, size, photo). Photos come from the shared Google Drive castle folder.
- **Gallery:** photo IDs come from `bc_gallery`; the photos are in the shared Google Drive gallery folder. 12 photos per page in a 4 x 3 grid.
- **Reviews:** approved rows from `bc_reviews` are shown. New reviews submitted on the site stay hidden until `approved` is set to true in Supabase.

The page has built-in copies of the castles and photo list, so it still works if Supabase can't be reached.

## Deploy on Vercel

1. In Vercel, choose **Add New → Project** and import this repository.
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Click **Deploy**.

No environment variables are needed. The Supabase publishable key in `index.html` is meant to be public; row-level security limits it to submitting enquiries and reviews and reading castles, gallery photos and approved reviews.

## Updating content

| What | Where |
|---|---|
| Castle names, sizes, photos | Supabase `bc_castles` |
| Gallery photos | Add to the Drive folder, then add the file ID to `bc_gallery` |
| Approve or hide reviews | Supabase `bc_reviews.approved` |
| See enquiries | Supabase `bc_enquiries` |
| WhatsApp number | `WA_NUMBER` near the top of the script in `index.html` |
