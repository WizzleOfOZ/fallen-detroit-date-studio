# ANGELS OF ANARCHY: FALLEN DETROIT — THE TWO SOULS STUDIO

A private creative website for **Phil and Kris** to build proposed content together for *Angels of Anarchy: Fallen Detroit*.

**Included:** dark gothic desktop/mobile design, six-act date-night itinerary, 17 established districts, district concept forge, drag-and-connect room architect, character concept lab, AI-image concept gallery with automatic image resizing, alternating horror story relay, five-category two-person music exchange, two independent AI engine workspaces, joint proposal approval, local autosave, JSON import/export, GDD addendum export and OPTIONAL cross-PC Firebase Realtime Database synchronization.

## 1. Open the website immediately (local-only)

1. Extract the ZIP to a folder on Windows.
2. Double-click `index.html` to open it in Chrome or Edge.
3. Navigate the left sidebar. Content saves in **that browser on that computer** automatically when you press Save/Add or move a room card.
4. Choose the Phil or Kris seat at the top. Each person can explore the site without an account.
5. Try **Room Architect → + Three-room starter**, then drag the cards, use **Link**, and edit details in the inspector.
6. Visit **Studio & Sync → Export full studio backup** after your session.

**Local-only mode does not sync between two separate PCs.** For a shared live session, continue with steps 2–4. A static site alone cannot provide live synchronization.

## 2. Put the website online (recommended: GitHub Pages)

A link must be accessible from **both PCs** before you can share a collaborative session.

1. Create a GitHub repository, for example `fallen-detroit-date-studio`. Prefer a private repository if appropriate; check your GitHub plan's Pages availability/visibility options. **GitHub Pages sites themselves may be publicly accessible even when their source is private.** Do not rely on obscurity for sensitive data.
2. Upload `index.html`, `styles.css`, `app.js`, the `assets` folder, and optionally this README. The `index.html` must be in the repository root.
3. Go to repository **Settings → Pages**.
4. In **Build and deployment**, choose **Deploy from a branch**, select `main`, `/ (root)`, and save.
5. Open the website URL GitHub provides (usually `https://YOURNAME.github.io/REPOSITORY/`). Verify the website loads on both computers before proceeding.

Other static hosts such as Cloudflare Pages or Netlify will also work. **Do not share a local `file:///` link; it only points to your own computer.**

## 3. Create the shared Firebase Realtime Database

The site cannot create a Firebase project for you. This is a one-time external service setup.

