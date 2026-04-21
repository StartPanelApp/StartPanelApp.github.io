<div align="center">
  <img width="1200" alt="StartPanel Screenshot" src="img/StartPanelScreenshot.jpg">
</div>

# StartPanelApp
<i>- A personal start page for your everyday tools, with optional Homey Pro integration</i>  

StartPanel is a **customizable browser start page and dashboard**, built with TypeScript and Vite.
It lets you collect links, widgets, and **Homey Pro controls** in one place – running entirely in the browser with no backend or database required.
All settings and layout data are stored **locally in your browser**, giving you full control of your configuration.

## Key features

- Customizable **start page with links and widgets**
- Multiple tabs (for work, home, or anything you want)
- Runs directly from **GitHub Pages** or can be hosted locally

### Homey integration (optional)
- **Homey dashboard** with live capability updates via Homey Cloud (or local polling)
- Flexible layouts including **column layout or free placement**
- Support for **background images / floorplan dashboards**
- Use multiple tabs (for example per room, floor, or function)
- Built in easy to use Homey Pro widgets
- Installable as a **Progressive Web App (PWA)** for tablet or kiosk setups

## Run it directly in your browser

Just go to:  
https://startpanelapp.github.io/  

> **Note:** This is *not* an official Homey app. It is a personal project that I originally built for my own use.

