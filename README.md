# Standards Chord Charts

Chord charts for jazz standards, with guitar and piano voicings, transposition and play-along playback. It's a single web page, built mobile first.

**Live site:** https://mediavanity-dev.github.io/standards/

## What it does

- **159 tunes:** ballads, bebop heads, blues, rhythm changes, bossa novas and modal tunes.
- **Any key:** pick a key from the menu and every chord, diagram and note name transposes with it.
- **Guitar and piano diagrams:** guitar uses movable jazz shapes. Piano shows a left-hand bass note and a right-hand voicing. Voicings are chosen across the whole tune so each chord moves as little as possible from the one before.
- **Chord detail:** tap any chord to see its notes spelled by scale degree, its piano voicing and every guitar voicing. Tap a voicing to use it everywhere in the tune. On phones the detail fills the screen.
- **Fretboard for soloing:** from the chord detail, show every chord tone across frets 0–15, labeled by degree or note name. The root is orange, the guide tones (3rds and 7ths) are filled and other chord tones are outlined.
- **Charts that read like a fake book:** four bars per row, % for repeated bars, first and second endings, bar numbers and a form summary such as "AABA · 32 bars".
- **Analysis overlays:** optional brackets under ii–V pairs and Roman numerals relative to the song's key.
- **Playback:** plays the changes at any tempo from 40 to 280 bpm, highlighting the current bar, and loops until you stop it. On a computer, the space bar starts and stops playback.
- **Playback tuning:** shifts only the sound, from 6 semitones down to 6 up, to play along on a guitar tuned down (E♭ or D tuning) or up. Chord names and diagrams stay as written, and a small tag beside the tempo shows the shift. It's under View options.
- **Your own songs:** add, edit and delete songs in the page. They're saved in your browser on that device.

## Running it

There's nothing to install or build. Open `index.html` in a browser, or use the live site. The page loads one web font from Google Fonts and works without it.

## Adding songs to the built-in list

Songs live in the `SONGS` array in `index.html`. Each entry looks like this:

```js
{t:"Autumn Leaves",key:"Gm",sec:[
{n:"A",x:2,b:"Cm7|F7|Bbmaj7|Ebmaj7|Am7b5|D7b9|Gm7|Gm7"},
{n:"B",b:"Am7b5|D7b9|Gm7|Gm7|Cm7|F7|Bbmaj7|Ebmaj7"},
{n:"C",b:"Am7b5|D7b9|Gm7 Gb7|Fm7 E7|Ebmaj7|Am7b5 D7b9|Gm6|Gm6"}]},
```

| Field | Meaning |
|---|---|
| `t` | Title |
| `key` | Key the chart is written in, such as `Bb` or `Gm` |
| `sec` | Sections, in order |
| `sec[].n` | Section name. Names starting with A–E build the form summary. |
| `sec[].b` | Bars separated by `\|`, chords within a bar separated by spaces |
| `sec[].x` | Optional: play this section this many times |
| `m` | Optional: beats per bar when it isn't 4 (`3` for waltzes, `6` for 6/4) |
| `note` | Optional: a short tag such as `"Bossa nova"`. Search matches it. |

**Beats within a bar:** chords split the bar evenly. A `.` holds the previous chord one more beat, so `Cm7 F7 Bbmaj7 .` gives Cm7 and F7 one beat each and Bbmaj7 two. In a 4/4 bar with three chords and no dots, the first chord gets beats 1–2.

**Endings:** two sections in a row with the same name that differ only in their last bar or two are shown as one section with first and second endings. Write both sections out in full.

**Shortcuts:** `rc("Title")` adds a rhythm-changes tune in Bb. `blues("Title","F","...12 bars...")` adds a 12-bar blues.

### Chord symbols

The root is a letter with an optional `b` or `#`, followed by the quality. A slash and a note name set the bass, as in `Bb/D`.

| Write | Chord |
|---|---|
| `C`, `Cm`, `C+` or `Caug`, `Csus` | Major, minor, augmented and sus triads |
| `C6`, `C6/9`, `Cm6` | Sixth chords |
| `Cmaj7`, `Cmaj9`, `Cmaj7#11` | Major sevenths |
| `Cm7`, `Cm9`, `Cm11`, `Cm(maj7)`, `Cm#5` | Minor chords |
| `Cm7b5`, `Cdim7` | Half-diminished and diminished |
| `C7`, `C9`, `C13`, `C7sus4` | Dominants |
| `C7b9`, `C7#9`, `C7#5`, `C7b5`, `C7#11`, `C7b13`, `C7alt` | Altered dominants |

Other spellings, such as `C9sus4` or `C13b9`, are voiced as the nearest chord in this table, and the chord detail panel notes it.

## About the charts

The changes are the commonly played versions, in the key most often used. Many were checked against a standard fake book. Charts vary between books and players, so check them against your favorite recording.
