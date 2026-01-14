# iOS Shortcut Automation Guide for SideStore Refresh

## Overview

This guide shows you how to create an iOS Shortcut that automatically refreshes your SideStore apps without needing to open the app manually. This is especially useful for keeping your LiveContainer + SideStore setup running smoothly.

## What You'll Need

- iPhone with iOS 15 or later
- SideStore already installed and paired (follow the main guide first)
- Shortcuts app (built into iOS)
- LocalDevVPN profile installed and active

## Understanding Auto-Refresh

SideStore apps need to be refreshed every 7 days because of Apple's free developer certificate limitations. Instead of remembering to do this manually, we can automate it using iOS Shortcuts.

***

## Creating the Refresh Shortcut

### Step 1: Open Shortcuts App

1. Open the **Shortcuts** app on your iPhone
2. Tap the **+** button in the top right to create a new shortcut
3. Tap **Add Action**

### Step 2: Add URL Action

1. Search for **URL** in the actions search
2. Add the "URL" action
3. Enter this URL: `sidestore://refresh`

### Step 3: Add Open URLs Action

1. Search for **Open URLs**
2. Add the "Open URLs" action below the URL action
3. It should automatically connect to the URL from step 2

### Step 4: Name Your Shortcut

1. Tap on the shortcut name at the top (likely "New Shortcut")
2. Rename it to something like **"Refresh SideStore"**
3. Tap **Done** to save

***

## Setting Up Automation

Now let's make this shortcut run automatically.

### Creating a Time-Based Automation

