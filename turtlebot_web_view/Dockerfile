FROM rayman/ros-indigo-ros-base
MAINTAINER Jihoon Lee <jihoonlee.in@gmail.com>

# Install system dependencies
RUN apt-get update && apt-get install -y --force-yes tmux wget
RUN apt-get install -y --force-yes ros-indigo-turtlebot ros-indigo-rosbridge-suite ros-indigo-tf2-web-republisher
RUN apt-get install -y --force-yes ros-indigo-joint-state-publisher
RUN apt-get install -y --force-yes vim git python-wstool nodejs 

# Create userid for building and running ROS applications
RUN useradd -m ros
RUN adduser ros root

# Install turtlebot webview launcher
RUN cd /tmp; wget https://raw.githubusercontent.com/jihoonl/dockers/master/turtlebot_web_view/files/turtlebot_web.launch
RUN mv /tmp/turtlebot_web.launch /home/ros/

# Install turtlebot webview start script
RUN cd /tmp; wget https://raw.githubusercontent.com/jihoonl/dockers/master/turtlebot_web_view/files/start.sh
RUN mv /tmp/start.sh /home/ros/
RUN chmod +x /home/ros/start.sh

EXPOSE 9090

CMD ["/bin/bash", "/home/ros/start.sh"]
