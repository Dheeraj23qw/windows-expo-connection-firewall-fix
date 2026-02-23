### Windows Firewall and Expo Connection Timeout Guide

If your terminal runs correctly but your phone cannot connect to your Expo development server, the issue is likely a firewall restriction. This occurs frequently with Windows Defender or third-party antivirus software like AVG and Avast.

---

### 1. Windows Firewall Settings

Windows may silently block Node.js from communicating with your mobile device.

1. Open **Windows Defender Firewall with Advanced Security**.
2. Select **Inbound Rules**.
3. Locate all entries named **Node.js**.
4. If an entry has a red icon, right-click it and select **Properties**.
5. Set the action to **Allow the connection**.
6. Save the changes and restart Expo.

---

### 2. AVG or Avast Firewall Conflict

Antivirus software often overrides Windows settings. Even if Windows allows the connection, these programs may still block it.

1. Open the AVG or Avast dashboard.
2. Navigate to **Menu > Settings > Protection > Enhanced Firewall**.
3. Either disable the **Enhanced Firewall** temporarily or add **node.exe** to the **Allowed Apps** list.

---

### 3. Expo SDK 54+ Configuration

For SDK 54 and newer, you must define a scheme in your configuration for deep linking to function.

Update your **app.json** file:

```json
{
  "expo": {
    "scheme": "your-app-name"
  }
}

```

---

### 4. Summary Checklist

* **Inbound Rules:** Ensure Node.js is allowed in Windows Firewall.
* **Antivirus:** Disable Enhanced Firewall in AVG or Avast.
* **App Config:** Verify that a "scheme" is present in app.json.
* **Restart:** Clear the cache and restart the server using:
`npx expo start --clear`

---
