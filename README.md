# VISA Screening Assistant

Static, iPad-friendly clinician web app for the Vision Impairment Screening Assessment (VISA). Designed for GitHub Pages. No backend, analytics, cookies, or remote data storage.

## Deploy on GitHub Pages
1. Create a new GitHub repository (private/public according to your permission and organizational requirements).
2. Upload `index.html`, `styles.css`, `app.js`, and `manifest.webmanifest` to the repository root.
3. In **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Open the resulting Pages URL in Safari on iPad. Use **Share → Add to Home Screen** for an app-like launcher.

## Clinical logic implemented
- VISA is treated as a screening/referral instrument, not a diagnostic test and not a summed numeric scale.
- Immediate referral triggers: abnormal eye alignment, eye movement/nystagmus, visual field findings, and visual-inattention threshold findings.
- Distance acuity screening level: 0.0 or 0.2 in each eye. Reduced: 0.4 or worse.
- Near acuity screening level: N5 or N6 in each eye. Reduced: N8 or worse.
- Grating: small-size achieved is the expected screening level; large-size only is reduced.
- Isolated reduced acuity with otherwise normal screen → re-screen after 3 days; refer if persistent.
- Symptoms/family/visual-observation concern without another identified problem → re-screen after 3 days; refer if persistent.
- Line bisection >6 mm from center → referral trigger.
- Abnormal clock drawing → referral trigger.
- Clock cancellation <42/50 → referral trigger.

## Privacy / PHI
The app does not transmit or persist entered data. Do **not** add browser localStorage, cloud databases, analytics, or third-party scripts for PHI unless your organization has approved the architecture and applicable agreements/security controls.

## Important implementation note
The original VISA testing pack includes calibrated/print-specific visual stimuli and instructs high-quality printing/defined test distances. This app records and interprets those results; it does not attempt to replace calibrated visual-acuity/grating stimuli with arbitrary iPad screen rendering.

## Source
VISA materials © VISION Research Unit, University of Liverpool. Use/distribution remains subject to the permission/license held by the deployer.

## Interactive iPad tasks (v2)
- Visual-field map supports touch/Apple Pencil annotation for suspected loss and observed-normal areas. Referral logic still uses the clinician's VISA field findings.
- Line bisection accepts a direct patient mark and calculates absolute center deviation using the clinician-entered displayed line length. Confirm physical display calibration before relying on the millimeter result.
- Clock drawing supports finger/Apple Pencil drawing, undo, and clear. The app does not algorithmically interpret handwriting; the clinician applies the VISA qualitative criterion.
- Clock cancellation presents 50 large clock targets with small clocks/open circles as distractors and automatically counts selected large clocks. The task remains unscored until the patient begins it.
