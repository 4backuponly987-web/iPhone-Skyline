# SKYLINE — iPhone / GitHub Pages build

This repo is ready to host as a GitHub Pages site. The game remains desktop-compatible, but on touch-first phones it switches to the dedicated iPhone flight controls.

## iPhone controls

- **Left thumb vertical pad:** up = dive, down = pull up / flare.
- **Tilt iPhone left/right:** bank and steer. The first launch asks for motion permission and calibrates the current phone angle as neutral.
- **Tuck:** hold while the wings are out. If the wings are stowed, tapping the same button deploys them.
- **Barrel Roll:** rolls in the current tilt direction; near neutral it uses the last steering direction.
- **Parachute:** top-left. It only deploys the canopy; it does not act as a cut-away button.
- **Pause:** top-right. The pause menu also contains tilt calibration, sensitivity and reverse-steering controls.
- **Tight carve:** while flying, touch and hold any empty part of the screen while tilting. This mirrors the desktop left-click hard-turn control. Release to return to normal steering. Touches on actual buttons, sliders and menus are ignored.

The mobile build deliberately removes other trick inputs, inverted flight and respawn-point controls. Free Fly uses an airborne hot start because the mobile layout intentionally has no jump/step-off button. Races already begin airborne.

## Put it on GitHub Pages

1. Create a new GitHub repository.
2. Upload **all files and the `icons` folder** from this repo to the repository root.
3. In GitHub open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose `main` and `/ (root)`, then save.
6. Open the GitHub Pages HTTPS address in Safari on the iPhone.
7. Tap **Share → Add to Home Screen** and enable **Open as Web App** if Safari shows that option.
8. Open SKYLINE from the Home Screen, press **Enable tilt + calibrate**, and allow motion access.

## Offline use

`service-worker.js` caches the complete game, mobile controls, manifest and icons. After the Pages site has loaded successfully online once and the service worker has installed, the Home Screen app can launch with no connection / in Airplane Mode.

If you publish a new build later, update the `CACHE` name in `service-worker.js` (for example `skyline-iphone-v3`) so existing installations refresh cleanly.

## Important

Motion sensors are only exposed in a secure context. GitHub Pages uses HTTPS, so the deployed version meets that requirement. Opening `index.html` directly from the iPhone Files app is **not** equivalent to the GitHub Pages version and will not provide the full PWA/offline install behavior.


## Mobile control tuning

Open **Pause** while flying to adjust **Tilt sensitivity** and **Left-thumb sensitivity** independently. Both settings are saved locally on the iPhone. You can also recalibrate the neutral tilt angle or reverse the tilt direction if you deliberately prefer the opposite mapping.
