---
title: "[LR] Clonemator: Spatiotemporal Clones in VR"
date: 2024-09-27T19:56:26+08:00
draft: false
tags: ["Human-Computer Interaction", "Virtual Reality"]
---

[This review is intended solely for my personal learning]  

[The VR project, **ChronoClones**, in OpenHCI 2024 was based on this paper]

Paper Info
> arXiv: 2311.04427  
> Title: Clonemator: Composing Spatiotemporal Clones to Create Interactive Automators in Virtual Reality  
> Authors: Yi-Shuo Lin, Ching-Yi Tsai, Lung-Pan Cheng  

## Prior Knowledge
- **Interaction Techniques in VR**: Traditional approaches (e.g., Go-Go, portals) focus on specific tasks or single-avatar enhancements. While helpful, these designs rarely offer a broad, integrative way to handle diverse, complex interactions without pre-coded solutions.  
- **Programming by Demonstration (PbD)**: Non-VR automation tools like Sikuli or Ringer let users capture and replay interactions to automate tasks. However, applying PbD to immersive VR—where physical presence, body movement, and 3D spatial context matter—is underexplored.


## Goal
Clonemator aims to let users create and collaborate with virtual “clones” of themselves to accomplish complex or repetitive tasks, all without manual scripting. By allowing clones to be configured across space (e.g., different locations, scales) and time (e.g., static pose, synchronous motion, or replayed actions), the system seeks to empower users to construct flexible, intuitive “automators” for tasks ranging from object manipulation to cooperative assemblies.


## Method
1. **System Components**  
   - **Spatial Manipulations**:  
     - *Spawn Methods*: Direct, Indirect, Auto, and Relative allow users to generate clones at specific positions or in bulk.  
     - *Movement & Control*: Users can switch first-person perspective to any clone, group them to lock relative positioning, mirror or scale them, etc.  
   - **Temporal Modes**:  
     1. *Static*: The clone remains “frozen” in the spawned pose.  
     2. *Synchronous*: The clone mimics the user’s real-time movements.  
     3. *Replay*: The clone executes recorded actions (including object interactions) on a loop.

2. **Implementation**  
   - Built in Unity for a Meta Quest 2 setup. Avatars animate via inverse kinematics from headset/controller input. A wrist-mounted menu and voice commands handle cloning and mode changes.

3. **Preliminary User Study**  
   - **Participants**: 12 volunteers, mostly with little VR experience.  
   - **Procedure**: Two parts: (a) a tutorial with guided tasks—hammering pegs, catching fish, fanning flames while cooking; (b) independent tasks where participants devised strategies for challenges like moving heavy objects or retrieving items from high shelves.  
   - **Observations**: Noted solution diversity, user feedback on intuitiveness, any difficulties encountered.


## Results
- **Creative Compositions**: Participants tackled the same tasks with varied strategies. For instance, one formed a “bucket brigade” of clones passing objects synchronously; another stacked static clones as a step stool to reach elevated items.  
- **Ease of Use**: Many found direct spawning and synchronous control “very natural,” particularly once they realized clones could hold objects, mirror movements, and be grouped or duplicated.


## Conclusion
Clonemator expands VR interaction beyond one-body, one-task paradigms. By combining key PbD principles—recording user actions—and flexible re-spawning of those actions in clone form, it enables a user-friendly path to on-the-fly automation. Early evidence suggests that novices rapidly adopt these spatiotemporal cloning techniques to build surprisingly complex solutions in VR without explicit programming.


## Limitations
1. **Limited Body Tracking**: Only headset and controllers drive the full-body avatar, restricting lower-body fidelity.  
2. **Precise Alignment Needs**: Complex tasks sometimes require further “snapping” or advanced positioning aids to ensure clones align exactly with small targets.  
3. **Cognitive Load**: Managing many clones with different timings can overwhelm users in intricate scenarios.  
4. **Replay Editing**: Replaying continuous user actions is powerful, but advanced editing or partial replays could further expand utility.


## Reference
* The paper: https://arxiv.org/abs/2311.04427  
* This note was written with the assistance of Generative AI and is based on the content and results presented in the original paper.