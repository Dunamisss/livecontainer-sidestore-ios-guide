# LiveContainer + SideStore iOS Guide (Including Shortcuts with LocalDevVPN)
## Contents

- [Important notes](#important-notes) 
- [STEP 1 – What you are installing](#step-1-what-you-are-installing) 
- [STEP 2 – One-time PC requirements](#step-2-one-time-pc-requirements) 
- [STEP 3 – Install SideStore on the iPhone (via AltServer)](#step-3-install-sidestore-on-the-iphone-via-altserver) 
- [STEP 4 – Enable Developer Mode on iPhone](#step-4-enable-developer-mode-on-iphone) 
- [STEP 5 – Create and save the SideStore pairing file](#step-5-create-and-save-the-sidestore-pairing-file) 
- [STEP 6 – Install LiveContainer + SideStore IPA](#step-6-install-livecontainer-sidestore-ipa) 
- [STEP 7 – First-time setup inside LiveContainer](#step-7-first-time-setup-inside-livecontainer) 
- [STEP 8 – Enable JIT-less / VPN mode](#step-8-enable-jit-less-vpn-mode) 
- [STEP 9 – Adding more LiveContainers (optional)](#step-9-adding-more-livecontainers-optional) 
- [STEP 10 – Installing and running IPAs inside LiveContainer](#step-10-installing-and-running-ipas-inside-livecontainer)
- - [iOS Shortcut Automation Guide](SHORTCUT-AUTOMATION-GUIDE.md)
- [Suggested graphics / screenshots](#suggested-graphics-screenshots)

## Important notes

- This is a **generic** guide for iOS 15-26.2 (tested on iPhone 17 Pro); exact screens may differ slightly on each iPhone model.- You need a PC (Windows or Mac) once to set up SideStore properly; after that you can refresh apps on the phone.
- LiveContainer + SideStore is experimental but widely used to bypass the 3‑app limit and keep everything in one app.

***

## STEP 1 – What you are installing

- **[SideStore](https://sidestore.io)**: An on‑device AltStore‑style installer that lets you sideload IPAs and refresh them over Wi‑Fi using a pairing file and VPN.
- **[LiveContainer (with SideStore inside)](https://github.com/LiveContainer/LiveContainer)**: A container app that runs many IPAs "inside" itself, bypassing the normal 3‑app limit; there is a combined `LiveContainer+SideStore.ipa`.

***

## STEP 2 – One-time PC requirements

Do this once on any Windows or Mac.

1. Install the latest **iTunes** (Windows) or use the built‑in Finder (Mac) so the iPhone is recognised.
2. Download and install **[AltServer](https://altstore.io)** from the official AltStore site.
3. Connect your iPhone by cable, unlock it, and tap **Trust** on both iPhone and PC/Mac if asked.
4. Make sure Wi‑Fi is on and both iPhone and PC/Mac are on the **same network**.

***

## STEP 3 – Install SideStore on the iPhone (via AltServer)

This gives you a normal SideStore app first.

1. On the PC/Mac, download the official **[SideStore.ipa](https://github.com/SideStore/SideStore/releases)** from the SideStore GitHub or website.
2. In the system tray/menu bar, click the **AltServer** icon and choose something like **Install .ipa / Sideload .ipa**, then pick your iPhone and the `SideStore.ipa`.
3. Enter your Apple ID and password when asked (use a burner Apple ID if you prefer).
4. Wait until it says SideStore is installed; the **SideStore** icon will appear on the iPhone Home Screen, but do **not** open it yet.
5. On the iPhone, go to **Settings → General → VPN & Device Management → your Apple ID → Trust** and confirm.

***

## STEP 4 – Enable Developer Mode on iPhone

SideStore and LiveContainer need Developer Mode for JIT‑less and VPN pairing.

1. On iPhone: **Settings → Privacy & Security → Developer Mode**. 
2. Turn Developer Mode **On** and restart the device when iOS asks.

***

## STEP 5 – Create and save the SideStore pairing file

This pairing file lets SideStore refresh apps over Wi‑Fi later without the PC.

1. Open **SideStore** on the iPhone and follow the setup prompt until it tells you to create or import a pairing file.
2. On the PC/Mac, use the SideStore helper/loader (iLoader or similar, depending on the guide you follow) to generate a **pairing file** for your device.
3. Save that pairing file somewhere safe (e.g. iCloud Drive or PC folder) – you may need it again if you reinstall.
4. Import the pairing file into SideStore when asked so SideStore shows your device as **paired** and can refresh apps using its VPN method.

***

### Extra note about iLoader (PC)

If you prefer an all‑in‑one Windows tool instead of AltServer + separate pairing tools, you can use **[iLoader](https://github.com/nab138/iloader)**. It can handle installing LC+SS and managing your SideStore certificate from one place.

- Open **iLoader** on your PC and sign in with the Apple ID you use for SideStore/LC+SS.
- Use the **Certificate** tab to revoke any old SideStore / LC+SS certificates in one click if you hit certificate errors when installing on multiple devices.
- With your iPhone connected, install **LC+SS stable** directly from iLoader, then continue from **STEP 4 – Enable Developer Mode on iPhone** in this guide.

You can repeat the same process with another iOS device using the **same Apple ID and certificate**, so both devices share one LC+SS setup.

***

## STEP 6 – Install LiveContainer + SideStore IPA

You can either use standalone LiveContainer or the combined "LiveContainer+SideStore.ipa". Here the combined version is used.

1. On iPhone, in Safari, go to the **[LiveContainer GitHub releases](https://github.com/LiveContainer/LiveContainer/releases)** page and download **[LiveContainer+SideStore.ipa](https://github.com/LiveContainer/LiveContainer/releases)** (or the latest combined IPA).
2. Open **SideStore** on the iPhone, tap **+ / Add** and choose the downloaded `LiveContainer+SideStore.ipa`.
3. When iOS shows **"App Contains Extensions"**, tap **Keep App Extensions (Use Main Profile)** so it does not consume extra app slots.
4. Wait until SideStore finishes installing; you will see **LiveContainer+SideStore** (or similar name) on the Home Screen.

***

## STEP 7 – First-time setup inside LiveContainer

This step links the internal SideStore to your existing SideStore pairing and certificate, so everything is in one place.

1. Open the **LiveContainer+SideStore** app. 
2. In LiveContainer, tap the **SideStore widget/button** near the `+` in the top‑left to open embedded SideStore.
3. When iOS shows dialogs about network/VPN or certificates, tap **Allow** on both.
4. In the SideStore settings inside LiveContainer, log in with the same Apple ID you used earlier (or import the existing SideStore certificate and pairing file when offered).
5. If you see an option like **"Import Certificate From SideStore"** in LiveContainer settings, use it so LiveContainer reuses the original SideStore signing certificate instead of creating a new one.

***

### LocalDevVPN on iPhone

SideStore now uses **LocalDevVPN** (or similar "local VPN" profiles) for its JIT‑less / VPN refresh method instead of older VPN apps like StosVPN.

Do this once after installing SideStore / LC+SS:

1. On iPhone, open **Settings → General → VPN & Device Management** and make sure the **LocalDevVPN** profile from SideStore is installed and trusted.
2. Open the **LocalDevVPN** app (or the VPN profile SideStore installed), tap **Connect**, and accept the VPN permission dialog so iOS allows SideStore to create a VPN tunnel.
3. When you first open SideStore (inside or outside LiveContainer), allow network / local network discovery permissions if prompted so it can find your device over the local network.

Once LocalDevVPN is connected, SideStore can refresh apps over Wi‑Fi using your pairing file without needing the PC every time.

***

### LocalDevVPN on PC (optional helper)

You do not need a full VPN client on PC, but your PC must be able to talk to the phone over the local network when generating the pairing file or using tools like iLoader.

- Make sure the iPhone and PC are on the **same Wi‑Fi / LAN** and that your firewall allows iTunes/AltServer/iLoader to communicate with the device.
- If you are using iLoader, keep it open while the device is connected so it can talk to the phone, generate the certificate and install LC+SS correctly.

***

## STEP 8 – Enable JIT-less / VPN mode

This is what allows wireless refreshing and multi‑app use.

1. Open embedded **SideStore** inside LiveContainer and go to **Settings**. 
2. Ensure that the **VPN profile** is installed and allowed; iOS will show a standard VPN permission screen – tap **Allow**.
3. Run the **JIT‑less diagnose / test** option (name varies) to confirm everything is configured correctly.

***

## STEP 9 – Adding more LiveContainers (optional)

You can create extra containers if you want separate "profiles" for apps.

1. In **LiveContainer settings**, look for **Install Another LiveContainer**.
2. Tap it, then in the iOS share sheet select **Save to Files** and choose a folder; this saves a new `LiveContainer2.ipa`.
3. Use SideStore again to install this second container if you want separate sets of apps.

***

## STEP 10 – Installing and running IPAs inside LiveContainer

Now any supported iPhone model on iOS 15–18 can run many unsigned apps within LiveContainer with SideStore handling refresh.

1. Download your chosen **.ipa** files to the iPhone (e.g. via Safari → Files app). 
2. Open **LiveContainer**, go to the **Apps** tab, and tap the **+** button.
3. Browse to the IPA file and select it; wait until the install finishes and the app appears in the list.
4. Tap the app in LiveContainer to launch it; LiveContainer will handle execution and JIT‑less mode where supported.

***

## Suggested graphics / screenshots

You can later add real screenshots with image hosting links, but these are suggested placements and captions.

- Under **STEP 3**: 
  "Screenshot: AltServer menu with 'Install .ipa' highlighted and iPhone name selected." 
- Under **STEP 5**: 
  "Screenshot: SideStore pairing file screen showing 'Create Pairing File' button at bottom." 
- Under **STEP 6–7**: 
  "Screenshot: LiveContainer home screen with `+` button and SideStore widget; another screenshot showing certificate import option."

***

## Official Links

- **SideStore Website**: [https://sidestore.io](https://sidestore.io)
- **SideStore GitHub**: [https://github.com/SideStore/SideStore](https://github.com/SideStore/SideStore)
- **LiveContainer GitHub**: [https://github.com/LiveContainer/LiveContainer](https://github.com/LiveContainer/LiveContainer)
- **AltStore Website**: [https://altstore.io](https://altstore.io)


**Created By Dunamis**
