<div align=center>
   <img width="180" height="150" src="images/logo.png"/>
   <h1>AV1_WARN</h1>
</div>
Some experimental records of experiments of choosing SEFCNN network depth, including whether to add SE block and layer selection of SE block.And I'd like to share some commands for training.

## Table of contents

- [Files](#Files)
- [Training](#Training)
- [Testing](#testing)

## Files
* training/NN_RUN.py : main training file.
* training/UTILS.py : defines some functions that need to be used in the training process, such as how to load the data set and how to calculate PSNR.
* training/WDSR.py : A TensorFlow-based implementation of [Wide Activation for Efficient and Accurate Image Super-Resolution](https://arxiv.org/abs/1808.08718) (WDSR), winner 
  of the [NTIRE 2018](http://www.vision.ee.ethz.ch/ntire18/) super-resolution challenge.
* training/NN_TEST.py : test the generalization power of the saved checkpoints.

## Training
* WDSR models can be trained with a pixel-wise loss function with NN_RUN.py.Default for WDSR is mean squared error.<br>
For example,

        python NN_RUN.py

    VDSRx15_SE_qp37.log is the file you want to redirect the output to, which you can change at will.

* if start with a checkpoint

        python VDSRTEST.py --model_path=./checkpoints/CHECKPOINT_NAME.ckpt

* The commands for launching tensorboard:

        tensorboard --logdir=logs
        
    The `--logdir` option sets the location point to the log directory of the job.If you still have difficulty,you can refer to the <br>
    https://www.jianshu.com/p/d8f9b0dfacdb.

## Testing

        python VDSRTEST.py >>./train_log/VDSRx15_SE_qp37_Test.log 2>&1


