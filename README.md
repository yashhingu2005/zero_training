# Training ZERO in Isaac Lab

This repository documents the workflow I used to train my custom quadruped robot, **ZERO**, using Isaac Lab. The goal is to provide a straightforward pipeline that others can follow, from a Fusion 360 CAD model to a trained reinforcement learning policy.

> **Note:** This is the workflow that worked for me. There are other ways to achieve the same result, but the resources below are the ones I personally used.

---

## Workflow

```text
Fusion 360 CAD
        │
        ▼
 Export URDF
        │
        ▼
 Import into Isaac Sim
        │
        ▼
 Convert to USD
        │
        ▼
 Create Robot Configuration
        │
        ▼
 Create Training Environment
        │
        ▼
 Train with Isaac Lab
        │
        ▼
 Trained Policy (.pt)
```

---

# 1. Install Isaac Sim & Isaac Lab

Start by following NVIDIA's official documentation:

- Isaac Sim Documentation
- Isaac Lab Documentation

The installation process that worked for me is documented here:

https://github.com/marcelpatrick/IsaacSim-IsaacLab-installation-for-Windows-Easy-Tutorial

---

# 2. Export Your Robot from Fusion 360

The original Fusion2URDF exporter is no longer compatible with newer versions of Fusion 360.

I used this updated fork instead:

https://github.com/yashhingu2005/fusion2urdf_for_updated_fusion

Basic process:

- Finish your CAD model.
- Add and configure all joints.
- Verify joint limits and joint axes.
- Name all links and joints clearly.
- Export the robot as a URDF.

---

# 3. Import into Isaac Sim

- Import the exported URDF.
- Verify that all joints move correctly.
- Check joint orientations.
- Adjust collisions if necessary.
- Save the robot as a USD asset.

---

# 4. Isaac Lab Setup

After creating the USD asset:

- Create the robot configuration (`*_cfg.py`).
- Create the training environment.
- Configure observations.
- Configure actions.
- Implement rewards.
- Configure the PPO training parameters.

---

# 5. Training Checklist

Before starting training, I recommend checking the following:

- [ ] Robot imports successfully.
- [ ] All joints move correctly.
- [ ] Joint limits are correct.
- [ ] Robot stands without instability.
- [ ] Collision meshes are correct.
- [ ] Self-collisions behave as expected.
- [ ] Actuator settings are configured.
- [ ] Robot configuration is complete.
- [ ] Environment configuration is complete.
- [ ] Reward function is implemented.
- [ ] Observations are implemented.
- [ ] Actions are implemented.
- [ ] Reset logic works.
- [ ] PPO configuration is complete.

---

# 6. Train the Policy

Run the Isaac Lab training command for your environment.

Training checkpoints and logs will automatically be saved in the `logs/` directory.
<img width="948" height="578" alt="Recording 2026-07-14 011459" src="https://github.com/user-attachments/assets/53bf691b-9b1b-49b2-b778-045baa8e2ba0" />

---

# Learning Resources

The main inspiration for this project was Lychee AI's excellent Isaac Lab tutorials.

YouTube Channel:
https://www.youtube.com/@LycheeAI

Video:
https://youtu.be/tQziqSx-F80

---

# Acknowledgements

- NVIDIA Isaac Sim
- NVIDIA Isaac Lab
- Lychee AI
- Fusion2URDF
- Everyone contributing to open-source robotics ❤️
