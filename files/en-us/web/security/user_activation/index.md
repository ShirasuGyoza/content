---
title: Features gated by user activation
slug: Web/Security/User_activation
---

To ensure applications are unable to abuse APIs that can create bad user experience when the behavior is not desired, some APIs can only be used when the user is in an "active interaction" state, meaning the user is currently interacting with the web page, or has interacted with the page at least once. Browsers limit access to sensitive APIs like popups, fullscreen, or vibration APIs to active user interactions to prevent malicious scripts from abusing these features. This page lists web platform features available only after user activation.

A user activation either implies that the user is currently interacting with the page, or has completed an interaction since page load. Typically, this is a click on a button or some other user interaction with the UI.

More precisely, an _activation triggering input event_ is an event which:

- has the [`isTrusted`](/en-US/docs/Web/API/Event/isTrusted) attribute set to `true`, and
- is an event of the following types:
  - [`keydown`](/en-US/docs/Web/API/Element/keydown_event) (except for the <kbd>Esc</kbd> key nor a shortcut key reserved by the user agent)
  - [`mousedown`](/en-US/docs/Web/API/Element/mousedown_event)
  - [`pointerdown`](/en-US/docs/Web/API/Element/pointerdown_event) (if `pointerType` is "mouse")
  - [`pointerup`](/en-US/docs/Web/API/Element/pointerup_event) (if `pointerType` is not "mouse")
  - [`touchend`](/en-US/docs/Web/API/Element/touchend_event)

If an activation has been triggered, the user agent differentiates between two types of user activation window states: sticky and transient.

## Transient activation

{{Glossary("Transient activation")}} is a window state that indicates a user has recently pressed a button, moved a mouse, used a menu, or performed some other user interaction. Transient activation expires after a timeout (if not renewed by further interaction) and may also be consumed by some APIs (like {{domxref("Window.open()")}}).

Example APIs that require transient activation:

- [`beforeunload` event](/en-US/docs/Web/API/Window/beforeunload_event)
- {{domxref("Clipboard.read()")}}
- {{domxref("Clipboard.readText()")}}
- {{domxref("Clipboard.writeText()")}}
- {{domxref("Document.requestStorageAccess()")}}
- {{domxref("Element.requestFullScreen()")}}
- {{domxref("Element.requestPointerLock()")}}
- `GPUAdapter.requestAdapterInfo()`
- {{domxref("HID.requestDevice()")}}
- {{domxref("HTMLInputElement.showPicker()")}}
- {{domxref("HTMLVideoElement.requestPictureInPicture()")}}
- {{domxref("IdleDetector.requestPermission()")}}
- {{domxref("MediaDevices.selectAudioOutput()")}}
- `MediaStreamTrack.sendCaptureAction()`
- `MediaDevices.getViewportMedia()`
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("Navigator.share()")}}
- {{domxref("PaymentRequest.show()")}}
- {{domxref("PresentationRequest.start()")}}
- {{domxref("RemotePlayback.prompt()")}}
- {{domxref("USB.requestDevice()")}}
- {{domxref("Keyboard.lock()")}}
- {{domxref("Window.open()")}}
- {{domxref("Window.showOpenFilePicker()")}}
- {{domxref("Window.showSaveFilePicker()")}}
- {{domxref("Window.showDirectoryPicker()")}}
- `Window.getScreenDetails()`
- `Window.queryLocalFonts()`
- {{domxref("XRSystem.requestSession()")}}

## Sticky activation

{{Glossary("Sticky activation")}} is a window state that indicates a user has pressed a button, moved a mouse, used a menu, or performed some other user interaction. It is not reset after it has been set initially (unlike transient activation).

Examples APIs that require sticky activation:

- {{domxref("Navigator.vibrate()")}}
- `navigator.getAutoplayPolicy()`
- `navigator.virtualKeyboard.show()`

## See also

- {{Glossary("Transient activation")}}
- {{Glossary("Sticky activation")}}
- [Features restricted to secure contexts](/en-US/docs/Web/Security/Secure_Contexts/features_restricted_to_secure_contexts)

{{QuickLinksWithSubpages("/en-US/docs/Web/Security")}}
