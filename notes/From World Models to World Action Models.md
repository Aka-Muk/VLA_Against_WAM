**New Words** 
    - *Taxonomy* : Arranging things into groups(formal) . 
    - *PID* : Proportional Integral Derivative 
    - *Latent Dynamics Model* : First reduce the world view into a latent (minimized) state - then compute future state . 
        - *Latent Vector* : Compact array of numbers to capture essential features , structure and meaning of complex data . 
    - *Encoder* : Something to break down the inout feed into individual components (ex : pixels)
    - *RGB - D* : Includes depth in addition to RGB . Is not exactly loght dependent due to depth sensor (active IR) . 
    - *End-Effector* : Controlling commands directed specifically at the tool or hand attached to the tip of a robotic arm rather than controlling each individual arm joint . (Using inverse kinematic solver)
    - *Neural - Symbolic Operator Model* : Hybrid AI architecture to combine neural networks (statistical) with symbolic logic (mathematical operators , structured knowledge graphs) . 
    - *Semantically* : Filtering data , tokens or words based on 'essential meaning' . 
    - *Transition Model* : Also called dynamics model is a component in ml to decide how state changes from one moment to the next . 


## World 
Set of task relevant entities - includes the robot and its environment (of interest and ambient) . 

## Design Space View 
    *Observation Space WM*  
        Predicting future observation directly in the observation space under given action . 
        RGB images are most common representations - easy to collect , inexpensive and widely available sensors . However for decision making use RGB D or multiple view RGB images . - By latent dynamics model or interface actions . 

        *Monocular Vision Models* :
            Convert RGB into RGB D by following principles of convering parallel lines , vanish points , relative object sizes , blurring , lighting . 
        
    *State - Space Observation WM* 
        Unlike OSWM which may be forced to model the unnecessary visual details rather than task-relevant evolution , SSWM first abstract observations into a structured state representation and then predict future evolution . 
        Here p(θ) may or may not be a neural network - it may be a physics simulator engine or a neural - symbolic operator model . 

        Latent State Model : 
            Observation encoded into latent vectors by neural networks . We can either 
                - Get the current latent state from state domain 
                - Or directly get the future latent state from current domain . 
        Point Track  Model : 
            rm irrelevant background information while preserving the explicit motion information of the scene . 
            Predict how individual physical points on objects and surfaces move through space from frame to frame . 
        Physical State Model : 
            World is represented bny physical variables of position , velocities , contact state , friction coefficients so on . 
            Sim is tuned by reconstructing the target scene in 3D , then aligning the simulated env with real scene by replaying real interaction trajectories and optimizing dynamics . 

## World Action Models 
    *Imagine then Execute Format* 
        2 step paradigm . Treated as separate modules . 
        First step is to generate visual subgoals 
        Second step is to (by inverse dyanbmics) convert visual subgoals into robot actions . 
    *Video-feature-conditioned action Paradigm* 
        No need to render complete future state video , we just use exact spatial features to condition an action prediction module . 
    *Joint Video-Action Modelling*
        Pretrain on large scale visual data --> modify output space to produce robot actions --> adapt the model on robot trajectories with output labels . 
        Improves consistency since everything is learned on a shared representational space . 
        Difficult to align optimizational objectives and handling high dimensional visual generation and action prediction . 
    *Auxillary video prediction* 
        It treats future frame generation as a side (auxillary) task while robot is under training . 
        This will force better understanding by predicting future cideo and also runtime is minimized since robot acts instantly without wasting time rendering future video frames . 
        Since video branch is removed during execution , the robot does not have future plan to double check . 


**Troublesome Concepts** 
    - [ ] xt+1 ∼ pθ (· | o0:t, at) <-- whatever this is ...