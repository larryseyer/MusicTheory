MusicTheory [![Build Status](https://travis-ci.org/cemolcay/MusicTheory.svg?branch=master)](https://travis-ci.org/cemolcay/MusicTheory)
===

A music theory library with `Key`, `Pitch`, `Interval`, `Scale` and `Chord` representations in swift enums.

Requirements
----
* Swift 4.0+
* iOS 8.0+
* macOS 10.9+
* tvOS 9.0+
* watchOS 2.0+

Install
----

```
pod 'MusicTheorySwift'
```

Usage
----

`MusicTheory` adds a bunch of basic enums and structs that you can define pretty much any music related data. Most importants are `Pitch`, `Key`, `Scale` and `Chord`.   

All data types conforms `Codable`, `CustomStringConvertable`.  
`Pitch`, `Key`, `Interval`, `Accident` structs are `RawPresentable` with `Int` as well as `ExpressibleByIntegerLiteral` that you can represent them directly with `Int`s.

#### `Pitch` and `Key`

- All keys can be defined with `Key` struct. 
- It has a `KeyType` where you can set the base key like C, D, A, G, and an `Accitental` where it can be `.natural`, `.flat`, `sharp` or more specific like `.sharps(amount: 3)`.
- You can create `Pitch`es with a `Key` and octave.
- Also, you can create `Pitch`es and `Key`s with MIDI note number.
- `Pitch`, `Key`, `Accidental` structs are equatable, `+` and `-` custom operators defined for making calulations easier.
- Also, there are other helper functions or properties like frequency of a note.

``` swift
let dFlat = Key(type: d, accidental: .flat)
let c4 = Pitch(key: Key(type: .c), octave: 4)
```

#### `Interval`

- Intervals are halfsteps between notes.
- They are `IntegerLiteral` and you can make add/subsctract them between themselves, notes or note types.
- You can build scales or chords from intervals.
- m2, M2, m3, M3, P4, d5, P5, m6, M6, m7, M7 and P8 are predefined intervals.

#### `ScaleType` and `Scale`

- `ScaleType` enum defines a lot of readymade scales.
- Also, you can create a custom scale type by `ScaleType.custom(intervals: [Interval], description: String)` 
- `Scale` defines a scale with a scale type and root key.
- You can generate notes of scale in an octave range.
- Also you can generate `HarmonicField` of a scale.
- Harmonic field is all possible triad, tetrad or extended chords in a scale.

``` swift
let c: NoteType = .c
let maj: ScaleType = .major
let cMaj = Scale(type: maj, key: c)
```

#### `ChordType` and `Chord`

- `ChordType` is a struct with `ChordPart`s which are building blocks of chords.
- You can define any chord existing with `ChordType`.
- Thirds, fifths, sixths, sevenths and extensions are parts of the `ChordType`. 
- Each of them also structs which conforms `ChordPart` protocol.
- `Chord` defines chords with type and a root key.
- You can generate notes of chord in any octave range.
- You can generate inversions of any chord.

``` swift
let m13 = ChordType(
  third: .minor,
  seventh: .dominant,
  extensions: [
    ChordExtensionType(type: .thirteenth)
  ])
let cm13 = Chord(type: m13, key: .c)
```

#### `Tempo` and `TimeSignature`

- Tempo is a helper struct to define timings in your music app.
- TimeSignature is number of beats in per measure and `NoteValue` of each beat.
- You can calculate notes duration in any tempo by ther `NoteValue`.
- Note value defines the note's duration in a beat. It could be whole note, half note, quarter note, 8th, 16th or 32nd note.

Documentation
----

[Full documentation are here](https://cemolcay.github.io/MusicTheory/)

Unit Tests
----

You can find unit tests in `MusicTheoryTests` target.  
Press `⌘+U` for running tests.

AppStore
----

This library battle tested in my apps for iOS, macOS, watchOS and tvOS, check them out!  
[KeyBud](https://itunes.apple.com/us/app/keybud-music-theory-app/id1203856335?mt=8) (iOS, watchOS, tvOS, macOS)  
[FretBud](https://itunes.apple.com/us/app/fretbud-chord-scales-for-guitar-bass-and-more/id1234224249?mt=8) (iOS, watchOS, tvOS)  
[ChordBud](https://itunes.apple.com/us/app/chordbud-chord-progressions/id1313017378?mt=8) (iOS)  
[ArpBud](https://itunes.apple.com/us/app/arpbud-midi-sequencer-more/id1349342326?ls=1&mt=8) (iOS)