For common questions, see the [**FAQ section further down**](#-faq-frequently-asked-questions) on this page.

---

## Homey Pro Integration

To use StartPanel with **Homey Pro**, you can connect through the **Homey Cloud**, run the app locally on a NAS, or simply use **webhooks**.  
Depending on how you run the app, you can view device status and control devices directly from the page.

---

# ⭐ How to Use StartPanelApp

## 1. Run directly from GitHub Pages (easiest)

Simply open:

👉 **https://startpanelapp.github.io/**

This is the easiest way to use StartPanelApp.

### Connecting to Homey

Requirements:

- A **Homey Pro 2023 or newer**
- Your **Homey ID**
- A **Homey API Key**

The connection is made through **Homey Cloud**, which provides **live updates**.

Alternatively, you can use **webhooks only**, which requires no authentication but provides limited functionality.  
(Webhooks also work with older Homey models.)

### Finding your Homey ID

Go to:
Settings → General → Cloud → Homey Cloud  
Copy the **Homey ID** and paste it into:  
StartPanel → **Settings → Homey → Homey ID**  

### Creating an API Key

Go to:  
Settings → API Keys  
Create a **new API key** and give it the required permissions  
(at minimum **Devices, Flows, and Variables**).  

Copy the key and paste it into:  
StartPanel → **Settings → Homey → API Key / Bearer Token**  

---

## 2. Install as an App (PWA)

This web app can be installed on Android using **Google Chrome** as a **Progressive Web App (PWA)**.

This provides a cleaner interface without the browser address bar and works perfectly for **tablet dashboards or kiosk setups**.

Steps may vary depending on device and Android version.

### Installation

1. Open the web app in **Google Chrome**
2. Tap **⋮ (three dots)** in the top-right corner
3. Select **Add to Home screen** or **Install App**
4. Confirm by tapping **Install**

The app will now appear among your other apps and can be launched like a normal application.

### Updates

The app updates automatically whenever a new version is published on GitHub.  
No manual reinstallation is required.

---

### 🔒 Optional: Enable Kiosk / Screen Pinning Mode on Android

This is perfect for a **dedicated Homey control panel** on a wall-mounted tablet.

Steps (may vary between Android devices):

1. Go to **Settings → Security**
2. Enable **Screen Pinning**
3. Open the StartPanel app
4. Tap the **Recent Apps** button
5. Tap the **pin icon**

The user can now not leave the app without entering the device PIN.

(Some Android devices may not support this feature.)

---

## See the **FAQ section further down** for additional help and tips.

---

## Advanced Usage

If you want to avoid cloud services or GitHub dependencies, you can run StartPanel locally on a NAS such as:

- Asustor
- Synology
- QNAP

When running locally, the system uses **polling instead of live updates**, meaning device updates occur with a small delay based on the selected polling interval.

⭐ Do I need to be on the same network as Homey?  

**Yes** – if you connect locally using polling.

**Exception:** If you use **VPN**, everything works normally because the connection behaves as if you were on the same local network.

**No** – if you connect through **Homey Cloud**, which works regardless of where the web page itself is hosted.

---

# Running StartPanel on a NAS (Apache, Nginx, Asustor, Synology, QNAP)

### 0. Make sure a web server is enabled on your NAS

If you do not already have a web server installed, see the instructions further below.

---

### 1. Open the project GitHub page

https://github.com/StartPanelApp/StartPanelApp.github.io

---

### 2. Download the required files

You only need:

- `index.html`
- the entire `/assets` folder

(The folder contains all JavaScript, CSS, and image files.)

---

### 3. Upload the files to your NAS web directory

Log into your NAS and open the web server (Apache, Nginx, etc.).

Most NAS systems have a folder called something like: “web”, “www” or similar.

Copy **index.html** and the entire **/assets** folder into that directory.

Important:

- `index.html` **must keep its name**
- `/assets` must be located in the **same folder**

Example structure:
```
/web
├── index.html
└── assets/
   └── (all JS/CSS/bilder)
```

### 4. Open the page in your browser

Go to for exempel:  
http://tour-nas-ip-address/

Or if you placed it in a subfolder, for example StartPanel:  
http://your-nas-ip-address/StartPanel/

---

### 5. The page should now load directly from your NAS.

---

### 6. Using Homey locally

To control devices and read status locally:

- You must be on the **same network as your Homey Pro**
- Or use **VPN**

Alternatively, you can still connect via **Homey Cloud**.

---

### 7. Local settings storage

All settings and links are stored in **LocalStorage**.

This means settings are unique for each **browser and device**.

However, you can create a **backup file** and restore it on another browser or device.

---

### 8. Webhooks

Webhooks work even when you are **not on the same network** as Homey.

However, reading device status requires the page to run:

- on the same network
- or through VPN.

---

# Installing a Web Server on Your NAS

Most NAS systems can run a simple web server capable of hosting static websites (HTML, CSS, JavaScript).  
That is all StartPanel requires.

---

### 1. Log in to your NAS admin interface

Open your NAS control panel in a browser, for example:  
http://your-nas-ip:5000  
(or another port depending on your NAS model)

---

### 2. Open the App / Package Center

Search for something like:
```
“Web Server”
“Apache”
“Nginx”
“Web Station”
“Hosting”
“WWW Server”
```
---

### 3. Install the web server

Install it with **default settings**.

Some NAS systems may also install:

- PHP
- MySQL

These are **not required** for StartPanel and can be ignored.

After installation, a web directory will be created, usually named something like:
```
/web
/www
/var/www
/home/www
/WebServer
/volume1/web (Synology)
```
This folder is what the web server serves when visiting your NAS IP address.

---

### 4. Restart the web server

Restart the service via the NAS control panel.

---

### 5. Done!

Your NAS is now running a web server, and you can proceed with the earlier instructions to install StartPanel.

💡 Tip:  
If you want to access the dashboard outside your home network, consider using **VPN**.

---

# 📌 FAQ (Frequently Asked Questions)

## ❓ How do I sync the dashboard between multiple devices?

The dashboard is stored locally in your browser using **LocalStorage** and you can either sync / copy it manually by following the steps below:

Steps:

1. Go to **Settings → Backup & Restore**
2. Click **Export Data** to download the JSON file
3. Move the file to another device (for example an iPad)
4. On the other device: **Settings → Backup & Restore → Import Data**

Done ✔
**NOTE!** Keep in mind that the layout is NOT dynamic, and may not fit a different type of device with a smaller / larger screen, or a different orientation.

Make sure to **create manual backups regularly**.  
Store the backup file safely since it is **not encrypted**.

OR

You can use the Cloud Sync. feature, see below.

---
 
## ❓ Can the dashboard sync automatically between devices?

Yes. (But there are some things you have to keep in mind, see below at Cloud Sync.)

Cloud Sync lets you keep your dashboard in sync across multiple devices by storing your configuration in the cloud.

### ⚙️ Setup in StartPanel

1. Go to **Settings → Cloud Sync**
2. Select a **Cloud Provider**
3. Enter your credentials (see setup guides below)
4. Click **Test Connection**
5. If it shows ✅ OK:
   - Enable **"Cloud Sync"**
   - Choose your preferred sync interval


---

<a id="cloud-sync"></a>
## ❓ Cloud Sync

### How does it work - and what do you need to consider?

- Your settings are automatically uploaded when:
  - You make changes (edit widgets, layout, etc.)
  - A scheduled sync runs
- The latest version is downloaded when:
  - You open the app
  - You manually refresh the page
  - Background sync triggers

### ⚠️ Important

- Sync is **not real-time**
- If two devices edit at the same time:
  → the **last saved version wins**
- This is intentional to avoid API limits on free plans

---

## 📦 Data Limits (Important!)

Cloud providers have strict size limits:

- **GitHub Gist** → ~1 MB  
- **jsonbin.io (free)** → ~100 KB  

### 🚫 Avoid using images

Images (especially base64) can quickly exceed these limits.

👉 Recommendation:
- Avoid storing images in your dashboard
- Use external image URLs instead

---

## 🔄 API Limits & Pending Requests

Each sync and each edit creates API requests.

- Frequent sync intervals = more requests
- Free tiers allow many requests, but not unlimited

👉 Recommendation:
- Use a reasonable sync interval (e.g. 30 minutes or more)

---

## 🧠 Layout Considerations

StartPanel uses a **fixed column layout**, not responsive auto-layout.

This means:

- Layout is based on your column setup
- Different screen sizes (desktop vs mobile) may look different!

👉 Recommendation:
- Test your layout on multiple devices

---

## Is the json file encrypted on the cloud service

Yes, on the cloud service it is encrypted. But not when you save it locally. Read more about that in a later chapter below.

---

# 🔧 Cloud Provider Setup

You have two cloud service provider to choose between. And that is GitHub gist and jsonbin.io.

---

## ☁️ GitHub Gist Setup

1. Go to https://github.com  
   → Sign up / Log in

2. Go to https://github.com/settings/tokens  
   → Generate new token (**classic**)

   - Expiration: optional  
   - Scope: ✅ `gist`

3. Copy the token  
   → Paste into StartPanel

---

4. Go to https://gist.github.com  
   → Create a **Secret Gist**

   - Description: `StartPanelSync`  
   - Filename: `startpanel_backup.json`  
   - Content:
     ```json
     {}
     ```

5. Click **Create secret gist**

6. Copy the **Gist ID** from the URL  
   → Paste into StartPanel

---

## ☁️ jsonbin.io Setup

1. Go to https://jsonbin.io  
   → Sign up / Log in

2. Go to **API Keys**  
   → Copy your **X-MASTER-KEY**  
   → Paste into StartPanel

3. Go to **Bins**  
   → Create a new Bin

   Content:
   ```json
   {
     "users": []
   }

4. Save the Bin

5. Copy the BIN ID
→ Paste into StartPanel

---

## ⚠️ Cloud Sync – Important Notes & Recommendations

### 🔸 Widget Expand / Collapse State

The expanded/collapsed state of widgets is **not synced**.

- This state is stored **locally in each browser**
- A widget can be expanded on one device and collapsed on another

👉 This is intentional to reduce unnecessary sync traffic and API usage.

---

### ❓ Why can't I sync to a local file on my NAS?

Cloud Sync requires a **public API endpoint** that your browser can access directly.

A local file on your NAS:
- is not accessible via a standard cloud API
- cannot handle authentication or remote updates in the same way

👉 Therefore, Cloud Sync only works with supported cloud providers (e.g. GitHub Gist, jsonbin.io)

---

### 🖼 Image Storage Recommendation

To avoid large sync files:

👉 Store images externally instead of inside your dashboard data.

Recommended options:
- OneDrive
- Google Drive (public/shared links)
- Other image hosting services

Then link to the image in StartPanel.

✔ Prevents hitting size limits  
✔ Keeps your JSON small and fast  

---

## 💾 Local Backup vs ☁️ Cloud Sync

### 💾 Local Backup – Pros
- No size limitations (images work fine)
- Full control of your data
- No dependency on external services
- Works completely offline

### 💾 Local Backup – Cons
- Not encrypted
- Manual handling required (export/import)

---

### ☁️ Cloud Sync – Pros
- Easy multi-device sync
- Automatic updates
- No manual file handling

### ☁️ Cloud Sync – Cons
- Limited storage (depending on provider)
- API rate limits may apply
- Dependent on third-party services
- Not real-time sync
- Risk of overwriting changes ("last write wins")

---

## ⭐ Recommendation

👉 **Always keep a local backup!**

Cloud Sync is convenient, but a local backup ensures you never lose your data.

## ❓ Does the local backup file contain sensitive information? (e.g. Homey tokens)

Yes, the backup file may contain:

- your dashboard layout
- widget configurations
- authentication tokens (for example Homey PAT)

This is not a security issue per se, but the file should be treated as a **personal configuration file** as the data is not encrypted when saved locally!

Recommendations:

- store it in a safe location
- avoid sending it unencrypted
- do not share it unless you want to share your setup

---
 
## ❓ Do I need to run it locally on a NAS?

No.

However, running locally can be useful if you want to access **local network resources**, such as images from IP cameras.

---

## ❓ Does it only work with Homey Pro 2023 and newer?

Yes, for full functionality (reading device status and controlling devices) when using **Cloud or polling**.

Using **webhooks only** may work with older Homey models.

Full functionality requires an **API token / PAT**, which is available on **Homey Pro 2023 and newer**.

---

## ❓ Can I view live video from IP cameras?

Yes, there are some ways to try, but there are sveral conditions that must be met.  

**Option 1 (Recommended): MJPEG stream (simplest)**

If your camera supports MJPEG, this is the easiest method.

Use the "Video (MJPEG)" widget and enter the camera stream URL.

Example (Foscam):

http://192.168.1.34:88/cgi-bin/CGIStream.cgi?cmd=GetMJStream&usr=admin&pwd=12345

Requirements and limitations:

- StartPanel must run locally (for example on a NAS or local web server)
- The stream must be accessed over HTTP (not HTTPS) to avoid browser security issues
- The camera must support MJPEG streaming
- ⚠️ MJPEG streams do not include audio

This method requires minimal setup and works directly in the browser.

**Option 2: RTSP via go2rtc (more advanced)**

1. The camera must provide an **RTSP stream**
2. StartPanel must run locally on a **web server** (for example on a NAS)
3. **go2rtc** must run on the NAS using **Docker**
4. The RTSP stream must be **H.264** (not H.265)
5. The video can normally only be viewed on the **same network** or via **VPN**
6. Use the **Iframe widget** with the go2rtc stream URL, for example:
http://192.168.1.3:1984/stream.html?src=kamera1

go2rtc acts as a **bridge**, converting the RTSP stream into a format that browsers can play.

It works well but requires some setup.

**🧠 Simple explanation:**  
MJPEG = easiest, but basic (no sound, higher bandwidth)  
RTSP via go2rtc = more setup, but better quality and supports audio  

**💡 When to choose what**

👉 Choose MJPEG if:  
- you want something that just works
- you don’t need audio
- you don’t want to install anything extra

👉 Choose go2rtc if:   
- you want better video quality
- you need audio
- you’re OK with a bit more setup

<div align=left><img width="350" alt="CCTV example" src="img/StartPanelApp - CCTV image.png" /></div>

---

## ❓ Can I show still images from IP cameras?

Possibly.

If the app runs locally on a NAS web server, the **Image widget** may be able to fetch camera snapshots.

Each manufacturer uses different URLs, and not all cameras support this feature.

Example (Foscam V5P):  
https://192.168.1.X/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=NAME&pwd=PASSWORD  

Insert the URL into the **Image widget** and set a refresh interval (for example **60 seconds**).

Note that browser security restrictions may sometimes block such requests.

---

<div align="left">
  <img width="900" alt="StartPanel Screenshot" src="img/StartPanel - Demo Layout.jpg">
</div>

## ❓ What is the Homey Layout feature?

The Layout feature lets you place Homey device capabilities freely on top of a background image.  
This makes it possible to create visual dashboards such as:

- a house floor plan
- a room layout
- a technical overview
- or any custom graphic or picture you want to use

The background image is created in another program (for example a drawing tool or floor-plan editor) and then imported into StartPanel. After that you can place capabilities anywhere on the screen.  

If you want to design a floor-plan image, there are several free alternatives you can use.  
Here are some tools to help you create one:

### Online Tools
- [Floorplan Creator](https://floorplancreator.net/)
- [RoomSketcher](https://www.roomsketcher.se/)
- [RemPlanner](https://remplanner.com/)

### Install (Desktop)
- [Sweet Home 3D](https://www.sweethome3d.com/)
- [FreeCAD](https://www.freecad.org/)


Examples of what you can display and control:

- Turn lights on/off
- Adjust dimmer levels
- See if doors or windows are open
- View temperature or humidity
- Monitor power consumption
- Display sensor values
- Display variables

This allows you to build an intuitive and visual dashboard where your smart home devices are positioned exactly where they belong. And this will get you an fast and easy way to see whats on and off and so on.

### To create a Layout dashboard tab:  
Go to Settings > Dashboards  
Click "Add Homey Layout"  

---

## ❓ Why do some link icons sometimes show only a letter?

This behavior is caused by factors outside the app's control:

**Icon service caching**  
Icon providers use their own cache. If they fail to fetch an icon once, they may remember the failure for a while.

**Temporary service outages**  
Icon services may be temporarily unavailable or overloaded.

**Websites blocking icon scraping**  
Some websites block automated services that try to fetch their icons.

**Browser cache**  
Your browser may cache a broken image or failed request.

In many cases the icon appears again automatically later.

---

## ❓ Can I create multiple dashboards?

Yes.

Go to **Settings → Dashboards**.

There you can:

- create additional dashboards
- edit existing ones
- choose whether they appear as **tabs** or in a **dropdown menu**

---

## ❓ Why are old versions kept in the `/assets` folder?

If a new version causes problems, you can revert to a previous version by editing **index.html** and pointing it to an older `.js` file in `/assets`.

You can see which file belongs to which version on GitHub under:  
/docs/assets

---

## ❓ Is this an official Homey app?

No.

---

## ❓ Will updates erase my data?

Normally **no**.

The dashboard configuration is stored in **LocalStorage**, which is not affected by normal code updates.

However, data could be lost if:

- the browser clears storage
- the storage schema changes
- major version upgrades occur
- browser extensions interfere
- the environment changes (for example moving to a new NAS)

For this reason, **regular backups are strongly recommended**.

---

## ❓ Is the app free?

Yes.

Occasionally a small **donation banner** may appear encouraging support for a **cat shelter**.  
This is completely optional.

---

## ❓ Does the dashboard update in real time?

**Yes** when connected through **Homey Cloud**.

**No** when running locally using **polling**.

Polling means the app checks Homey for updates at a set interval, for example:

- every 10 seconds
- every 20 seconds
- every 30 seconds

You can configure this under:

**Settings → Homey → Polling Interval**

---

## ❓ Do I need a Homey to use this app?

No.

You can use StartPanel purely as a **start page with widgets**.  
Homey integration is simply an optional feature.

---


## ❓ Can I add road / traffic cameras to the dashboard?

Example for **Sweden (Trafikverket / Trafiken.nu)**

<div align=left><img width="350" alt="Traffic camera example" src="img/startPanelApp - Vagkamera.jpg" /></div>

You can add traffic cameras as automatically refreshing **still images**.

### 🌍 Where do the cameras come from?

Examples:

- Trafiken.nu (Stockholm, Gothenburg, etc.)
- Trafikverket (nationwide Sweden)

Images typically update **about once per minute**.

### 🧩 How do I find the image URL?

The image URLs are not publicly listed, but you can find them like this:

1. Open the camera page in Chrome or Firefox
2. Press **F12** to open Developer Tools
3. Go to the **Network** tab
4. Wait for the camera image to refresh
5. Look for a file ending in **.jpg**
6. Right-click → **Copy URL**

That is the direct image URL.

### 🖼 Add it to StartPanel

1. Add the **Image widget**
2. Paste the image URL
3. Set a refresh interval (for example **60 seconds**)

Done ✔

---

## ❓ Why can't I link to local HTML files or apps on my device?

Browsers block links that attempt to open local files or launch apps directly for **security reasons**.

This prevents links such as:  
file://  
C:\…   
app://   
or local .html-files. 

This is a standard browser security feature designed to protect users.

---

Visit **https://startpanelapp.github.io/** to try the app live.


