# Flyout — "More" Button
## Paste into MagicPath chat

---

Add a flyout panel that appears when the user hovers or clicks the "More" (•••) button on the left sidebar. The flyout extends to the right of the sidebar.

## FLYOUT PANEL STYLING
- Width: 320px
- Background: white
- Border-radius: 16px
- Shadow: large soft shadow (0 8px 32px rgba(0,0,0,0.10))
- Subtle border: #E5E7EB
- Anchored to the right edge of the sidebar, vertically aligned with the "More" button (near the bottom of the sidebar)
- Show it open in this design

## FLYOUT CONTENT

A clean vertical list of additional navigation items. Each item is a row with: icon (20px, gray) + label (14px, dark text) + optional right-side detail text (12px, gray) or badge.

### Items:

1. **📡 Channels**
   Right detail: "3 connected"
   
2. **🔌 Services**
   Right detail: "5 connected"

3. **📖 Training**
   Right detail: "35% complete" with a tiny green progress bar

4. **📊 Analytics**
   Right detail: "↑ 12% this week" in green

5. **🧬 Brand Profile**
   Right detail: "✅ Active"

6. **📋 Strategy**
   Right detail: "April plan active"

---

Divider line (subtle gray, 1px)

---

7. **🌙 Dark Mode**
   Right side: toggle switch (off position)

8. **❓ Help & Support**
   Right detail: small arrow →

9. **📱 Download App**
   Right detail: small arrow →

---

### Bottom of flyout:

A subtle card with the user profile:
- Teal circle "SC" avatar + "Dr. Sarah Chen" bold + "Pro Plan" gray text beneath
- Small gear ⚙️ icon on the right (links to Settings)

---

## DESIGN NOTES
- Show this flyout OPEN in the design
- Each row has a subtle hover state (light gray #F3F4F6 background on hover)
- The items with right-side detail text create a clean two-column feel within the list (label left, detail right)
- The profile card at the bottom has a slightly different background (#F8F9FA) to separate it from the list
- Clean, minimal, no clutter — this is a utility menu for secondary features
- Items 1-6 are shortcuts that switch to the corresponding tab on the right panel when clicked
- Divider separates platform navigation (top) from utility options (bottom)
