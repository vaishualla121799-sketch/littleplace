# A Little Place for You ♡ — Firebase + Vercel gift website

This is a static, mobile-friendly gift website based on your original HTML. It includes:
- Gift-box opening animation and confetti reveal
- Owner-only editor (Firebase email/password sign-in)
- Public, unique gift URL
- Firebase Storage photo uploads, caption edits and photo removal
- Editable letter, recipient name, home message and open-when notes
- Interactive shared garden: visitors can plant flowers and wishes
- Soft original background melody generated in the browser (no music file or copyrighted track)
- Firebase Firestore and Storage security rules

## Important: what is already built vs what needs your account

The website code is ready. A live share URL cannot be created until you connect your own Firebase project and deploy it to Vercel. This project does not contain your Firebase credentials, and you should never share those credentials or your owner password.

## 1. Create a Firebase project (free tier available, usage limits apply)

1. Open https://console.firebase.google.com/ and create a project.
2. In Project settings → General → Your apps, add a **Web app**.
3. Copy the Firebase web configuration into `firebase-config.js`, replacing every `YOUR_...` placeholder.
4. In Build → Authentication → Sign-in method, enable **Email/Password** and **Anonymous**.
5. In Build → Firestore Database, create a database.
6. In Build → Storage, get started and create the default bucket.
7. In Firestore → Rules, paste the contents of `firestore.rules` and publish.
8. In Storage → Rules, paste the contents of `storage.rules` and publish.

The first account you create through the website becomes the owner of the gift it creates. Keep that login private.

## 2. Deploy to Vercel

1. Extract this ZIP.
2. Create a GitHub repository and upload the files in this folder (`index.html`, `firebase-config.js`, `vercel.json`, rules and README).
3. Sign in to https://vercel.com/ and import that repository.
4. Framework preset: **Other**. Build command: leave blank. Output directory: `.`.
5. Deploy. Vercel will give you a website address.

You can also use Vercel CLI from this folder: `vercel --prod`.

## 3. Create your gift and share it

1. Open your deployed Vercel website.
2. Select **Create my owner account** and register using your email and a strong password.
3. The website creates a gift and opens the private editor.
4. Edit the recipient name, letter, home message and open-when notes.
5. Upload photos and captions. You can remove or change them later.
6. Select **Copy recipient link**. Send that link to your friend.
7. Keep your own editor link by adding `&edit=1` to the end of the gift URL, or sign in again with the gift URL.

Example:
- Recipient: `https://your-site.vercel.app/?gift=GIFT_ID`
- Owner editor: `https://your-site.vercel.app/?gift=GIFT_ID&edit=1`

## 4. A few practical notes

- Music is an original, gentle Web Audio melody. Browsers require a tap before audio can start; the gift opening tap starts it. The music button can pause/resume it.
- Photos are public to anyone who has the gift URL. Do not upload private or sensitive images.
- Garden flowers and wishes are stored in Firestore and appear to visitors of the same gift. Visitors need anonymous authentication enabled.
- Only the owner can change gift text and photos. A recipient can interact with the garden but cannot edit gift content.
- This starter does not include a “forgot password” screen. Use Firebase Authentication's password reset from the Firebase Console if needed, or add a reset flow later.
- Firebase free usage has limits and may require billing configuration for some Storage projects/regions. Check the current Firebase plan and bucket setup shown in your console before uploading many photos.
- The Firestore and Storage rules are included as a sensible baseline. Test the deployed project with a separate visitor account/browser before sending the link widely.

## Troubleshooting

**“Could not open this gift”**: check the gift ID in the URL, Firebase config, Firestore rules, and Authentication settings.

**Photo upload fails**: check that Firebase Storage is enabled, the bucket name in `firebase-config.js` is exact, and Storage rules are published. Some Firebase Storage setups require a billing-enabled project; follow the requirement shown in your Firebase Console.

**Garden cannot save**: enable Anonymous sign-in and publish `firestore.rules`.

**Blank page / Firebase error**: check browser console and ensure all placeholders in `firebase-config.js` have been replaced.
