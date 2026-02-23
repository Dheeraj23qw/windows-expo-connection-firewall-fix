
---

# How to Fix Expo Connection Timeout and Windows Firewall Errors

If your Expo terminal runs but your phone cannot connect to the local development server, you are likely experiencing a firewall block. This guide provides solutions for Windows Defender, AVG, and Avast.

## 1. Fix Windows Firewall Blocking Node.js

Windows Defender Firewall often blocks Node.js inbound connections by default, preventing your phone from reaching the server.

1. Search for **Windows Defender Firewall with Advanced Security**.
2. Click on **Inbound Rules** in the left sidebar.
3. Scroll to find all entries named **Node.js**.
4. If an entry shows a red icon, right-click it and select **Properties**.
5. Select **Allow the connection** and click **Apply**.
6. Restart your Expo server.

## 2. Resolve AVG and Avast Firewall Conflicts

Third-party antivirus software like AVG or Avast often overrides Windows settings. Even if Windows allows the connection, these programs may block it.

1. Open your **AVG** or **Avast** dashboard.
2. Navigate to **Menu > Settings > Protection > Enhanced Firewall**.
3. Either turn off **Enhanced Firewall** or add **node.exe** to the **Allowed Apps** list.
4. Restart your computer if the connection still fails.

## 3. Expo SDK 54 Deep Linking Configuration

For Expo SDK 54 and higher, you must define a "scheme" in your configuration file to prevent connection errors during deep linking.

Update your **app.json** file:

```json
{
  "expo": {
    "scheme": "your-app-name"
  }
}

```

## 4. Troubleshooting Checklist

If the "Connection Timed Out" error persists, verify the following:

* **Inbound Rules:** Ensure Node.js is set to "Allow" in Windows Firewall.
* **Antivirus:** Disable the Enhanced Firewall feature in AVG or Avast.
* **App Config:** Ensure the "scheme" property exists in your `app.json`.
* **Network Profile:** Set your Windows Network Profile to **Private** instead of Public.
* **Clear Cache:** Restart your project using the clear command:
`npx expo start --clear`

---
