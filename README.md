Code written by Ryan Cecil as Research Assistant under Stacey Levine, Ph.D.
Duquesne University 2020


A CUDA/C++ implementation based on INRF equation found in the following paper:
Evidence for the intrinsically nonlinear
nature of receptive fields in vision by Marcelo Bertalmio,
Alex Gomez-Villa, Adrian Martin, Javier Vazquez-Corral, David Kane, & Jesus
Malo. Link: https://www.nature.com/articles/s41598-020-73113-0


The nonlinearity used in the INRF operator is Relu.


The code for this operator is compiled using bazel. 


To compile and use the operator. Download Tensorflow's Source code from: https://github.com/tensorflow/tensorflow
Then, add the INRF2d directory to the user_ops directory within Tensorflow. Place INRF2dBuild.sh at the top of the Tensorflow directory.
Ensure that you have a Bazel version compatible with your current version of Tensorflow installed.
Then, in the Tensorflow directory, call


bash INRF2Build.sh (INRF2dBuild.sh may have to be changed depending on the number of cores in your computer)


The compiled operator should be now stored as 

bazel-bin/tensorflow/core/user_ops/INRF2d_gpu.so


Now, take the directory, INRFOp and integrate it into the project that you wish to use the INRF operator for. In the INRFOp
directory, change

'{path to tensorflow}/tensorflow-r2.3/bazel-bin/tensorflow/core/user_ops/INRF2d_gpu0.so'


to contain the path to your tensorflow directory and the compiled operator. Then, the INRF2d operator 
should now be importable into your Python files using {from INRFOp import INRF2d}.

