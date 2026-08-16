# Verification protocol — read before touching floorplans, renders, or measurements

This file exists because of a recurring failure pattern in this project: claiming a
visual/spatial fix is correct based on surface pattern-matching (right room, right
object, roughly right area) instead of checking the specific claim being made, and
in one case answering a direct "why did this happen" question with a plausible-sounding
explanation that was never actually checked against the image. Both are worse than
being slow or saying "I don't know yet."

## 1. Before claiming any spatial/geometric fix is correct

- State the specific claim in one sentence before checking it — e.g. "the fridge is
  fully inside the nook's footprint, not in the open connector path in front of it,"
  not "the fridge looks right."
- Crop/zoom into exactly the region the claim is about. Not the whole image, not a
  nearby region — the exact spot. A wide shot that "looks plausible" is not a check.
- If the crop doesn't clearly resolve the claim, say so. Don't round an unclear read
  up to "confirmed."
- This applies to my own diagrams (SVG renders) and to Gemini's photoreal output
  separately — Gemini has repeatedly not followed explicit instructions (added walls,
  moved objects to the wrong sub-location) even when given a correct reference image.
  A correct prompt is not evidence of a correct result. Only the pixels are.

## 2. Never explain "why" without re-checking

If asked why a render came out a certain way, re-open that specific image and look
before answering. Don't reconstruct an explanation from what I intended or from a
plausible mental model of the geometry. If I can't verify the cause, say that
explicitly rather than offering a confident-sounding guess.

## 3. Measurement claims

Every dimension or wall position stated as fact must trace to one of:
- a number printed on the source drawing (`ground floor.JPG` / `first floor.JPG`), or
- a pixel measurement I actually performed and can point to, or
- an explicit "estimate, not dimensioned on the source" flag.

No unflagged invented numbers. Pixel-derived measurements have been unreliable
horizontally vs. vertically in these scans before — cross-check against a printed
dimension chain where one exists rather than trusting a single pixel ratio.

## 4. When an instruction has more than one reasonable spatial reading

If a placement/sizing instruction could mean more than one specific location or
orientation, say which specific reading I'm about to act on *before* spending a
generation round on it (a one-line "placing it flush against X, tucked behind Y —
confirm?" is cheap), or ask directly if genuinely unsure. Don't silently pick one
interpretation and present the result as the obvious correct reading of what was
asked.

## 5. Delivering a "fixed" render

Before sending an edited render back, crop into the exact spot the complaint was
about and compare it against the specific complaint, not the image as a whole.
