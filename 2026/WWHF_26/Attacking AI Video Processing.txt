# Attacking AI Video processing
Presenter: Patrick Double

Major cloud provider (AWS?)

Summarization of content of a video

LLM prompt injection was a concern

Test Data
 - What comprises a video
 - How is data being processed?
 - How to generate test cases quickly
TOOLSET!

Cross tenant data exposure
Prompt injection
Service degredation
Service outages

Use Cases:
 Healthcare
 Security Camera
 Vehicle Insurance Claims

Video Concepts

Container (Mp4, MKV, MOV, etc)
Audio, Video, subtitle, metadata containers

Resolution, FPS, encryption
H264/H265 for video
AVC, Mp3, Opus, EC3
Text based subtitles, most interesting


Processing popeline arch

Video input -> Guardrail
Guardrail -> frame extraction
Guardrail -> transcription
Guardrail -> subtitle extraction
FrameExtraction -> Scene detection
FrameExtracition -> Object classification
Frame extraction -> frame embedding
Frame extraction -> OCR



Gauardrail validate input and output
subject to vuns
Mau be mplemented with llms


Scene detection
Built in breaks vs autodetection via sampling
Light level 
sound level
object id
black frames

object classification -> ml, id people, object, animal, etc
determined by the model being used. Needs full frames

Frame embedding -> ml model to vector,
OCR -> get characters from the screen

transcription -> do we need to look at multiple channels
text may be safe if it was produced by a controlled process.

Frame captuion vs object extraction

may coerce prompt injection




Prompt Injection

-> Give instructions to a model that illicites a malicious behavior

Bypass Guard rails

Information overload
Which streams is it appied to
Unexpepcted content: long subtitles

LLM Template

Creat a concise, coherent summary of the video based on the scene trancsiprts and visual cues below

Prompt spread across steams to avoid detection

Text-To-Video.py

Generate a video with text, optional TTS and embedded subtitles


LLM confusion
  - Use unrelated or fantastic content to confuse the llms
  
Resource exhaustion

Use too much compute, memory or storage

Limit file size
 - Codec could make an explosion of data
High-Video-scene-rate.py


Create highly noisy inputs to confuse object count

Large video resultion

High framerate, compression does a good job of masking

Mp4 timestamps

MP4_DATETIME_FUZZER.py
Output csv of what changes made

Random Errors

SCATTER_BYTES.y

TEXT_TO_IMAGE.py

LOREM.py generate random text

Collected a list of prompt injection, run them through the various scripts to see the output


github.com/bvcyber/video-fuzzing
