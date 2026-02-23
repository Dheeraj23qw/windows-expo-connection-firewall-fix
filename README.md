

```md
# Windows Firewall & Expo Connection Timeout Fix (Node.js / AVG / Avast)

If your terminal is running fine but your phone times out when connecting to Expo or a local dev server, the issue is often a hidden firewall block — especially caused by AVG or Avast overriding Windows Firewall rules.

This guide explains how to fix:

- Hidden firewall blocks
- AVG / Avast Enhanced Firewall conflicts
- Node.js inbound rule issues
- Expo SDK 54+ deep linking (scheme) issue

---

## 1️⃣ Hidden Firewall Block (Windows)

If:
- `npx expo start` runs fine
- QR code scans
- But the phone says **"Connection Timed Out"**

👉 This usually means Windows Firewall is blocking Node.js silently.

### Fix:

1. Open:
```

Windows Defender Firewall with Advanced Security

```

2. Click:
```

Inbound Rules

```

3. Find:
```

Node.js

```

4. If you see a **Red circle with slash icon**:
- Right-click → **Properties**
- Select → **Allow the connection**
- Apply & Save

Restart Expo after this.

---

## 2️⃣ AVG / Avast Firewall Trap (Very Common)

AVG & Avast override Windows Firewall even if Windows shows "Allowed".

### Fix:

1. Open AVG / Avast Dashboard
2. Go to:
```

Menu → Settings → Protection → Enhanced Firewall

```
3. Turn OFF:
```

Enhanced Firewall

```
OR
4. Add:
```

node.exe

````
to Allowed Apps inside AVG

⚠️ Simply allowing in Windows Firewall is NOT enough if AVG firewall is active.

---

## 3️⃣ Expo SDK 54+ Scheme Fix (Deep Linking Failure)

If you're using SDK 54+, and your app fails to open from Expo Go:

Make sure your `app.json` includes:

```json
{
"expo": {
 "scheme": "yourappname"
}
}
````

Without this, deep linking fails and your phone may show connection errors.

---

## 4️⃣ Quick Checklist

✅ Windows Inbound Rule → Allow Node.js
✅ AVG / Avast Enhanced Firewall → OFF
✅ app.json includes "scheme"
✅ Restart PC after firewall changes
✅ Restart Expo using:

```bash
npx expo start --clear
```

---

## 💡 Why This Happens

* Antivirus software overrides Windows firewall
* Node.js rule becomes blocked after update
* Expo SDK 54 requires explicit scheme for deep linking
* Windows network profile changes (Public vs Private)

---

## 📌 Tested On

* Windows 10 / 11
* Node.js 18+
* Expo SDK 53 / 54
* AVG Antivirus
* Avast Antivirus

---

## ✍️ Author

Dheeraj Kumar

```


Tell me which one you want 🚀
```
