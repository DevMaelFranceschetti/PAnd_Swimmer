# Swimmer environment study

## Tools developed

We developed two tools to help understanding the failure of RL algorithmes on Swimmer benchmark : the "Vignettes" and the "Gradient study".
The python code can be fount in directory "tools_developed".
Those two scripts are based on CEM-RL code from Aloïs Pourhot.
The "Vignette" tool is using random perturbation method to visualize the geometry of the objective function arount an actor.
The "Gradient study" tool displays the geometry of objective function on the direction followed by the algorithm, so the estimated gradient in case of TD3. 
Dot product indication helps to understang the behavior of the algorithme.

Those tools needs Mujoco and Swimmer to be installed, and the code based on CEM-RL to be present in the same directory than the tools.

### Vignette parameters

	--env, default='Swimmer-v2', type=str :  benchmark used
	--nb_lines, default=60, type=int : number of directions generated, good values : precise 100, less precise 60 or 50
	--minalpha, default=0.0, type=float : start value for alpha, good value : 0.0
	--maxalpha, default=10, type=float : end value for alpha, good value : large 120 or 100, around actor only 10
	--stepalpha, default=0.25, type=float, step for alpha in the loop, good value : precise 0.25 or 0.5 , less precise 2 or 3
	--eval_maxiter, default=1000, type=float : number of steps for the evaluation. Depends on benchmark used.
	--min_colormap, default=-10, type=int : min score value for colormap used (depend of benchmark used)
	--max_colorma, default=360, type=int : max score value for colormap used (depend of benchmark used)
	--basename, default="actor_td3_2_step_1_", type=str : base (files prefix) name of the actor pkl files to load
	--min_iter, default=1000, type=int : iteration number (file suffix) of the first actor pkl files to load
	--max_iter, default=200000, type=int : iteration number (file suffix) of the last actor pkl files to load
	--step_iter, default=1000, type=int : iteration number between two consecutive actor pkl files to load
	--base_output_filename, default="vignette_output", type=str : name of the output file to create
	--filename, default="TEST_5", type=str : name of the directory containing the actors pkl files to load
  
### Gradient study parameters

	--env, default='Swimmer-v2', type=str)
	--minalpha, default=0.0, type=float : start value for alpha, good value : 0.0
	--maxalpha, default=10, type=float : end value for alpha, good value : 10
	--stepalpha, default=0.5, type=float : step for alpha in the loop, good value : 0.25 ou 0.5
	--eval_maxiter, default=1000, type=float : number of steps for the evaluation. Depend on benchmark used.
	--min_colormap, default=-10, type=int : min score value for colormap used (depend of benchmark used)
	--max_colormap, default=360, type=int : max score value for colormap used (depend of benchmark used)
	--filename, default="TEST_5", type=str : name of the directory containing the actors pkl files to load
	--basename, default="actor_td3_2_step_1_", type=str : base (files prefix) name of the actor pkl files to load
	--min_iter, default=1000, type=int : iteration (file suffix) of the first actor pkl files to load
	--max_iter, default=201000, type=int : iteration (file suffix) of the last actor pkl files to load
	--step_iter, default=1000, type=int : iteration step between two consecutive actor pkl files to load
	--output_filename, default="gradient_output.png", type=str : name of the output file to create


## TD3 modification

We propose a modification of the initial settings of TD3 to achieve good performance on Swimmer: 
use discount = 1 and use start_steps = 20000, removing the update from TD3 before start_steps iterations.
See the paper for more details and explanations.
