# Firebase Security Rules Setup

## Overview
This document contains the security rules needed to secure your Firebase Realtime Database and Firestore for the voice calling application.

## Files Created
- `firebase-rules.json` - Realtime Database rules
- `firestore.rules` - Firestore security rules

## How to Apply These Rules

### 1. Realtime Database Rules
1. Go to Firebase Console → Project Settings → Realtime Database
2. Click on the "Rules" tab
3. Replace the existing rules with the content from `firebase-rules.json`
4. Click "Publish"

### 2. Firestore Security Rules
1. Go to Firebase Console → Firestore Database
2. Click on the "Rules" tab
3. Replace the existing rules with the content from `firestore.rules`
4. Click "Publish"

## Security Features

### Realtime Database Rules
- Only authenticated users can read/write data
- Users can only write to their own user node (`auth.uid == $uid`)
- Status and lastSeen fields are validated for data types
- Indexes on shortID and email for efficient queries
- Calls collection accessible to all authenticated users

### Firestore Security Rules
- Users can only read/write their own user documents
- Search queries limited to 50 results to prevent abuse
- Calls and ICE candidates accessible to all authenticated users
- Proper authentication checks on all operations

## Important Notes
- These rules assume users are authenticated before accessing any data
- The rules prevent unauthorized access to user data
- Search functionality is preserved while maintaining security
- Call signaling data is accessible to all authenticated users for proper functionality

## Testing
After applying the rules, test:
1. User authentication (Google and email/password)
2. User profile updates
3. User search functionality
4. Call initiation and signaling
5. Online status updates
