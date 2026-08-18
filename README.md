# Blob Tracking

A TouchDesigner project for building and iterating on a real-time blob-tracking
workflow. It is organized as a compact project file with versioned working
copies, making it easy to open the latest composition, tune the tracking chain,
and save experiments without replacing the main file.

## Project Files

- `blobtracking.toe`: current working project
- `blobtracking.9.toe`: latest numbered snapshot
- `blobtracking.8.toe`: earlier snapshot
- `NewProject.toe`: original project copy
- `Backup/`: TouchDesigner-generated backup files; kept locally but ignored by
  Git

Use `blobtracking.toe` as the normal entry point. The numbered files are useful
reference points when comparing changes or recovering an earlier setup.

## Requirements

- [TouchDesigner](https://derivative.ca/), using a version compatible with the
  project file
- A camera, capture device, video file, or other input configured in the
  network when using live tracking

## Quick Start

1. Open `blobtracking.toe` in TouchDesigner.
2. Confirm that the intended input source is available and producing an image.
3. View the tracking output and adjust the relevant controls for the current
   lighting, background, and subject.
4. Save meaningful iterations under a new, descriptive project filename.

## Working With the Project

Blob tracking is highly dependent on the input scene. When tuning the network,
change one control at a time and check both the thresholded image and final
tracking result. Stable lighting, clear contrast between the subject and its
background, and a clean input image generally produce the most reliable
results.

Keep the main project file focused on the current working version. Use
descriptive copies for experiments, for example:

```text
blobtracking-low-light.toe
blobtracking-multi-subject.toe
blobtracking-calibrated.toe
```

## Version Control

TouchDesigner `.toe` files are binary project files. Git can store their
history, but cannot provide useful line-by-line comparisons or automatic merge
resolution. Make small, purposeful commits and include a short note describing
the change, such as an input adjustment, threshold calibration, or tracking
behavior update.

The included `.gitignore` excludes automatic backups, temporary files, Python
cache files, and operating-system metadata. It intentionally does not ignore
project files or source media, so important creative work can be versioned when
needed.

## Notes

- Test with the actual camera and lighting setup before relying on the tracker
  in a live environment.
- Avoid committing large rendered videos or disposable captures unless they are
  essential project references.
- If a project copy contains machine-specific device settings, recheck the
  input configuration after opening it on another computer.

  ## Improvements
