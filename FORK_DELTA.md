# Fork delta

This fork stays close to [`quickdrawjs/quickdraw`](https://github.com/quickdrawjs/quickdraw)
and preserves its MIT license unchanged.

The published `@quickdrawjs/core` package includes the same unchanged MIT
license notice so the release artifact remains self-contained.

## Base

- Upstream base: `quickdrawjs/quickdraw@81a40da3647590e210b778c12288c7d0394ea2a7`
- Fork release line: `host-camera-v0.2.0-*`

## Maintained delta

The core `Editor` has one small, host-agnostic embedding seam:

- `cameraInput: false` leaves camera ownership to the host by disabling
  Quickdraw's wheel, pinch, hand/middle-button/space-drag, and keyboard camera
  input.
- `setExternalCamera(camera)` cancels deferred fits, camera animation, fit
  easing, and queued rendering; it then adopts the supplied camera and renders
  synchronously.
- `renderBackground: false` keeps the on-screen drawing canvas transparent
  while retaining the normal Quickdraw selection and interaction overlay.

The defaults preserve upstream behavior. No host-specific UI, persistence, or
product behavior lives in this repository.

## Merge discipline

Keep the delta confined to the editor implementation, its public declarations,
core documentation, and focused editor tests. To refresh from upstream, merge
or rebase the upstream branch, run `npm test`, `npm run typecheck`, and
`npm run build`, then inspect the range from the upstream base to the current
`host-camera-*` tag.
