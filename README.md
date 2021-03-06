# home-assistant-apps
[Home Assistant](https://home-assistant.io) apps based on [AppDaemon](https://home-assistant.io/docs/ecosystem/appdaemon/). A sample configuration for all apps is located here:
[sample_config/apps.yaml](sample_config/apps.yaml)

AlarmSystem
============

The idea is to notify if an intrusion is detected. The system arms itself if all device_trackers are marked away and disarms if any device_tracker is back home. For me the system works perfectly without manual intervention. In order to allow baby sitters or other guest without residents you can enable a guest mode. The xiaomi aqara gateway can be integrated to play alarm sounds or flash lights.

This system work with any light system (should support color) and with any sensors who report on/off values. I have tested it with xiaomi hub, sensors, buttons. Some disscusion can be found in the [forum](https://community.home-assistant.io/t/alarmsystem-with-appdaemon/31312)

Key | Description | Default
------------ | ------------- | -------------
device_trackers | list of tracked devices (for auto arming / disarming) | []
armed_home_sensors | list of sensors to monitor (like doors, motion, sensors) in case you are home | []
armed_away_sensors | list of sensors to monitor (like doors, motion, sensors) in case you are away | []
alarm_control_buttons | list of buttons to control (single click arm_away, double click disarm, long pres arm_home) | []
alarm_lights | list of lights to flash (red color for triggered alarm) | []
vacation_control | not used (tbd)
guest_control | input boolean to configure a babysitter mode which does not auto arm | None
silent_control | input boolean to mute the alarm sound | None
alarm_volume_control | input_number for alarm volume | None
info_volume_control | input_number for input volume | None
xiaomi_aqara_gw_mac | xiaomi_aqara_gw_mac to play ringtones | None
notify_service | script to call for notification | None
notify_title | title parameter for script | AlarmSystem triggered, possible intruder


HeatSaver
============

This app controls the temperature based on the opening and closing of windows/doors and some global control settings. Tt saves heating by lowering the thermostat if you are away or a window is open. 

Key | Description | Default
------------ | ------------- | -------------
device_trackers | list of tracked devices | []
door_window_sensors | list of sensors to monitor (like doors, motion, sensors) | []
climate_controls | list of cliamte controls | []
guest_control | input boolean to configure a babysitter mode which does not shut down heating | None
vacation_control | input boolean to configure a vacaction mode which lowers temperatures | None
offset_temperature | offset temperature | 0
home_temperature_control | slider to control temperature of the state at home | None
away_temperature_control | slider to control temperature of the state at away | None
vacation_temperature_control | slider to control temperature of the state at vacation | None
open_temperature_control | slider to control temperature of the state at open | None
