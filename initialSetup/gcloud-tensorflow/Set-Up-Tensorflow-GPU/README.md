# Set-Up-Tensorflow-GPU
## CuDNN and Cuda version are tested with Tesla K80, P100 GPU only! - Nvidia driver version 384.13

In this guide, I will show a 6-steps process of quickly setting up and running the Tensorflow GPU on google cloud instance. The same process is also applicable for any other virtual machine instances deployed on any other cloud computing platform such as AWS, Paperspace, Digitial Ocean etc.

Step-1;
- Start your VM instance and log-in to it using your terminal.
- `cd <any_folder>`.
- Simply create files as in this folder, namely `script_1.sh`, `script_2.sh` and `requirements.txt` and paste in the appropriate commands in each file to their respective files.
- Don't forget to give executable permission for script files -> `chmod a+x script_1.sh script_2.sh`

Step-2. From your `<any_folder>` directory, run the LINUX shell file "script_1.sh" using command as shown below:

`./script_1.sh`

Step-3. Download https://developer.nvidia.com/compute/machine-learning/cudnn/secure/v7.0.5/prod/9.0_20171129/cudnn-9.0-linux-x64-v7 by logging into your nvidia-developer account(if you don't have one, create one! - it's free!!)
- Make sure you have the file in your `<any_folder>` folder.
- Don't worry about extracting the compressed file. It is taken care by `script_2.sh`

Step-4. From your `<any_folder>`, run the following command:

`./script_2.sh`

Step-5. Run `source activate tf` . Then once you enter the conda environment, run `pip install -r requirements.txt`. 

Step-6. Verify that tensorflow-gpu is being used by your instance. Follow the below steps:
- Run `python`
- `import tensorflow as tf`
- `sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))`
- You should see your GPU information along with the total memory available and memory free, etc
