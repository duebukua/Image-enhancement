<div align=center>
   <img width="180" height="150" src="images/logo.png"/>
   <h1>AV1_WARN</h1>
</div>
Some experimental records of experiments of choosing SEFCNN network depth, including whether to add SE block and <br>
layer selection of SE block.And I'd like to share some commands for training.

## Table of contents

- [Files](#Files)
- [Training](#Training)
- [Testing](#testing)

## Files
* experiment_results : include the results of performance of the model by validation
* HM_MODELS/checkpoints : include model files created during the training period
* HM_MODELS/logs : event files, which contain the information that TensorBoard use to create the visualization.

## Training
* SEFCNN models can be trained with a pixel-wise loss function with train.py.Default for SEFCNN is mean squared error.<br>
For example,

        python VDSRUNK.py >>./train_log/VDSRx15_SE_qp37.log 2>&1

    VDSRx15_SE_qp37.log is the file you want to redirect the output to, which you can change at will.

* if start with a checkpoint

        python VDSRTEST.py --model_path=./checkpoints/CHECKPOINT_NAME.ckpt

* The commands for launching tensorboard:

        tensorboard --logdir=logs
        
    The `--logdir` option sets the location point to the log directory of the job.If you still have difficulty,you can refer to the <br>
    https://www.jianshu.com/p/d8f9b0dfacdb.

## Testing

        python VDSRTEST.py >>./train_log/VDSRx15_SE_qp37_Test.log 2>&1


