<div style="text-align: center;" align="center">
  <img src="../docs/figs/sense-base-framework.svg" alt="cdi-hub" width="600"/>
  <h1> :robot: SENSE-BASE Framework </h1>
</div>

**SENSE-BASE** is a ROS2-based framework for multimodal biosignals from EEG, EoG, ECG, and depth cameras.

## :school_satchel: Getting started
* :octocat: Clone SENSE-BASE repositories under `sense-base` path and refer to the [CONTRIBUTING](../CONTRIBUTING.md) guideline for detailed instructions on contributing to the project.
```
# For example:
git clone git@github.com:sense-base/sense_eeg.git
```
* :computer: [Setting up ROS2 with docker container](https://github.com/sense-base/base/tree/main/docs/docker)

* :nut_and_bolt: Run and debug. Open a terminal into the loaded container in VSCode using the dev containers extension, and run
```
colcon build --symlink-install
source install/setup.bash
ros2 launch eeg_publisher mock_publisher_launch.py
```

On a different terminal, run
```
source install/setup.bash
ros2 topic list
ros2 topic echo /eeg/raw
ros2 bag record /eeg/raw
ros2 bag info <bag_file_name> (e.g., `rosbag2_data_time`)
ros2 bag play <bag_file_name>
rqt_graph
```

## Setup environment with pyenv
Install Python Environment (3.10 or higher recommended):

### Using pyenv
```bash
pyenv install 3.10.17  # Or any >=3.10 version you prefer
```

```bash
pyenv virtualenv 3.10.17 sense_EEG-env
pyenv local sense_EEG-env
pip install -e ".[dev]"
```

## Using uv
```
uv venv --python 3.12
source .venv/bin/activate
uv pip install -e ".[test,learning,model_optimisation]"
uv pip list --verbose
pre-commit run -a
```

### Run Pre-commit Hooks
```bash
pre-commit run --all-files
```

