ResizableImageViewAutoLayout
===


Description
---

I'm trying to draw a round rect and behind some content. I created an image asset with the appropriate cap insets. I then added an image view as a subview of a container view, and pinned its left/right/top/bottom to the superview. (The actual content will be in a sibling view of the image view with a higher Z index.)

If the center stretchable area of the image is any greater than 1px by 1px, the image view does not lay out correctly. It is too big in each dimension by the size of its center area.

This wouldn't be too big of a deal if the 1px/1px center size didn't cause serious problems with the alignmentRectInsets property. Setting the alignmentRectInsets to small nonzero values with a 1px/1px center causes the view to become GIGANTIC and Auto Layout to complain.

Steps to Reproduce
---

1. Run the attached demo app
2. Quit the simulator, open ImageAssets.xcassets
3. Select the PinkBackground@1x image
4. In the Slicing section of the Attributes inspector, change the Width and Height of the Center area to 1px by 1px
5. Re-run the app

Expected Results
---

On both runs, the round rect is centered in the simulator.


Actual Results
---

Round rect is too big and off-center. On the first run, it's off by about 92 pixels (those pixels should have been squished).

On the second run, the view is too large for Auto Layout to handle, and trying to use View Debugging crashes Xcode.