# ros2_hik_camera

A ROS2 packge for Hikvision USB3.0 industrial camera

## Usage

```
ros2 launch hik_camera hik_camera.launch.py
```

## Params

- exposure_time
- gain

## Outgoing Information
- image
- camera data
Both are published

# Publisher
camera_pub_ is the publisher

# Image
The image data appears to be transported in whatever the standard ROS2 method is
via a publisher. It uses RGB8 encoding.
- type: sensor_msgs::msg::Image
- ENCODING: RGB8
- SIZE: height*width*3 (bytes presumably?) line 38
- HEADER.FRAMEID: "camera_optical_frame"
- HEADER.STAMP: this->now()
- STEP: out_frame.stFrameInfo.nWidth * 3

This line for some reason (line 92)
image_msg_.data.resize(image_msg_.width * image_msg_.height * 3);

# Camera Data

- type: sensor_msgs::msg::CameraInfo