The main goal of this project is to provide a practicable linux daemon, which monitors the cpu temperature and adjusts fan speed according to a linear translation temperatur => fan speed

The first versions are written in perl with the capability of writing syslog messages

The daemon needs the eeepc-linux eee.ko module to work properly. It will not alter your fsb. It just reads temperature and writes to fan\_speed and fan\_manual.

**Version 0.2 released yesterday**

  * New SIGTERM,SIGKILL Events to restore hardware control

  * More comfortable spinning control