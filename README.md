# Overview of the Thesis
Undergraduate senior thesis for Tommy Hosmer, supervised by Dr. Tarek Zohdi. 

If pdf is not rendering please try: https://drive.google.com/file/d/1kn8Ydk4duxIg33kNxVRkrCHRW9YHpwTN/view?usp=share_link

# Outline
The goal of the project was to develop an artificial neural network (ANN) to model synthetic data representing data center energy consumption and couple it to a a physics-based model for the flow of energy among multiple devices (i.e. an energy management system or EMS). Two genetic algorithms were employed, one to optimize the parameters of the neural network that aren't tuned during the gradient descent of TensorFlow. The second genetic algorithm searched for the optimal flow of energy on each timestep of the physical simulation. The ANN predicted energy consumption as a function of energy delivered to the system, the system's desired energy level, and the energy generated on the previous step; it replaced the need for another physics-based model to determine each device's energy consumption. 

# Motivation and Methods
This project served as a culmination of two graduate courses, Mechanical Engineering 249: Machine Learning Tools for Modeling of Energy Transport and Conversion Processes and Mechanical Engineering C201: Modeling and Simulation of Advanced Manufacturing Processes. I wanted to take techniques I learned from both courses, applied machine learning and physics-based modeling coupled with design optimization, and apply them to a problem relevant to climate change and the growth of data centers. 

In the physics-based model, I sought to optimize the flow of energy between multiple interconnected devices that minimizes line losses and dependence on a centralized power source, formed a non-convex space that I sought to iterate through on each time step. This motivated the use of the genetic algorithm, which performed a rapid search through the design space to mitigate energy loss. This work was building on previous research by Dr. Zohdi in https://doi.org/10.1007/s00466-022-02212-8.

The development of the ANN is often left to careful experiments with hyperparameters to determine the optimal structure that can deliver robust and accurate predictions. This can be costly in terms of time and attention and once again I used a genetic algorithm, this time to determine the optimal set of parameters that aren't tuned during gradient descent in the TensorFlow library. These parameters are the neurons per layer, dropout rates, and value ranges for the weights of the neural network. Tuning the ANN with a genetic algorithm was inspired by work done in https://doi.org/10.1007/s00466-022-02216-4.

The ANN replaced what could have been a computationally expensive CFD solver for the heat transfer in each device to determine the energy needed to cool the device, such as https://doi.org/10.1007/s00466-022-02152-3. 

# Results
The cost function for the EMS decreased by 66% with the implementation of the genetic algorithm. The genetic algorithm reduced the cost for the ANN by 12%.
