# GestureHalo

Gesture recognition from a phone's accelerometer. A small model trained in Edge Impulse (spectral features + neural network) runs in the browser as WebAssembly. Classes: idle, wave, circle.

## Status
Work in progress. The web app is built; the trained model files are added after the final training run. Until `public/model/` holds the exported files, the page shows the live sensor graph only.

## Results
[Fill in only from a fresh test set recorded after the last training run: accuracy, confusion matrix, number of recordings.]
Small personal dataset: one person, one phone. Not tested on other people or devices.

## How it works
Phone accelerometer (62.5 Hz, includes gravity) -> 2-second windows (125 samples x 3 axes) every 200 ms -> spectral features -> small neural network -> idle / wave / circle (below 60% confidence shows "uncertain").

## Run it
1. Copy `edge-impulse-standalone.js` and `edge-impulse-standalone.wasm` from the Edge Impulse WebAssembly export into `public/model/`.
2. Deploy over HTTPS (motion sensors are blocked on plain HTTP): `firebase deploy --only hosting`, or `firebase hosting:channel:deploy preview` for a test URL.
3. Open the URL on your phone and tap Start Sensors.
