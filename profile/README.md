<a href="https://chalkdraw.io"><img src="https://www.chalkdraw.io/og.jpg" alt="chalkdraw on the Mac: a cloud architecture diagram drawn by hand, with three whiteboards open as tabs" width="100%"></a>

**chalkdraw** is a whiteboard for the Mac with the look of a napkin sketch and the manners of a native app: sketchy lines, a hand-written font and marker colours, with the tools of a real editor. The iPad comes next.

It is written in Swift and SwiftUI on its own Core Graphics engine, with no web view anywhere, and it speaks Excalidraw's file format, so a drawing moves between the two without losing anything.

[chalkdraw.io](https://chalkdraw.io) · [@chalkdraw on X](https://x.com/chalkdraw) · [hello@chalkdraw.io](mailto:hello@chalkdraw.io) · Coming soon on the Mac App Store

### What it does

- **Draws like on paper.** Rectangles, diamonds, ellipses, arrows, free-hand strokes and text, all in the same sketchy hand. Arrows stick to the shapes they point at and follow them around.
- **Turns text into diagrams.** Paste a Mermaid flowchart or sequence diagram and it lands as shapes and arrows you can move. Paste JSON and it opens up as connected cards, key by key.
- **Gets along with Excalidraw.** `.excalidraw` files open as they are, properties chalkdraw doesn't know survive a save, and a shape copied here pastes into excalidraw.com and back.
- **Lives in the cloud from the first stroke.** Every element syncs on its own and conflicts settle by Excalidraw's own rules, so two people can draw on the same whiteboard at once.
- **Shares and comments.** Invite people by mail or by a link, and pin comments right on the drawing.

### Under the hood

The sketchy look comes from rough.js seeding a random generator with each element's `seed`. A renderer that only imitates it draws every imported diagram with a different hand. So chalkdraw's renderer is a line-by-line Swift port of [rough.js](https://github.com/rough-stuff/rough) and [perfect-freehand](https://github.com/steveruizok/perfect-freehand), and CI checks it against output captured from the real libraries: straight lines match coordinate for coordinate, and curves to within `1e-9`.

The app is Swift 6, SwiftUI and Core Graphics. The cloud is Firebase, with its Functions in TypeScript. The site is Preact and Vite, prerendered to static HTML.

<sub>Made in Brazil by [Geovani Amaral](https://github.com/iamageo).
