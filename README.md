# Expo Linking.addEventListener Inconsistency

This repository demonstrates a bug encountered when using the Expo `Linking` API to handle deep links. In certain scenarios (cold start, app termination), the `Linking.addEventListener` fails to trigger, leaving the app unable to process deep links. The primary challenge is the absence of explicit error messages; the app silently ignores the incoming link.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on a physical device or emulator.
4. Close the app completely.
5. Open a deep link (e.g., `exp://your-expo-app-id.expo.io`).
6. Observe that the app doesn't handle the link as expected.

## Solution

The provided solution addresses the unreliability by employing a more robust approach to deep link handling. It involves a combination of techniques to ensure the event listener is active and properly handles the cases where the deep link might have been received before the listener was ready.

This bug is likely related to the asynchronous nature of the `Linking` API and how the event listener interacts with the app's lifecycle events.