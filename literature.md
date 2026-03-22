
# Introduction

### Scope

This literature review targets the filed of __controlling robots with end-to-end neural networks__, especially the bahaviour cloning approach applied to manipulation.
Due to good success, even this formerly tiny subfield of roboics got a lot of attention lately resulting in a huge number of publications.  
Looking for methods suitable for application in __industrial settings__, whith very high requirements on reliability and success rate, there are very few papers though. 
The vast majority of papers tries to generalize as broad as possible (e.g. to tackle the infinite variety in homes) and seldom to make use of good prior knowledge (as often is available in industry settings) or system approaches in order to reach success rates above 99%. 

So in the following I try to collect a selection of publications that reflect the field and are a good starting point to further the research targeting applications where high success rate is more important than generality (though still welcome of course). Be aware that most of the cited papers have a different goal though.

### Sources

Main source of course is __arxiv__, where almost all research for the topic is available, often acompanied by code in __github__. Where available the links lead to the project pages since they give quick overview, often a video and include links to arxiv and github.   
An other very valuable and recomendable resource are __videos of current workshops__. Especially the experience reported and practical advice given makes them worth watching. Much more than in papers, also failed tries and negative results are reported.


### Recency

Since the field is progressing extremely fast, every document like this will be outdated within weeks in the details. Most of the following is as of August with __last updates end of September 2005__. While still being a good introduction, overview and entrypoint (the questions and methods don't change that quickly)it will be necessary to lookout for newer ideas, models and code all the time.   

For longer term projects I would recomend to automate (even if very basic) the search and filter process and connect the result output to a chat channel for low-threshold access to the team and immediate appropreation and discussion. Add a "ask the paper" CoPilot connection if possible.   
At the minimum, skim a simple keyword based search like [robot+VLA](https://arxiv.org/search/advanced?advanced=&terms-0-operator=AND&terms-0-term=VLA+robot&terms-0-field=abstract&classification-computer_science=y&classification-physics_archives=all&classification-include_cross_list=include&date-year=&date-filter_by=date_range&date-from_date=2025-01-01&date-to_date=&date-date_type=submitted_date&abstracts=show&size=50&order=-announced_date_first) regularly as a very first step. You will find interesting new papers almost every day.   

### From ALVINN to π₀, A Short **History** of End-to-End Robot Policies

This review focuses on future opportunities, not history. A very short peek into development of the field in focus to where the project is today: 

**1988 — ALVINN**
Dean Pomerleau’s *Autonomous Land Vehicle in a Neural Network* showed the first true end-to-end behavioral cloning policy. A simple network mapped raw camera pixels directly to steering commands. This early demo proved that perception and control could be unified without hand-engineered pipelines.
[Paper (NeurIPS 1988)](https://proceedings.neurips.cc/paper/1988/file/812b4ba287f5ee0bc9d43bbf5bbe87fb-Paper.pdf)

**2015 — Deep Visuomotor Policies**
Sergey Levine and colleagues revived the ALVINN idea with deep convolutional networks. Their *End-to-End Training of Deep Visuomotor Policies* learned to map images and robot state to joint torques, trained with guided policy search. This marked the first modern, scalable demonstration of end-to-end robot control.
[Paper (arXiv 1504.00702)](https://arxiv.org/abs/1504.00702)

**2022 — Gato**
DeepMind’s *A Generalist Agent* introduced Gato, a transformer trained across 600+ tasks: playing Atari, captioning images, chatting, and controlling a robotic arm. All tasks shared a single model and weight set, with observations and actions tokenized into one sequence. Gato showed that a generalist foundation model could unify control, perception, and language.
[Blog (DeepMind)](https://deepmind.google/discover/blog/a-generalist-agent/)

**2022–2023 — RT-1 and RT-2**
Google/Everyday Robots scaled the idea specifically for robotics. *RT-1* (Robotics Transformer) trained on 130k episodes of real robot data. *RT-2* connected vision-language pretraining with robot control, letting robots execute instructions grounded in web knowledge. These models pushed generalist policies into large-scale deployment.
[RT-1 blog](https://research.google/blog/rt-1-robotics-transformer-for-real-world-control-at-scale/)
[RT-2 blog](https://research.google/blog/rt-2-new-model-translates-vision-and-language-into-action/)

**2024–2025 — ACT and π₀**

* **ACT** (Action Chunking with Transformers) improves efficiency by predicting chunks of actions instead of step-by-step control, adding temporal abstraction.
* **π₀** is a vision-language-action foundation model using flow matching, trained across embodiments, pushing toward generalist policies that transfer across robot platforms.
  [ACT explainer](https://medium.com/%40deepkarkada/action-chunking-with-transformers-act-robot-policy-80519fc024bc)
  [π₀ paper (arXiv 2410.24164)](https://arxiv.org/abs/2410.24164)    





# Current Research Overview

A selection of recent papers that should give a good overview about currently ongoing research.
If you skim the project pages of the first 2-3 in every topic, you should be able to get a pretty good overview in 1-3h.


**Surveys**   

[Pure Vision Language Action (VLA) Models: A Comprehensive Survey](https://arxiv.org/pdf/2509.19012)   
[A Survey on Vision-Language-Action Models: An Action Tokenization Perspective](https://arxiv.org/abs/2507.01925)   
[Vision-Language-Action Models for Robotics: A Review Towards Real-World Applications](https://vla-survey.github.io/) (including interactive table)   

See this good early blog about core challenges and lessons learned:   
[What Matters in Learning from Offline Human Demonstrations for Robot Manipulation](https://ai.stanford.edu/blog/robomimic/)  

There are quite a number of "awsome-lists" about the topic, most seem abondoned though. 
These two seem very up to date:   
[awesome-embodied-vla/va/vln](https://github.com/jonyzhang2023/awesome-embodied-vla-va-vln)   
[Awesome World Models for Robotics](https://github.com/leofan90/Awesome-World-Models?tab=readme-ov-file)

And since progres is relying on analysis of hurdels: some critical arguments from Rodney Brooks:    
[Post: Why Today’s Humanoids Won’t Learn Dexterity](https://rodneybrooks.com/why-todays-humanoids-wont-learn-dexterity/)


**System**

[A System-Level View on Out-of-Distribution Data in Robotics](https://arxiv.org/abs/2212.14020)   
[Can We Detect Failures Without Failure Data? Uncertainty-Aware Runtime Failure Detection for Imitation Learning Policies](https://cxu-tri.github.io/FAIL-Detect-Website/)    
[Run-time Observation Interventions Make Vision-Language-Action Models More Visually Robust](https://aasherh.github.io/byovla/)   
[Vision-Language-Action Model and Diffusion Policy Switching Enables Dexterous Control of an Anthropomorphic Hand](https://vla-diffu-switch.github.io/)   
[Gemini Robotics 1.5: Pushing the Frontier of Generalist Robots with Advanced Embodied Reasoning, Thinking, and Motion Transfer](https://storage.googleapis.com/deepmind-media/gemini-robotics/Gemini-Robotics-1-5-Tech-Report.pdf)    


**Models**   

[VLA-Adapter: An Effective Paradigm for Tiny-Scale Vision-Language-Action Model](https://vla-adapter.github.io/)    
[The Better You Learn, The Smarter You Prune: Towards Efficient Vision-language-action Models via Differentiable Token Pruning](https://liauto-research.github.io/LightVLA/)

[3D FlowMatch Actor: Unified 3D Policy for Single- and Dual-Arm Manipulation](https://3d-flowmatch-actor.github.io/)   
[EmbodiedOneVision: Interleaved Vision-Text-Action Pretraining for General Robot Control](https://eo-robotics.ai/eo-1)   
[Unified World Models: Coupling Video and Action Diffusion for Pretraining on Large Robotic Datasets](https://arxiv.org/pdf/2504.02792)   
[FLOWER: Democratizing Generalist Robot Policies with Efficient Vision-Language-Action Flow Policies](https://intuitive-robots.github.io/flower_vla/)


**Data collection**  

[Do You Need Proprioceptive States in Visuomotor Policies?](https://statefreepolicy.github.io/)
[Guiding Data Collection via Factored Scaling Curves](https://factored-data-scaling.github.io/)   
[Predictive Red Teaming: Breaking Policies Without Breaking Robots](https://predictive-red-team.github.io/)   
[Counterfactual Behavior Cloning: Offline Imitation Learning from Imperfect Human Demonstrations](https://arxiv.org/abs/2505.10760)


**Data augmentaion**   

[RoboTransfer: Geometry-Consistent Video Diffusion for Robotic Visual Policy Transfer](https://horizonrobotics.github.io/robot_lab/robotransfer/)   
[RoCoDA: Counterfactual Data Augmentation for Data-Efficient Robot Learning from Demonstrations](https://rocoda.github.io/)   
[Accelerating Visuomotor Policies via Entropy-Guided Demonstration Acceleration](https://demospeedup.github.io/)   
See table in next chapter for more

**Real2X2Real**   

[RoboGSim: A Real2Sim2Real Robotic Gaussian Splatting Simulator](https://robogsim.github.io/)   
[RE3SIM: Generating High-Fidelity Simulation Data via 3D-Photorealistic Real-to-Sim for Robotic Manipulation](https://xshenhan.github.io/Re3Sim/)

[Real2Render2Real: Scaling Robot Data Without Dynamics Simulation or Robot Hardware](https://real2render2real.com/)   
[EmbodieDreamer: Advancing Real2Sim2Real Transfer for Policy Training via Embodied World Modeling](https://embodiedreamer.github.io/)   
[DreamGen: Unlocking Generalization in Robot Learning through Video World Models](https://research.nvidia.com/labs/gear/dreamgen/)

[EasyHeC: Accurate and Automatic Hand-eye Calibration via Differentiable Rendering and Space Exploration](https://github.com/ootts/EasyHeC?tab=readme-ov-file)   
See table in next chapter for more


**RL**

[What Can RL Bring to VLA Generalization? An Empirical Study](https://rlvla.github.io/)   
[VLAC: A Vision-Language-Action-Critic Model for Robotic Real-World Reinforcement Learning](https://vlac.intern-ai.org.cn/)   
[VLA-RL: Towards Masterful and General Robotic Manipulation with Scalable Reinforcement Learning](https://arxiv.org/abs/2505.18719v1)   
[ConRFT: A Reinforced Fine-tuning Method for VLA Models via Consistency Policy](https://cccedric.github.io/conrft/)


**Evaluation**   

[Is Your Imitation Learning Policy Better than Mine? Policy Comparison with Near-Optimal Stopping](https://arxiv.org/abs/2503.10966v4)   
[The Importance of A/B Testing in Robotics](https://research.google/blog/the-importance-of-ab-testing-in-robotics/)
[Evaluating Real-World Robot Manipulation Policies in Simulation](https://simpler-env.github.io/)  

[RoboArena: Distributed Real-World Evaluation of Generalist Robot Policies](https://robo-arena.github.io/)   
[A Careful Examination of Large Behavior Models for Multitask Dexterous Manipulation](https://toyotaresearchinstitute.github.io/lbm1/)   
 

**Benchmarks**   

[RoboTwin 2.0: A Scalable Data Generator and Benchmark with Strong Domain Randomization for Robust Bimanual Robotic Manipulation](https://robotwin-platform.github.io/)   
[LIBERO: Benchmarking Knowledge Transfer for Lifelong Robot Learning](https://libero-project.github.io/main.html)

**Simulation Frameworks**   
  
The two Benchmark papers above include simulation frameworks, especially RoboTwin is very easy to set up.   
[ManiSkill3: GPU Parallelized Robotics Simulation and Rendering for Generalizable Embodied AI](https://www.maniskill.ai/)   
[EmbodiedGen: Towards a Generative 3D World Engine for Embodied Intelligence](https://github.com/HorizonRobotics/EmbodiedGen)




# Data Augmentation and Generation

## 2D Visual Augmentations

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| Domain Randomization (2017) | Random textures, lighting, distractors in sim -> robust sim-to-real. | Successful real-world transfer from 0 real demos. | [Paper](https://arxiv.org/abs/1703.06907) | Input: simulator scene configs. Output: synthetic RGB frames/sequences. |
| GreenAug (2024) | Green screen during data collection -> chroma-key new backgrounds; cheap scene diversity. | Strong scene generalization with minimal effort. | [Code](https://github.com/hithqd/greenaug) | Input: RGB frames + mask. Output: RGB frames/video (drop-in for BC datasets). |
| ROSIE (RSS 2023) | Text-guided diffusion inpainting of objects/backgrounds for robot demos. | Novel task/object success; improved success detection. | [Paper](https://arxiv.org/abs/2302.11550) \| [Project](https://diffusion-rosie.github.io/) | Input: RGB frames + text. Output: inpainted frames/video. |
| RoboEngine (IROS 2025) | Task/physics-aware background replacement (Robo-SAM + diffusion). | +200% cross-scene generalization vs no-aug. | [Code](https://github.com/OpenRobotLab/RoboEngine) \| [Project](https://huggingface.co/datasets/OpenRobotLab) | Input: RGB frames; Output: augmented frames/video (ACT/DP ready). |
| Physically-based Lighting Augmentation (2025) | Inverse rendering -> relight demos; propagate via finetuned video diffusion. | 40.1% reduction of BC generalization gap across 6 lighting conditions (720 real evals). | [Paper](https://arxiv.org/abs/2508.01442) | Input: RGB video. Output: relit videos (convertible to BC loaders). |

## Viewpoint / Embodiment Augmentations

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| SPARTN / NeRF-based Corrective Aug (CVPR 2023) | Build NeRF from demos -> novel views + corrective action relabeling. | Reduced compounding error; improved stability. | [Paper](https://openaccess.thecvf.com/content/CVPR2023/papers/Zhou_NeRF_in_the_Palm_of_Your_Hand_Corrective_Augmentation_for_CVPR_2023_paper.pdf) | Input: multi-view/moving-cam video + poses. Output: rendered novel views + relabeled actions. |
| RoVi-Aug (2024) | Diffusion augmentation to change robot embodiment & camera viewpoint. | Enables cross-embodiment deployment. | [Code](https://github.com/rovi-aug/rovi-aug) | Input: RGB frames. Output: embodiment/viewpoint-augmented frames. |
| ERMV (Editing Robotic Multi-View 4D) (2025) | 4D multi-view sequence editor with epipolar motion-aware attention; edits propagate over time. | Improves robustness/generalization of VLA policies in cluttered scenes. | [Paper](https://arxiv.org/abs/2507.17462) \| [Code](https://github.com/IRMVLab/ERMV) | Input: multi-view RGB sequences. Output: edited multi-view videos. |

## Semantic & Dataset-Level Augmentations

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| RoCoDA (ICRA 2025) | Counterfactual edits + SE(3) transforms with action updates. | Better generalization to unseen textures/poses; emergent behaviors. | [Paper](https://arxiv.org/abs/2411.16959) \| [Project](https://rocoda.github.io/) | Input: trajectories (states/actions). Output: augmented trajectories with relabeled actions. |
| MT-ACT / RoboAgent (2024) | Semantic variations + action chunking for low-data IL. | 80-90% success; >40% better generalization. | [Project](https://blog.phospho.ai/dissecting-action-chunking-with-transformers-act-precision-imitation-learning-for-robotic-manipulation/) | Input: ****LeRobot**** dataset. Output: ACT-friendly chunks (****LeRobot**** persists). |
| pi0 (Pi-Zero) (2024) | VLA foundation model; diverse multi-robot data acts as augmentation. | Strong zero-shot; robust fine-tuning. | [Paper](https://arxiv.org/abs/2410.24164) \| [Project](https://huggingface.co/blog/pi0) \| [Code](https://github.com/Physical-Intelligence/openpi) | Input: ****LeRobot****/HF datasets. Output: policy fine-tunes with ****LeRobot**** loaders. |

## 3D / NeRF / Gaussian Splatting

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| DP3 (2024) | 3D point-cloud diffusion -> inherent view/rotation invariance. | ~55% higher than 2D baselines; 85% success with 40 demos. | [Paper](https://arxiv.org/abs/2403.03954) \| [Code](https://github.com/YanjieZe/3D-Diffusion-Policy) | Input: RGB-D/point clouds + proprioception. Output: action sequences. |
| RoboSplat (RSS 2025) | Edit 3DGS reconstructions (object, pose, lighting, robot, view). | One demo + aug -> 87.8% success (vs ~57% with 2D aug). | [Paper](https://arxiv.org/abs/2504.13175) \| [Project](https://yangsizhe.github.io/robosplat/) | Input: calibrated multi-view images. Output: augmented image sequences. |
| SplatSim (ICRA 2025) | Gaussian-splat renderer in sim for photorealistic training data. | Zero-shot sim->real ~86.25% success. | [Paper](https://arxiv.org/abs/2409.10161) \| [Project/Code](https://splatsim.github.io) | Input: reconstructed 3DGS/scene USD. Output: rendered RGB (+depth) rollouts. |
| RoboGSim (2025) | 3DGS real2sim2real digital-twin simulator with editing. | High-fidelity transfer; detailed metrics pending. | [Project](https://robogsim.github.io) | Input: multi-view captures -> 3DGS. Output: sim rollouts (RGB/depth/poses). |
| RL-GSBridge (ICRA 2025) | Mesh-based 3DGS synced to physics; real2sim2real. | Successful real-world grasping with zero extra real data. | [Paper](https://arxiv.org/abs/2409.20291) | Input: RGB-D scans -> 3DGS+mesh. Output: sim rollouts/policies. |
| RoboPearls (2025) | Editable video simulation from demo videos using 3DGS; object ops, relighting, language-driven edits. | Strong sim perf; real-robot generalization shown. | [Paper](https://arxiv.org/abs/2506.22756) \| [Project](https://tangtaogo.github.io/robpearls/) | Input: demo videos -> 3DGS. Output: editable synthetic sequences. |
| Discoverse (2025) | Open-source 3DGS+MuJoCo simulator for Real2Sim2Real. | +11–18.5% over SplatSim; +31.5% (ACT) / +29.3% (DP) with image aug. | [Paper](https://arxiv.org/abs/2507.21981) \| [Project/Code](https://air-discoverse.github.io/) | Input: assets (3DGS/Mesh/USD). Output: large-scale rollouts (RGB/Depth/State). |

## Real2Sim2Real Transfer Pipelines

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| RialTo (2024) | Scan real scene -> digital twin -> RL fine-tune -> redeploy. | ~+67% robustness to distractors/perturbations. | [Paper](https://arxiv.org/abs/2403.03949) | Input: real demos + scans. Output: sim fine-tuned policies for real. |
| RoboTransfer (2025) | Geometry-consistent multi-view video diffusion (depth/normal aware). | +33% (simple) to +251% (complex) task success. | [Paper](https://arxiv.org/abs/2505.23171) \| [Project](https://horizonrobotics.github.io/robot_lab/robotransfer/) | Input: multi-view videos (+depth/normals). Output: synthetic multi-view videos. |


## Temporal / Trajectory / Force Augmentations

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| Variable-Speed Teaching/Playback (2025) | Record demos at different speeds to capture richer force dynamics. | +55% success on force-involved tasks (pick, wipe). | [Paper](https://arxiv.org/abs/2412.08321) | Input: teleop trajectories (pos/force) at multiple speeds. Output: multi-rate trajectories. |
| DABI (2024) | Downsample high-freq telemetry -> ~10x more aligned samples. | Improved real-world success with Bi-ACT from 5 demos. | [Paper](https://arxiv.org/abs/2410.04370) | Input: high-rate robot states + images. Output: aligned lower-rate sequences. |
| DTW-IL / Action-Constrained IL (2025) | Generate surrogate demonstrations via MPC alignment using DTW distance. | Improves performance and sample efficiency across multiple tasks. | [Paper](https://arxiv.org/abs/2508.14379) \| [Code](https://github.com/NYCU-RL-Bandits-Lab/ACRL-Baselines) | Input: existing demos. Output: aligned surrogate trajectories. |

## Synthetic Rollout Generation (cross-listed)

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| RoboPearls (2025) | 3DGS-based editable video simulation from demo videos; full-length synthetic rollouts. | Shown sim + real-robot generalization improvements. | [Paper](https://arxiv.org/abs/2506.22756) \| [Project](https://tangtaogo.github.io/robpearls/) | Input: videos -> 3DGS. Output: synthetic sequences/episodes. |
| Discoverse (2025) | 3DGS+MuJoCo world for large-scale synthetic rollouts and R2S2R evaluation. | Up to +31.5% (ACT) / +29.3% (DP) from image aug; +11–18.5% over SplatSim baselines. | [Paper](https://arxiv.org/abs/2507.21981) \| [Project/Code](https://air-discoverse.github.io/) | Input: 3DGS/USD assets. Output: rollouts (RGB/Depth/State). |
| SplatSim (ICRA 2025) | Photorealistic 3DGS simulator to mass-generate training episodes. | ~86.25% zero-shot sim->real success with RGB policies. | [Paper](https://arxiv.org/abs/2409.10161) \| [Project/Code](https://splatsim.github.io) | Input: 3DGS scenes. Output: RGB(+depth) sequences. |
| RoboGSim (2025) | 3DGS digital twin; long multi-view rollouts with scene editing. | High-fidelity transfer (metrics pending). | [Project](https://robogsim.github.io) | Input: captures->3DGS. Output: multi-view rollouts. |
| RL-GSBridge (ICRA 2025) | Real2Sim via 3DGS; then train for long synthetic experience; deploy Real. | Zero-shot grasping success reported. | [Paper](https://arxiv.org/abs/2409.20291) | Input: RGB-D scans. Output: sim episodes/policies. |
| RoboTransfer (2025) | Geometry-consistent multi-view video diffusion -> long-horizon demo videos for training. | +33% to +251% gains depending on setting. | [Paper](https://arxiv.org/abs/2505.23171) \| [Project](https://horizonrobotics.github.io/robot_lab/robotransfer/) | Input: multi-view videos (+depth/normals). Output: synthetic videos. |
| ERMV (2025) | Multi-view 4D sequence editor -> long-horizon sequences with consistent geometry. | Improves generalization/robustness of VLA policies. | [Paper](https://arxiv.org/abs/2507.17462) \| [Code](https://github.com/IRMVLab/ERMV) | Input: multi-view sequences. Output: edited multi-view sequences. |
| NVIDIA Cosmos (2025) | World models for Physical AI; video generation and world simulation for augmentation/planning. | Intended for dataset augmentation, planning, and offline RL. | [Homepage](https://www.nvidia.com/en-us/ai/cosmos/) \| [Dev](https://developer.nvidia.com/cosmos) \| [Paper](https://arxiv.org/abs/2501.03575) | Input: prompts/conditioning video. Output: synthetic sequences. |
| Omniverse NuRec (2025) | Neural reconstruction libraries for RTX ray-traced 3DGS; capture->reconstruct->simulate USD digital twins. | Accelerates high-fidelity scene building for training. | [News](https://nvidianews.nvidia.com/news/nvidia-opens-portals-to-world-of-robotics-with-new-omniverse-libraries-cosmos-physical-ai-models-and-ai-computing-infrastructure) \| [Dev blog](https://developer.nvidia.com/blog/developers-build-fast-and-reliable-robot-simulations-with-nvidia-omniverse-libraries/) \| [Docs](https://docs.omniverse.nvidia.com/materials-and-rendering/latest/neural-rendering.html) | Input: multi-view captures -> USD/3DGS. Output: USD digital twins. |

## RL with Synthetic Rollouts - Offline RL (world-model/video)

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| NVIDIA Cosmos (2025) | Synthetic sequences from world models feed offline RL datasets and planning. | Positioned for RL dataset augmentation; robotics integration ongoing. | [Homepage](https://www.nvidia.com/en-us/ai/cosmos/) \| [Dev](https://developer.nvidia.com/cosmos) \| [Paper](https://arxiv.org/abs/2501.03575) | Input: prompts/conditioning. Output: sequences for offline RL. |
| RoboTransfer (2025) | Geometry-consistent multi-view videos usable for offline RL/IL training. | +33% to +251% gains in reported tasks (IL); applicable to offline RL. | [Paper](https://arxiv.org/abs/2505.23171) \| [Project](https://horizonrobotics.github.io/robot_lab/robotransfer/) | Input: multi-view videos. Output: synthetic videos for offline RL. |
| ERMV (2025) | Edited long-horizon multi-view sequences can populate offline RL buffers. | Reported IL/VLA gains; offline RL compatible. | [Paper](https://arxiv.org/abs/2507.17462) \| [Code](https://github.com/IRMVLab/ERMV) | Input: multi-view sequences. Output: edited sequences for offline RL. |

## RL with Synthetic Rollouts - Online RL (digital twin sim)

| Method (Year) | Summary | Reported Gains | Links | In/out data format |
|---|---|---|---|---|
| Sim-and-Real Co-Training (CVPR 2025) | Recipe: co-train in sim and real with shared replay/curriculum; sim data as augmentation. | Large real-robot gains (CVPR'25). | [ArXiv](https://arxiv.org/abs/2506.04058) \| [Project](https://co-training.github.io/) | Input: sim + real transitions. Output: RL policies (sim+real). |
| Discoverse (2025) | 3DGS+MuJoCo sim for scaled RL rollouts (R2S2R). | +11–18.5% over SplatSim; additional +29–31.5% with image aug. | [Paper](https://arxiv.org/abs/2507.21981) \| [Project/Code](https://air-discoverse.github.io/) | Input: assets (3DGS/Mesh/USD). Output: RL/IL rollouts. |
| SplatSim (ICRA 2025) | Photorealistic 3DGS sim for RL/IL loops. | ~86.25% zero-shot IL; supports online RL training. | [Paper](https://arxiv.org/abs/2409.10161) \| [Project](https://splatsim.github.io) | Input: 3DGS scenes. Output: RL rollouts/policies. |
| RoboGSim (2025) | 3DGS digital twins for RL training in edited scenes. | High-fidelity transfer (metrics pending). | [Project](https://robogsim.github.io) | Input: captures->3DGS. Output: RL rollouts. |
| RialTo (2024) | Digital twin + sim RL fine-tuning -> redeploy Real. | ~+67% robustness gains. | [Paper](https://arxiv.org/abs/2403.03949) | Input: real demos + scans. Output: RL-updated policies. |
| Omniverse NuRec (2025) | Neural reconstruction -> USD twins for Isaac RL pipelines. | Designed for Isaac/Omniverse RL data loops. | [News](https://nvidianews.nvidia.com/news/nvidia-opens-portals-to-world-of-robotics-with-new-omniverse-libraries-cosmos-physical-ai-models-and-ai-computing-infrastructure) \| [Dev blog](https://developer.nvidia.com/blog/developers-build-fast-and-reliable-robot-simulations-with-nvidia-omniverse-libraries/) | Input: multi-view captures -> USD/3DGS. Output: sim RL rollouts. |










