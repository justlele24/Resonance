# Resonance

**The Neuroscience of Music** — An interactive iOS app that teaches how the brain processes music through hands-on musical games.

Built for the **2026 Swift Student Challenge** by Raffaele Barra.

---

## Concept

You meet **Tempo**, a character whose brain has been scrambled. Each region that processes music is broken — sounds are jumbled, rhythm is lost, emotions are mixed up, and melodies are forgotten. Your job is to repair each region by completing interactive musical challenges, learning real neuroscience along the way.

## Stations

### 1. Motor Cortex — Rhythm Patterns
Repeat rhythmic sequences on drum pads, testing memory and timing. A speed round challenges your reflexes. Teaches how the motor cortex coordinates movement in response to rhythm through auditory-motor coupling.

### 2. Auditory Cortex — Tonotopic Mapping
Match frequencies to their correct positions on the brain's sound map. Demonstrates tonotopy — how the auditory cortex is physically organized from low to high frequencies, mirroring the cochlea's structure.

### 3. Amygdala — Mood DJ
Mix three musical parameters (key, tempo, brightness) to recreate target emotions. Explores how the amygdala evaluates acoustic features to generate emotional responses — major/minor keys, fast/slow tempos, and timbral qualities.

### 4. Hippocampus — Memory Fragments
Listen to a melody, watch it shatter into fragments, then reconstruct the original sequence from memory. Models how the hippocampus encodes, fragments, and reconstructs memories.

## Learn Tab

Seven illustrated articles covering the neuroscience behind each station — neuroplasticity, dopamine and musical reward, the amygdala's emotional processing, tonotopic maps, motor cortex rhythm coupling, hippocampal memory encoding, and the role of serotonin and cortisol. Each article features Canvas-drawn brain region illustrations and chemical molecule diagrams (dopamine, serotonin, cortisol). A full list of 30+ peer-reviewed sources is accessible from the Sources button.

## Technical Highlights

- **All audio synthesized in real-time** using `AVAudioEngine` with custom render blocks — no audio files except the background music track
- **Custom drum synthesis** with bass drum (sine + pitch sweep + noise burst), snare, and hi-hat
- **Piano-like tone synthesis** with harmonic overtones and exponential decay envelopes
- **Emotion synthesis** with arpeggiated chords, valence-mapped consonance/dissonance, and arousal-driven pulse
- **Canvas-drawn illustrations** — brain diagrams, chemical molecules (dopamine, serotonin, cortisol), neural networks, all rendered programmatically
- **Full Apple Accessibility compliance** — VoiceOver labels on all interactive elements, Dynamic Type support, 44pt minimum touch targets, Reduce Motion support (all animations guarded), haptic feedback toggle, sound effects toggle, high contrast mode
- **Swift 6 strict concurrency** — all Timer closures wrapped in `MainActor.assumeIsolated`, thread-safe audio state with `NSLock`, `@Sendable` callback types
- **Zero external dependencies** — pure SwiftUI + AVFoundation

## Architecture

```
App/            Navigation, state management, onboarding, tabs
  AppState      Central state manager with guarded haptics and animations
  ContentView   Root view with TabView (Play + Learn)
  SplashView    Animated landing screen with particle system
  MascotIntroView  Tempo's story with typewriter dialogue
  JourneyMapView   Station selection with progress tracking
  LearnView     Article library with illustrated cards
  InfoSheets    About, Accessibility settings, Credits

Audio/          Real-time audio synthesis
  AudioEngine   Background music + shared audio session
  ToneGenerator Tonotopy station sine waves
  MoodSynth     Amygdala station arpeggiated chords
  EmotionSynth  Amygdala emotion feedback with pulse
  MelodySynth   Hippocampus piano-like sequences

Components/     Reusable UI components
  BrainIllustration  Full brain diagram with region highlighting
  BrainRegionSketch  Isolated region drawings (seahorse, almond, etc.)
  TempoPopup    Overlay dialogue system with mascot
  ClickSound    Synthesized UI click sounds (WAV in memory)

Stations/       Game views
  MotorCortexView      Drum pad rhythm game
  ListeningBrainView   Frequency mapping challenge
  EmotionalBrainView   Mood DJ toggle mixer
  MemoryFragmentsView  Melody reconstruction with drag-and-drop
```

## Requirements

- iOS 16.0+
- Swift Playgrounds 4.5+ or Xcode 16+
- Headphones recommended for the full experience

## Credits

- **App Creator**: Raffaele Barra
- **Background Music**: "Shine" by Onycs, licensed via BreakingCopyright (Free To Use)
- **Scientific Sources**: 30+ peer-reviewed papers — see Sources sheet in the Learn tab
