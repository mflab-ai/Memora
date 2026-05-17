# Privacy Policy for Memora (Re-Moment)

**Effective Date:** May 17, 2026

This Privacy Policy explains how Memora ("we", "our", or "us") handles information when you use the Memora mobile application (the "App"). Memora is designed as a local-first photo indexing and memory-story rendering app.

## 1. Photos Access and Local Processing

Memora requests Photos library access so it can index assets, build recommendations, prepare story drafts, and render videos. The App may process photo metadata, thumbnails, image content, face-count signals, scene signals, quality signals, captions, and location/date information that is available through Apple's Photos APIs.

Standard indexing, recommendations, search, story review, and video rendering run on the user's device. Local app data such as indexes, generated stories, render jobs, preferences, checkpoints, diagnostics, and person profiles is stored in the App sandbox with SwiftData and related local storage. If the user enables iCloud Drive-backed storage, that database may sync through the user's personal Apple iCloud account. We do not have direct access to the user's iCloud account or local Photos library.

## 2. Pro Vision AI

Pro Vision AI is optional. If the user enables and uses it, selected image data and related request metadata may be sent to our backend and configured VLM provider to generate captions or process remote-assisted indexing.

The service is designed not to retain original image bytes for product use, model training, or dataset creation. Operational records may be retained, including sanitized request metadata, generated caption text or provider response text, request identifiers, request status, quota counters, entitlement identifiers, device hashes, timestamps, and error details. These records are used for entitlement validation, quota enforcement, idempotency, debugging, security, fraud prevention, and abuse prevention.

We do not use the user's photos or generated private photo metadata to train or fine-tune AI models.

## 3. Purchases, Entitlements, and Quota

In-app purchases are processed by Apple. We do not receive credit card or other payment details. To validate purchases and manage Pro Vision AI quota, the App and backend may process StoreKit transaction claims, product identifiers, entitlement status, quota usage, server-issued access tokens, and device hash values.

## 4. Diagnostics

Memora may use Apple-provided diagnostics such as MetricKit to help identify crashes, hangs, launch issues, CPU exceptions, and disk-write issues. These diagnostics are intended for stability troubleshooting and do not include the user's original photo files.

## 5. Security and Retention

We use reasonable technical and organizational safeguards appropriate for a small application service, including Apple platform sandboxing, Keychain-backed app secrets where applicable, server-side entitlement checks, short-lived server tokens, request size validation, idempotency checks, and quota enforcement.

Operational backend records are retained only as long as reasonably needed for the purposes described above, unless a longer period is required for legal, security, accounting, or dispute-resolution reasons.

## 6. User Choices

Users can control Photos access in iOS or iPadOS Settings, choose whether to use Pro Vision AI, and choose whether to use local or iCloud Drive-backed database storage where available. Disabling Photos access or Pro Vision AI may limit some App features.

## 7. Changes to This Policy

We may update this Privacy Policy from time to time. Material changes will be reflected by updating the Effective Date and publishing the revised policy on this page.

## 8. Contact

For privacy questions, contact MFLab-AI (Sang Hun Kim) through the public repository or the contact channel provided with the App.
