# The State of Autoplay on the Web

## TL;DR

Playback of any media that includes audio is generally blocked if the playback is programmatically initiated in a tab which has not yet had any user interaction. Browsers may additionally choose to block under other circumstances.

## Best Practices
* Don't ever assume a video will play, and don't show a pause button when the video is not actually playing.
* Use the promise returned by `HTMLMedia​Element​.play()` to check if the play attempt succeeded or failed.
* Always show media controls so that users can unmute or start the video even if it didn't autoplay.
* Use feature policies to delegate autoplay permission to iframes.

> [https://developer.mozilla.org/en-US/docs/Web/Media/Autoplay_guide](https://developer.mozilla.org/en-US/docs/Web/Media/Autoplay_guide)
>
> [https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/play#Usage_notes](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/play#Usage_notes)

## Chrome
*From version 66 (released on 4/17/2018)*

🙊 **Muted autoplay** is always allowed. 

📣 **Autoplay with sound** is allowed if:

* the user has interacted with the domain (click, tap, etc.) or
* the user's Media Engagement Index threshold has been crossed, meaning they previously played video with sound (desktop)
* the user has added the site to their home screen (mobile).

🚓 Top frames can delegate autoplay permission to their iframes to allow autoplay with sound. Autoplay is allowed by default on same-origin iframes.

> [https://developers.google.com/web/updates/2017/09/autoplay-policy-changes](https://developers.google.com/web/updates/2017/09/autoplay-policy-changes)

## Firefox
*From version 66 (released on 3/19/2019)*

🙊 **Muted autoplay** is always allowed.

📣 **Autoplay with sound** is only allowed if the user has interacted with the domain (click, tap, etc.).

🚓 Sites can autoplay audibly if the user has previously granted them camera/microphone permission.

👩‍💻 Users can enable autoplay with sound on a per-site basis.

> [https://hacks.mozilla.org/2019/02/firefox-66-to-block-automatically-playing-audible-video-and-audio/](https://hacks.mozilla.org/2019/02/firefox-66-to-block-automatically-playing-audible-video-and-audio/)

## Safari
*From iOS9 (released on 9/16/2015) and macOS High Sierra (released on 9/19/2017)*

🙊 **Muted autoplay** is allowed. However, elements will only begin playing when visible on-screen such as when they are scrolled into the viewport, made visible through CSS, and inserted into the DOM.

📣 **Autoplay with sound** is only allowed if the user has interacted with the domain (click, tap, etc.).

🚓 Videos are prevented from auto-playing when either hidden in a background tab or otherwise off-screen.

👩‍💻 Users have the ability to turn off all forms of auto-play, including silent videos.

> [https://webkit.org/blog/6784/new-video-policies-for-ios/](https://webkit.org/blog/6784/new-video-policies-for-ios/)
>
> [https://webkit.org/blog/7734/auto-play-policy-changes-for-macos/](https://webkit.org/blog/7734/auto-play-policy-changes-for-macos/)

## Edge

📣 **Autoplay with and without sound** is allowed by default.

🚓 Autoplay of media in background tabs is automatically suppressed. Iframes inherit the autoplay permission from the parent page regardless of content origin.

👩‍💻 Users can customize media behavior with both global and per-site autoplay controls. 

> [https://docs.microsoft.com/en-us/microsoft-edge/dev-guide/browser-features/autoplay-policies](https://docs.microsoft.com/en-us/microsoft-edge/dev-guide/browser-features/autoplay-policies)
