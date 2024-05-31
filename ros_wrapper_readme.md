To run ros wrapper do the following: (nvidia-docker needed)

- edit camera intrinsics and obj name mappings

zs6d_configs/bop_eval_configs/cfg_ros_ycbv_inference_bop.json

git submodule update --init --recursive

xhost local:docker

- to build docker run 

docker build -t zs6d .

docker run -it --runtime nvidia --privileged -e DISPLAY=${DISPLAY}  -e NVIDIA_DRIVER_CAPABILITIES=all -v /home/v4r/demo/pose_estimators/ZS6D/:/code -v /tmp/.X11-unix:/tmp/.X11-unix --net host zs6d /bin/bash 

(test -> via glxinfo | grep "OpenGL version string" should be OpenGL version string: > 3.xx and show nvidia driver version)

 - inside docker run once

python prepare_templates_and_gt.py

- to start ros wrapper run

docker run -it --runtime nvidia --privileged -e DISPLAY=${DISPLAY}  -e NVIDIA_DRIVER_CAPABILITIES=all -v /home/v4r/demo/pose_estimators/ZS6D/:/code -v /tmp/.X11-unix:/tmp/.X11-unix --net host zs6d 


test

ros cant communicate with master

export ROS_MASTER_URI=http://10.0.0.143:11311
export ROS_IP=10.0.0.232
