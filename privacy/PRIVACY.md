# Privacy Policy for Daily Coding Tracker Pro (DCT)

**Last updated:** June 2026

Daily Coding Tracker Pro ("DCT", "we", "the extension") is committed to protecting your privacy. This policy explains what data we collect, how it is used, and your rights regarding that data.

## 1. Information We Collect

**Personally Identifiable Information**
When you sign in with Google, we collect your Google account email address and a unique user ID via Firebase Authentication. This is used solely to associate your solve history with your account for cloud sync.

**Solve Activity Data**
DCT automatically detects and stores records of problems you solve on LeetCode, Codeforces, CodeChef, and HackerRank, including problem name, platform, difficulty rating, and timestamp.

**Local Error Logs**
A rolling log of up to 200 technical error entries is stored locally to help diagnose extension issues. These logs may be synced to Firestore for debugging purposes and do not contain personal browsing content.

## 2. What We Do NOT Collect

We do not collect health information, financial or payment information, passwords or credentials from third-party sites, personal communications (emails, chats), precise location data, full web browsing history, or keystroke/mouse activity.

## 3. How We Use Your Information

Your data is used exclusively to:
- Detect and log your problem-solving activity
- Calculate streaks, statistics, and analytics within the extension
- Sync your solve history across your devices via Firebase
- Diagnose and fix technical errors

We do not use your data for advertising, profiling, or any purpose unrelated to DCT's core function of tracking coding practice.

## 4. Data Storage

Solve history and logs are stored locally on your device using `chrome.storage.local`. If you sign in, this data is also synced to a private Firebase Firestore database associated with your account. Local data is automatically cleared when you log out.

## 5. Data Sharing

We do not sell, rent, or transfer your personal data to third parties. Data is shared only with Firebase (Google) as our cloud infrastructure provider, solely to deliver the syncing functionality described above.

## 6. Data Retention & Deletion

You can delete your locally stored data at any time by logging out of the extension or clearing extension storage via Chrome settings. To request deletion of your cloud-synced data, contact us at the email below.

## 7. Permissions Used

- **storage**: to save your solve history and preferences locally
- **identity**: to authenticate you via Google Sign-In
- **tabs**: to manage the OAuth login tab
- **host permissions**: to read solve status from supported coding platforms and communicate with Firebase

## 8. Children's Privacy

DCT is not directed at children under 13, and we do not knowingly collect data from children under 13.

## 9. Changes to This Policy

We may update this privacy policy from time to time. Changes will be reflected with an updated "Last updated" date above.

## 10. Contact

If you have questions about this privacy policy or your data, contact us at: **[your email here]**