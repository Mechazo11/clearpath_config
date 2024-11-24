# clearpath_config
Clearpath Configuration YAML Parser

Find documentation on the Clearpath Configuration YAML and more about the Clearpath ROS 2 System on the [Clearpath Documentation](https://docs.clearpathrobotics.com/docs/ros/config/yaml) webpage.

# Configration Examples
Under the **_sample_** folder there are example configurations that can be used as the starting point of your `robot.yaml`.


# Unit Tests
All unit tests are written using **PyTest** following the [Good Integration Practices](https://docs.pytest.org/en/6.2.x/goodpractices.html#goodpractices).

Therefore, `clearpath_config_test` is a package that mirrors the `clearpath_config` package structure. Each file from `clearpath_config` that is to be tested should have a corresponding file with the same name and the suffix `_test.py`.

To run the tests:
```bash
cd .../clearpath_config
python3 -m pytest
```
> **PyTest** will automatically search for the suffix `_test` throughout the current directory and run the tests.


### Errors that have been solved

The following files causes ```TypeError``` due to the change in semantics of type hinting that may have been introduced in Python 3.10+. These files are

* lists.py
* hosts.py
* servers.py
* middleware.py

A sample of such error is shown below

* Type hinting for ```BaseConfig``` class

```bash
[generate_description-5] Traceback (most recent call last):
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/install/clearpath_generator_common/lib/clearpath_generator_common/generate_description", line 40, in <module>
[generate_description-5]     from clearpath_generator_common.common import BaseGenerator
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/install/clearpath_generator_common/lib/python3.10/site-packages/clearpath_generator_common/common.py", line 45, in <module>
[generate_description-5]     from clearpath_config.clearpath_config import ClearpathConfig
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/build/clearpath_config/clearpath_config/clearpath_config.py", line 30, in <module>
[generate_description-5]     from clearpath_config.system.system import SystemConfig
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/build/clearpath_config/clearpath_config/system/system.py", line 38, in <module>
[generate_description-5]     from clearpath_config.system.hosts import HostConfig, HostListConfig
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/build/clearpath_config/clearpath_config/system/hosts.py", line 31, in <module>
[generate_description-5]     from clearpath_config.common.types.list import ListConfig
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/build/clearpath_config/clearpath_config/common/types/list.py", line 45, in <module>
[generate_description-5]     class ListConfig(Generic[T, U]):
[generate_description-5]   File "/home/tigerwife/clearpath_simulator_harmonic_ws/build/clearpath_config/clearpath_config/common/types/list.py", line 64, in ListConfig
[generate_description-5]     _obj: T | U,
[generate_description-5] TypeError: unsupported operand type(s) for |: 'TypeVar' and 'TypeVar'
[ERROR] [generate_description-5]: process has died [pid 82323, exit code 1, cmd '/home/tigerwife/clearpath_simulator_harmonic_ws/install/clearpath_generator_common/lib/clearpath_generator_common/generate_description -s /home/tigerwife/clearpath_simulator_harmonic_ws/robot_yamls/ -r husky_a200_sample.yaml --ros-args -r __node:=generate_description'].
```