1. Open [https://console.firebase.google.com](https://console.firebase.google.com/).
2. Select **Add project** and create a project. Analytics is optional for this website.
3. Within the project, open **Build → Realtime Database → Create Database**. Select a suitable region and create the database. Copy the exact HTTPS **database URL**, for example `https://your-project-default-rtdb.firebaseio.com` or `https://your-project-default-rtdb.REGION.firebasedatabase.app`.
4. Open the **Rules** tab in Realtime Database. Replace the database rules with the contents of `firebase-rules.json`, then publish. This restricts access to unguessable 40-character room paths; it is **not authenticated user access control**. Anyone with the invite link can read and write that room. The random token makes unsolicited guessing impractical, but it does not protect a leaked invite link.
5. In **Project settings → General → Your apps**, register a **Web app** (`</>` icon). No Firebase Hosting is required.
6. Copy the JavaScript **firebaseConfig** object values. This is the public Web App configuration, **not** a Firebase Admin SDK service-account private key. Ensure it includes your Realtime Database URL. Example:

   ```json
   {
     "apiKey": "YOUR_PUBLIC_FIREBASE_WEB_API_KEY",
     "authDomain": "YOUR-PROJECT.firebaseapp.com",
     "databaseURL": "https://YOUR-PROJECT-default-rtdb.REGION.firebasedatabase.app",
     "projectId": "YOUR-PROJECT",
     "appId": "1:123456789:web:abcdef123456"
   }
   ```

7. Load your hosted website → **Studio & Sync**, paste that JSON into the configuration box, and select **Create private shared room**.
8. Once connected, select **Copy invite link**. Send that link privately to Kris. The URL contains only the public Firebase Web App identifiers plus a secret, unlisted room token; treat the *whole link* as private.
9. Kris opens it in Chrome or Edge on her own PC. The site loads your shared session automatically. She selects **Kris** at the top (or in the welcome panel); you select **Phil**.
10. Edit a room or add a story beat. Changes to individual saved records should appear in the other person's browser through Firebase Realtime Database.

**Important:** Firebase might require a billing plan for certain configurations/quotas. Review Firebase's current pricing and free allowances yourself. The studio doesn't provision cloud infrastructure or guarantee free usage. It dynamically loads the Firebase Web SDK from Google's CDN when a room is connected, so internet access is required for live mode.

### Security model and limitations

- The room link is a **bearer key**: anyone with it can read/edit the room. There are no real user accounts, per-user passwords, or tamperproof votes. Switching seats is a trust-based mechanism for a private couple's session.
- The included database rules prevent broad root-level list reads and require a long 40-hex-character key. They do **not** prevent someone with an invite from deleting or changing data.
- Do not save passwords, addresses, confidential personal information, administrative tokens or paid AI credentials.
- All your local browser data can be lost if site storage is cleared. Export a full JSON backup after each date.
- Saving two different edits to **the same field at the same moment** may result in last-write-wins; work on separate sections or take turns for contested fields.
- If edits seem delayed while you're typing in a form, finish the field and press its **Save** button.
- This is a creative prototype, not a hardened production collaboration service. A production version should use Firebase Authentication, identity-bound votes, stricter validation and conflict resolution.

## 4. Each person uses their own AI engine

No API keys or provider accounts need to be connected to the website.

1. Navigate to **Dual AI Forge**.
2. Select **District environment**, **Room and gameplay**, **Character/creature**, **Narrative continuation**, **Visual concept art**, or **GDD consistency audit**.
3. Select **Copy this prompt**. It includes the current selected district and already-saved proposed material, plus the locked 17-district / 666-room constraints.
4. Phil pastes it into his own AI engine; Kris pastes it into hers. They may use totally different models.
5. Each returns to the studio, types their AI engine name on the matching AI desk, pastes the result and selects **Save draft**.
6. Compare the two responses; choose one, combine elements, or write a third idea.
7. Select **Send to Vault** to put an AI response forward for review.
8. In **Canon Vault**, Phil and Kris each select **Approve** from their own seat. Two approvals mark the idea **jointly approved as a concept**, **not official GDD canon**.

If you need an actual live AI chat integrated into this page later, you would need secure server-side proxy endpoints and provider APIs. Storing private AI keys in public website JavaScript or local browser fields is not recommended.

## 5. Save the date-night discoveries to development materials

1. Open **Studio & Sync**.
2. Download **Full studio backup (.json)** to preserve editable content.
3. Download **GDD concept addendum (.md)** to get a readable record of district ideas, room proposals and links, characters, story, song references, visual-art references and the Canon Vault approvals. The original compressed concept images remain in the JSON backup, not in the Markdown export.
4. Check each concept against your current authoritative GDD, the actual room index, ability gates, progression, connection constraints, and the current room distribution before choosing where it belongs in the game.
5. Integrate only intentionally approved, reconciled ideas into your production GDD and Godot project. This site **does not edit the original GDD or Godot files**.

## Design notes

The 17 district names follow the user's current *AoA Fallen Detroit v20 Complete Master GDD*. The 666-room total and Cathedral of Static hub anchor are source-backed. The site does **not** ship, reproduce, modify or redistribute the full GDD; it uses a minimal district identity index. The three-room starter is intentionally **example content**, not canonical rooms. The art is a custom SVG website illustration, not in-game production art.

**Date-night order:** The First Transmission → District Forge → Three Rooms from Hell → Character Lab → Story Relay → Music + Canon Vault + quiet ending.
#   f a l l e n - d e t r o i t - d a t e - s t u d i o  
 