# Acoustic Manifold

A single-file, offline-capable browser tool that turns animal songs and other sounds into spectral maps. Drop in a bird call, a whale phrase, a cricket trill or a thunderstorm and see where it lives in acoustic space.

**Live app:** https://grumby42.github.io/accoustic-manifold/

Build: `AMX-20261107-1910Z` · README shipped `2026-11-08T19:36:12Z` (UTC)

## What it shows

Every panel comes from frame-by-frame spectral analysis (a 2048-point FFT window slid across the audio). Nothing is uploaded; all processing runs in your browser.

| Panel | What it is |
|---|---|
| **Acoustic manifold** | Each point is one time-slice's feature vector (centroid, spread, tonality, crest, entropy, slope, rolloff, flux, RMS), projected to 2D with PCA. Points are colored by spectral centroid and sized by loudness. Faint threads connect consecutive frames, so the shape is the song's path through acoustic space. |
| **Spectrogram** | Log-frequency time-frequency view, with the spectral centroid traced in white. Click or drag to seek. |
| **Spectral descriptors** | Radar of eight normalized descriptors at the current instant, over the clip's average. |
| **Centroid–amplitude profile** | Loudness against pitch, colored by spectral flux (how fast the spectrum is changing). |

## Using it

1. Open the app, then **Synthesize demo song** or **Synthesize demo set** to see it working with no files.
2. **Load audio files** or drag recordings onto the drop zone (WAV, MP3, FLAC, OGG; stereo is mixed to mono).
3. Scrub the **time** slider, press **Play / sweep**, click the spectrogram, or click a manifold point to jump to that moment.
4. With two or more clips loaded, **Compare (mix)** overlays them in one shared projection, so positions are comparable across clips.

### Frozen reference basis

By default the shared projection refits whenever the set of clips changes, so the map is relative. **Freeze basis** locks the current projection; new clips are then placed into fixed coordinates, with the reference set drawn as a grey cloud for context. **Export basis** saves it as JSON, and **Import basis** restores it later or on another device, reproducing identical coordinates.

## Where to get recordings

The **Sources** button in the app lists these too.

- **Birds:** [Xeno-canto](https://xeno-canto.org) (Creative Commons, direct downloads; also frogs, bats, insects) · [Macaulay Library](https://www.macaulaylibrary.org) (Cornell)
- **Whales and marine mammals:** [Watkins Marine Mammal Sound Database](https://cis.whoi.edu/science/B/whalesounds/index.cfm) (WHOI) · [NOAA SanctSound](https://sanctsound.ioos.us/)
- **Ocean and earth sounds:** [NOAA PMEL Acoustics](https://www.pmel.noaa.gov/acoustics/multimedia.html) (icequakes, undersea earthquakes, vents)
- **Other animals:** [Tierstimmenarchiv](https://suche.tierstimmenarchiv.de/?language=english) (Museum für Naturkunde Berlin)
- **Weather and ambient:** [BBC Sound Effects](https://sound-effects.bbcrewind.co.uk) · [Freesound](https://freesound.org)

Each source sets its own terms. Most allow personal and research use; check before any commercial reuse.

Clean, isolated single-source clips give the most legible maps. Trim long files, since the analysis caps the frame count.

## Limits

- The manifold uses PCA, which is fast and deterministic. A nonlinear projection such as UMAP or t-SNE would show tighter clusters.
- Below a few hundred Hz the spectrogram resolves to about 21 Hz (set by the 2048-point window), so very low whale song looks blocky.

## Credits

Visual language inspired by the spectral bird-song pieces of [@lucioarese](https://www.instagram.com/lucioarese/). This is an independent implementation.

Built by Ted Gransbury. MIT licensed; see [LICENSE](LICENSE).
