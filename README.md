## GraphForge

GraphForge (also known as DungeonMapDigitizer in our course documentation) is an Android application that turns hand‑drawn dungeon maps into editable digital graphs. Using on‑device image pre‑processing, powered by Google's ML Kit, and a cloud‑hosted large vision–language model (LVLM), it produces a DOT‑formatted graph where rooms become nodes and hallways become edges.

### Features
- **Camera Capture:** Snap a photo of your hand-drawn dungeon map directly in the app. The image is locally pre-proceesed for clarity using **ML Kit**.
- **AI-powered digitization:** A large vision language model (LVLM) converts the processed image into a DOT-format graph. THe initial output identifies rooms as nodes and hallways as edges.
- **Interactive editing:** Viiew the generated graph and fix any mistakes by adding, deleting or reconnecting nodes and edges.
- **Automatic local storage:** Your finalized graph is automatically saved to a local SQLLite database behind the scenes for later retrieval.
- **Vector output:** Graphs are exported as vector data rather than raster images so arbitiarily large graphs do not lose viewing fidelity.
- **Extensible pipeline:** The project uses modular MVVM architecture. YOu can swap out the AI service, adjust the graph formatting or add new export options without rewriting the entire app.

### Requirements
To run GraphForge locally:
1. Clone this repository:
```sh
git clone https://github.com/pepsipotty/GraphForge.git
cd GraphForge
```
2. Open in Android Studio and import the project as a Gradle project. Ensure you have the latest stable Android Studio with the Jetpack Compose toolkit installed.
3. Build and run by choosing an emulator of physical device (recommended) running Android 10 or later and press Run in Android Studio. The app should then compile and install without any additional configuration.
4. Enter your API key through the user interface in the Settings tab accessible from the side navigation bar

### Typical Usage Flow
1. Launch the app and grant camera permission when prompted.
2. Tap **Camera Icon** to take photo of your hand-drawn dungeon. Framing does NOT need to be dead center
3. After snapping the photo, the app will preprocess the image locally using ML Kit and send it to the LVLM for digitization. This may take a few seconds depending on network latency. Typically 2-3 seconds
4. Once the graph is shown, inspect nodes and edges. If the model made a mistake (commonly seen by merging rooms incorrectly), use our built in editing tools to add, delete, rename or reconnect elements. Changes will be applied instantly thanks to Compose's state management.

### Credits
This app was created by a team of students during the Summer 2024 offering of CSE 5236 - Mobile App Development at the Ohio State University. Thanks to Scott Salisbury and Eric Middlekamp for their invaluable collaboration and of course Dr. Adam Champion for his guidance. The project uses open-source libraries including but not limited to **JGraphT**, **Room**, **Coil**, **OkHttp**, **ML Kit**, and **Lottie**

