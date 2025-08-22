# TTSSorcery

TTSSorcery is an extension that can generate TTS with multiple speakers and emotions all in one message. Since it uses Sorcery's method of executing actions the moment of the stream, that means TTS with multiple character voices with various audio variants/emotions can be genrated while the response is streaming. It uses custom text to speech from Zyphra's API (free) but with added features. The extension uses direct code and prompts from https://github.com/p-e-w/sorcery/tree/master

This is NOT integrated/compatible with sillytavern's built in text to speech, and only works with chat completions for now

## So how does it work

1. A prompt is injected to make the AI add special text to speech markers to the text (`§c:Character|happy.mp3|e1:0.8§`) 
2. These markers tell the extension who is speaking and how they should sound, and in what emotion
3. The extension processes these markers and sends them to zyphra's api
4. Zyphra returns audio files that are played in order

## How do i set it up

1. Get a zyphra api key (free tier gives 100 minutes/month)
2. Add your api key in the extension settings
3. Upload at least one voice sample for the Narrator
4. Add character voices as needed
5. Enable the extension

## Features

- **Voice cloning**: Upload any audio sample to clone voices for any character you want
- **Audio variants**: Create different emotional versions of a character's voice (happy, sad, angry, etc.), you just need to find the voice file online
- **Emotion control**: The ai automatically adds emotion values to dialogue, as Zonos model supports it
- **Multiple languages**: Supports English, Japanese, Chinese, French, German, Korean
- **Preloading**: Preloads audio segments so it doesn't pause for a long time mid generation

## How do i use the extension

- **Auto generation**: When enabled, automatically generates text to speech for new messages as long as streaming is enabled
- **Manual generation**: Click the wand icon in the menu or the three dots on any message then the wand
- **Playback controls**: Toggle playback from inside ST

## Audio variants

You can upload different versions of a character's voice for different emotions. Create variants with names like "happy", "sad", "angry", etc so the AI can know what audio variant to use for the context. You can add as much as you want, there is no limit.

## Emotion values

The AI adds emotion values to each dialogue segment using these 8 emotions:
1. Happiness
2. Sadness
3. Disgust
4. Fear
5. Surprise
6. Anger
7. Other
8. Neutral

This is included in every dialogue zonos tts generates

## Tips

- Use hybrid model over transformer, it has better voice quality
- Only works with chat completion (not text completion)
- Auto generation only works with streaming enabled
- 10-30 second audio samples work best
- Avoid background noise in your voice samples, if you cant, enable speaker denoising

## Issues

This extension has lots of bugs and almost 80% depends on you having a smart model. The regex it uses to detect characters can break if the model isnt smart enough to put it in the right placing. This has only been tested with models like Claude 3.7, Claude 3.5, Claude Opus, Gemini Pro, Claude Haiku so keep that in mind. It also only works with chat completion for now.