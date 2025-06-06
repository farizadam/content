---
title: "MediaRecorder: stop event"
short-title: stop
slug: Web/API/MediaRecorder/stop_event
page-type: web-api-event
browser-compat: api.MediaRecorder.stop_event
---

{{APIRef("MediaStream Recording")}}

The **`stop`** event of the {{domxref("MediaRecorder")}} interface is fired when
{{domxref("MediaRecorder.stop()")}} is called, or when the media stream being
captured ends. In each case, the `stop` event is preceded by a
`dataavailable` event, making the {{domxref("Blob")}} captured up to that
point available for you to use in your application.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js-nolint
addEventListener("stop", (event) => { })

onstop = (event) => { }
```

## Event type

A generic {{domxref("Event")}}.

## Example

```js
mediaRecorder.onstop = (e) => {
  console.log("data available after MediaRecorder.stop() called.");

  const audio = document.createElement("audio");
  audio.controls = true;
  const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
  const audioURL = window.URL.createObjectURL(blob);
  audio.src = audioURL;
  console.log("recorder stopped");
};

mediaRecorder.ondataavailable = (e) => {
  chunks.push(e.data);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): MediaRecorder +
  getUserMedia + Web Audio API visualization demo, by [Chris Mills](https://github.com/chrisdavidmills) ([source on GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [simpl.info MediaStream Recording demo](https://simpl.info/mediarecorder/), by [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}
