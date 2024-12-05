# RL-for-Image-Classification

This detailed project document describes the implementation of an **Actor-Critic reinforcement learning (RL) approach for image classification** using the MNIST and CIFAR10 datasets. It provides a comprehensive overview of the problem definition, the algorithm used, and the working of the Actor-Critic method. 

### **Problem Definition**
The goal is to classify images from MNIST and CIFAR10 datasets using a custom RL environment (`MNISTEnv` and `CIFAR10Env`). The agent interacts with masked regions of images, takes actions to navigate the masked regions, and receives rewards based on its actions to learn classification.

---

### **Algorithm**
The **Actor-Critic method** combines policy-based (actor) and value-based (critic) approaches.  
- **Actor:** Learns a policy to map states to actions (probability distribution).  
- **Critic:** Estimates the value function for expected rewards.

---

### **Libraries and Tools**
- **Gym:** For RL environment creation.
- **PyTorch:** For neural network implementation.
- **Keras:** To load MNIST and CIFAR10 datasets.

---

### **Reinforcement Learning (RL) Mapping**
1. **States:** Observations (masked image regions).  
2. **Actions:**  
   - Move directions (UP, DOWN, LEFT, RIGHT).  
   - Classify the digit (output class probability).  
3. **Goal:**  
   - Maximize reward by correctly classifying the image.  
   - End the episode either when the image is classified or after 20 steps.  
4. **Rewards:**  
   - -0.1 for incorrect classification or time step penalty.  
   - Positive reward for correct classification.

---

### **Actor-Critic Workflow**
1. **Actor Network:** Outputs action probabilities based on the current state.  
2. **Critic Network:** Estimates value function using state and action.  
3. **Training Process:**  
   - Actor improves policy based on rewards and critic feedback.  
   - Critic minimizes value function estimation error.  

Both networks update weights via backpropagation to refine predictions and policy.

---

### **Environment Example (MNISTEnv)**
A simplified version of the MNIST environment (`MNISTEnv`) is provided, with the following features:
- **State:** Masked MNIST image regions.  
- **Action:** Navigate through image and predict digit class.  
- **Reward:** Encourages efficient and correct classification.  

**Environment Code:**
- The code snippet initializes an RL environment for MNIST, with methods to reset, step through actions, and provide observations.

---

### **Key Code Components**
1. **Environment Initialization:**  
   - Loads datasets.  
   - Masks regions and sets action/state spaces.

2. **Step Function:**  
   - Defines agent actions and transitions.  
   - Provides rewards and checks for episode termination.

3. **Reset Function:**  
   - Resets mask and initializes the agent's position.

---

### **Working of Actor-Critic in Image Classification**
1. **Actor Network:**  
   - Predicts class probabilities and navigation direction.  
   - Improves by learning from rewards provided by the critic.  

2. **Critic Network:**  
   - Provides value estimates of actions taken in specific states.  
   - Guides actor updates by predicting the expected return.

3. **Training Loop:**  
   - The agent observes states, takes actions, and receives rewards.  
   - Networks update iteratively to optimize classification performance.

---

### **Summary**
This project demonstrates how reinforcement learning, particularly the Actor-Critic algorithm, can be adapted for image classification. By combining exploration (navigation) and prediction (classification), the agent learns efficient policies to classify masked images from MNIST and CIFAR10 datasets. The innovative use of custom environments and RL principles in a supervised learning domain is a standout feature.
