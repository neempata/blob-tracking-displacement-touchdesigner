# Blob Tracking Displacement Filter

This is a small [TouchDesigner](https://derivative.ca/) project that turns the
shapes in an image into moving visual effects. It uses blob tracking to find
distinct areas in a camera feed, video, or other image input, then uses that
tracking information to influence a displaced or filtered version of the image.

The project is intended as a place to learn and experiment. You do not need to
understand every operator before opening it. Start by following the image
through the network and observing how it changes at each stage.

## What Is a Blob?

In this project, a *blob* is a connected bright or dark region in a processed
image. For example, a hand against a plain background can become one or more
blobs after the image is converted to a high-contrast black-and-white mask.

TouchDesigner can calculate information about each blob, such as its position,
size, and area. That information can then drive other parts of a composition:
an image can bend around a blob, a circle can be drawn at its position, or text
can be placed above it.

## How the Network Works

The exact arrangement of operators is stored inside the `.toe` project file,
but the project follows this general flow:

1. **Input** - A camera, movie, or other TOP provides the original image.
2. **Image preparation** - The image is cleaned up and adjusted so the subject
   stands out from the background. Common controls here include brightness,
   contrast, blur, and color adjustments.
3. **Threshold or mask** - The prepared image is reduced to areas that count as
   foreground. This is the black-and-white image that makes the blobs easier to
   see and track.
4. **Blob tracking** - TouchDesigner analyzes the mask and reports the detected
   blobs. Their position is usually represented as normalized coordinates, where
   `0` is one side of the image and `1` is the other.
5. **Displacement and output** - The image is warped or filtered to create the
   final effect. The tracking result can be used to control where and how
   strongly this happens.

When exploring the network, TOPs are the image-processing operators, CHOPs
carry changing numeric values, and COMPs contain or organize parts of the
project. The viewer on an operator is useful: turn on viewers at different
stages to compare the original input, mask, tracking result, and final output.

## Opening the Project

1. Install a TouchDesigner version that can open the project file.
2. Open `blobtracking.9.toe`.
3. Find the input operator and check that it is receiving an image. A camera
   may need permission from the operating system, and a movie input may need a
   valid file path on your computer.
4. View the mask or threshold stage first. If the subject is not clearly
   separated from the background there, blob tracking will not be reliable.
5. View the tracking and final output stages, then adjust one control at a
   time.

If the project opens but the output is empty, check the input image before
changing tracking settings. If the input works but no blobs appear, adjust the
threshold and improve the contrast between the subject and background.

## Tuning Tips for Beginners

- Use even lighting and avoid reflections or shadows that could be mistaken
  for blobs.
- A simple, uncluttered background makes the mask much easier to control.
- Change one parameter at a time so you can tell what caused the result.
- Watch the mask while tuning. A useful mask has clear subject shapes without
  lots of isolated specks.
- If there are too many small blobs, try removing noise or increasing the
  minimum blob size. If a subject disappears, make the threshold less strict
  or improve the lighting.
- Different inputs need different settings. Values that work for a webcam may
  not work for a dark video or a brightly lit room.

## Making Experiments

Save the original project as a copy before making a large change. Useful names
make it easier to return to an earlier idea:

```text
blobtracking-low-light.toe
blobtracking-multi-subject.toe
blobtracking-calibrated.toe
```

The `.toe` files are binary project files, so Git cannot show useful line-by-line
diffs or merge their contents automatically. Small commits with a short note
are the easiest way to remember what changed. Recheck camera paths, device
settings, and other machine-specific values when opening a copy on another
computer.

## Ideas to Try Next

- Add text that displays a number beside each detected blob. This will require
  connecting each blob's position to a text or instancing system.
- Add a small circle or marker at each blob position while debugging. Seeing the
  marker move is often easier than judging the displacement effect alone.
- Experiment with blur, feedback, trails, color effects, or different
  displacement maps around the tracked areas.
- Compare one large blob with several smaller blobs and note which tracking
  settings produce stable results.

## Project Checklist

Before using the effect in a live setup, test the complete input, mask,
tracking, and output chain with the actual camera, lighting, and subject. Keep
large rendered videos and disposable captures out of version control unless
they are needed as project references.
