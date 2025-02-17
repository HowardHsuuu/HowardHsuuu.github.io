---
title: "[LR] Interfacing with Lucid Dreams"
date: 2024-09-25T20:33:52+08:00
draft: false
tags: ["Human-Computer Interaction"]
---

[This review is intended solely for my personal learning]

Paper Info - LuciEntry
> DOI: 10.1145/3613905.3649123  
> Title: LuciEntry: A Modular Lab-based Lucid Dreaming Induction Prototype  
> Authors: Po-Yao (Cosmos) Wang, Nathaniel Lee Yung Xiang, Rohit Rajesh, Antony Smith Loose, Nathan Semertzidis, and Florian ‘Floyd’ Mueller  

Paper Info - DreamCeption
> DOI: 10.1145/3613905.3649121  
> Title: DreamCeption: Towards Understanding the Design of Targeted Lucid Dream Mediation  
> Authors: Po-Yao (Cosmos) Wang, Rohit Rajesh, Antony Smith Loose, Nathaniel Lee Yung Xiang, Nathalie Overdevest, Nathan Semertzidis, and Florian ‘Floyd’ Mueller  

## Prior Knowledge

Lucid dreaming is a phenomenon wherein sleepers become aware of dreaming while asleep, often enabling manipulation of dream content and providing potential benefits such as enhanced creativity, nightmare alleviation, and stress relief. Past research has focused on techniques for lucid dream induction (e.g., wake-back-to-bed, mnemonic induction) and explored the use of interactive technologies—such as auditory or visual cues—to influence dream content. However, effectively automating or streamlining this process, as well as helping dreamers shape specific dream topics, remains a challenge.

## Goal

Both **LuciEntry** and **DreamCeption** explore how interactive systems can be harnessed to facilitate lucid dreaming:

- **LuciEntry** seeks to simplify and automate the induction of lucid dreams in a lab setting, featuring a modular and autonomous platform that detects REM and delivers multiple cues (visual, auditory, electrical) at the right moment to trigger lucidity. By reducing researchers’ workloads and increasing reliability, LuciEntry aims to make the study of lucid dreaming more systematic and accessible.

- **DreamCeption** focuses on shaping or “inserting” specific dream themes once a lucid dream is detected, thereby expanding what lucid dreamers can do after attaining lucidity.

## Method

#### LuciEntry

1. **Wake-Back-to-Bed Protocol**: Participants sleep 4 hours uninterrupted, then awaken briefly for cognitive training (e.g., MILD).
2. **Modular Architecture**: A headband with EEG and EOG electrodes connects to a Raspberry Pi server. When sustained REM is detected, the server automatically triggers external cues—LED flashing, binaural beats, and 40 Hz tACS—without researcher intervention.
3. **Emergency Button**: Users can halt stimulation at any time, ensuring safety and peace of mind.

#### DreamCeption

1. **Closed-Loop Detection**: Employs brain (EEG) and eye (EOG) sensors to identify when users enter a lucid dream.
2. **Targeted Stimuli**: Once lucidity is detected (participants move their eyes in a specific pattern, e.g., left-right signals), the system provides stimuli—visual (light), auditory (sound effects), and even haptic or galvanic vestibular stimulation—corresponding to a chosen dream theme (e.g., “scuba diving”).

## Results

#### LuciEntry

- In a pilot study with three overnight sessions, two participants reported achieving short lucid dreams after receiving the visual/audio/electrical cues.
- Demonstrated “dream incorporation,” where external stimuli (flashing lights, sounds) were woven into dream narratives (e.g., seeing brake lights in a racing dream).
- Identified system hurdles such as sensor calibration, headband comfort, and ensuring fully autonomous operation.

#### DreamCeption

- Illustrates how well-timed “dream prime” stimuli can lead lucid dreamers to incorporate specific elements (e.g., ocean sounds, bubble haptics) into their dream worlds.
- Underscores that real-time detection of lucidity is crucial to deliver prompts effectively.

## Conclusion

Taken together, **DreamCeption** and **LuciEntry** exemplify how HCI-driven solutions can deepen our engagement with lucid dreaming. **DreamCeption** offers a vision of _content-rich dream design_, enabling users to “sculpt” their dream environment. Meanwhile, **LuciEntry** addresses _scalable, automated induction_, promising a more robust framework for controlled experiments and eventual personal use. Both open exciting avenues in dream engineering—where carefully timed interventions harness the dreamer’s brain state to either reliably induce or intricately shape dream content.

These two prototypes illustrate an emerging intersection of immersive design, biofeedback, and sleep science, pushing beyond conventional VR experiences into the realm of dreams.

## Limitations
1. **Signal Quality**: EEG and EOG readings can be prone to interference from movement or improper electrode placement, potentially impeding real-time detection.
2. **Short Lucid Durations**: While users became aware of dreaming, many reported only fleeting moments of lucidity. Lengthening such episodes remains a challenge.
3. **Wearability**: Discomfort from wearing headsets or electrodes overnight can disrupt sleep and reduce data reliability.

---

## Reference
* The paper: 
    * LuciEntry: https://dl.acm.org/doi/10.1145/3613905.3649123
    * DreamCeption: https://dl.acm.org/doi/10.1145/3613905.3649121
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original papers.