1. In the Shortcuts app, tap the **Automation** tab at the bottom
2. Tap **+** (or "Create Personal Automation" if it's your first)
3. Select **Time of Day**

### Configure the Automation

1. **Time Settings:**
   - Choose a time when your iPhone is typically unlocked and connected to Wi-Fi
   - Good options: 7:00 AM, 12:00 PM, or 9:00 PM
   - Set it to **Daily** or choose specific days

2. **Repeat Settings:**
   - Select **Daily** for maximum reliability
   - Or choose **Weekly** if you want it to run once a week

3. Tap **Next**

### Add the Refresh Action

1. Tap **Add Action**
2. Search for **Run Shortcut**
3. Select "Run Shortcut"
4. Tap **Shortcut** and select your "Refresh SideStore" shortcut
5. Tap **Next**

### Disable Confirmation (Important!)

1. Toggle **OFF** the "Ask Before Running" option
2. This allows the automation to run without your interaction
3. Tap **Done**

***

## Alternative: NFC Tag Automation

You can also trigger the refresh by tapping an NFC tag.

### Setting Up NFC Automation

1. In Shortcuts, go to **Automation** tab
2. Tap **+** to create new automation
3. Select **NFC**
4. Tap **Scan** and hold your NFC tag to your iPhone
5. Name the tag (e.g., "SideStore Refresh")
6. Tap **Next**
7. Add the **Run Shortcut** action
8. Select your "Refresh SideStore" shortcut
9. Toggle OFF "Ask Before Running"
10. Tap **Done**

Now you can refresh SideStore just by tapping your iPhone to the NFC tag!

***

## Advanced: Low Power Mode Trigger

You can also set up an automation that reminds you to refresh when your battery is low.

### Low Power Mode Automation

1. Create new automation
2. Select **Low Power Mode**
3. Choose **Is Turned On**
4. Add action: **Run Shortcut**
5. Select "Refresh SideStore"
6. This runs every time you enable Low Power Mode

***

## Troubleshooting

### Automation Not Running

- **Check Wi-Fi**: Ensure your iPhone is connected to Wi-Fi
- **Check LocalDevVPN**: Make sure the VPN profile is active
- **Check SideStore**: Open SideStore manually once to ensure it's properly configured
- **Check Shortcuts Settings**: Go to Settings → Shortcuts → Allow Running Scripts (should be ON)

### "Ask Before Running" Keeps Appearing

- This is an iOS security feature
- The first few times, you may need to allow it manually
- After several successful runs, iOS should stop asking
- Make sure you've toggled OFF "Ask Before Running" in the automation settings

### Refresh Fails

- Open SideStore manually and check for errors
- Verify your pairing file is still valid
- Make sure Developer Mode is still enabled
- Check that LocalDevVPN is connected

### Apps Still Expire

- The 7-day refresh period starts from the last refresh, not installation
- Run the shortcut manually once to confirm it works
- Check the Shortcuts app history to see if automations ran successfully
- You may need to manually refresh if you miss several automatic refresh cycles

***

## Tips and Best Practices

### Optimal Refresh Schedule

- **Daily at 9 PM**: Runs when you're likely at home on Wi-Fi
- **Every 3 days at noon**: Reduces battery impact while staying safe
- **Weekly on Sunday morning**: Minimal automation, requires manual awareness

### Battery Impact

- The refresh process uses minimal battery
- Running daily vs. every 3 days has negligible impact
- The peace of mind is worth the tiny battery cost

### Multiple Automations

- You can create multiple triggers for the same shortcut
- Example: Daily time-based + NFC tag + Low Power Mode
- This gives you both automatic and manual options

### Backup Reminder

- Even with automation, set a phone reminder for every 6 days
- This ensures you catch any automation failures
- Better to refresh early than lose your apps

***

## Testing Your Automation

### Manual Test

1. Open the Shortcuts app
2. Go to your "Refresh SideStore" shortcut
3. Tap it to run manually
4. SideStore should open and begin refreshing
5. Wait for "Refresh Complete" message

### Automation Test

1. In Shortcuts, go to **Automation** tab
2. Find your refresh automation
3. Tap on it
4. Tap **Run Now** (if available)
5. Or temporarily change the time to 1 minute from now to test

***

## Security Notes

- The `sidestore://refresh` URL is a safe, official SideStore URL scheme
- Running shortcuts doesn't expose your Apple ID or pairing file
- Automations only work when your iPhone is unlocked (for security)
- No data is sent to external servers during refresh

***

## Advanced Customization

### Adding Notifications

You can add a notification to confirm the refresh:

1. Edit your "Refresh SideStore" shortcut
2. After the "Open URLs" action, add **Show Notification**
3. Set the message to: "SideStore refresh started!"
4. This gives you visual confirmation

### Creating a Widget

1. Long press on your Home Screen
2. Tap **+** in the top left
3. Search for **Shortcuts**
4. Select a widget size
5. Tap on the widget to configure
6. Select your "Refresh SideStore" shortcut
7. Now you can tap the widget to refresh instantly

### Siri Integration

1. Open Settings → Siri & Search
2. Scroll to Shortcuts
3. Find "Refresh SideStore"
4. Tap **Add to Siri**
5. Record a phrase like "Refresh my apps"
6. Now you can say "Hey Siri, refresh my apps"

***

## Frequently Asked Questions

**Q: Do I need to keep Shortcuts app open?**
A: No, automations run in the background even if the app is closed.

**Q: Will this work if my phone is locked?**
A: No, iOS requires the device to be unlocked for security reasons.

**Q: Can I run this on cellular data?**
A: Yes, but Wi-Fi is recommended for better reliability.

**Q: How do I know if the automation ran?**
A: Check the Shortcuts app → Automation tab → tap on your automation to see run history.

**Q: Will this drain my battery?**
A: No, the impact is negligible (less than 1% per refresh).

**Q: Can I use this with multiple SideStore installations?**
A: Yes, the URL scheme works with all SideStore installations on your device.

**Q: What if I'm away from home for more than 7 days?**
A: You can manually run the shortcut on cellular data, or use a mobile hotspot.

***

## Conclusion

With this automation setup, you'll never have to worry about your SideStore apps expiring. The shortcut runs silently in the background, keeping your LiveContainer and all your sideloaded apps working perfectly.

Remember: The automation is a convenience tool, not a guarantee. Always have a backup plan and check manually every few days until you're confident in your setup.

***

## Related Links

- [Main LiveContainer + SideStore Guide](README.md)
- [SideStore Official Documentation](https://sidestore.io/)
- [iOS Shortcuts User Guide](https://support.apple.com/guide/shortcuts/)


**Created By Dunamis**
