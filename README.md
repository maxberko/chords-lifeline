# Chords Lifeline

Branch `line`: the map is drawn as a living vine instead of a circle. What you played is the stem, tapering into the past with a seed per chord; the chord you are on is the bloom, breathing; the next options are tendrils that grow out to the right and sway. Thicker tendril means more likely; the buds along a tendril mark each semitone the voices travel, so a short bare tendril is a smooth move and a long budded one is a leap. Green tendrils stay in the key, rust ones are borrowed chords or secondary dominants. Hover a tendril for the reasoning, click it to move there, click a past seed to rewind. Demo plays a looping progression in the current key through the speakers and the detector; `?seed=C,Am,F,G7` composes a history at load without audio.

Live: https://maxberko.github.io/chords-lifeline/line/

Live (main branch, radial map): https://maxberko.github.io/chords-lifeline/

A composing aid. Play chords on piano or guitar; the app keeps the history of what you played (the lifeline), infers the key from it, and draws a radial map of where you can go next. Closer to the centre means more likely. Each option carries the 7th flavour it takes in that key (Fmaj7, G7, Am7), and the current chord shows which 7ths fit it.

Single-file web app (`index.html`), no build step. Serve it locally:

```bash
python3 -m http.server 8767
```

- Chord recognition in the browser (Web Audio API): FFT, chroma, template matching for major, minor, maj7, 7 and m7.
- Key inference from the recent history, with a manual override. Major and minor modes have their own role tables.
- Style selector: Neutral, Pop or Jazz. Each style has its own transition tables, weights for secondary dominants and borrowed chords, and 7th habits (Pop favours plain triads and add9; Jazz favours ii–V motion, tritone substitutes and extended 7ths).
- Ranking is a small, readable transition table per function (I, ii, iii, IV, V, vi and the minor-mode degrees), plus secondary dominants, borrowed chords and the parallel key at lower weights. Neutral style.
- No microphone? Click any option to compose by hand. Test with synthetic chords: `index.html?test=Am,Dm,E7,Am`.
