# openHAB 2.0 configuration

This is a base set of configuration. The rules are depending on a naming convention.

## conf

**Items** are organized by rooms. If you need a new room, copy&paste an existing one an search%replace the room prefix (e.g. bath -> kitchen)

**Rules** are organized by function. For example all heating stuff in the heating.rules

## Logging

set log level and view logs in the console:

	log:set DEBUG org.eclipse.smarthome.model.script.bath
	log:tail

Add log level for custom logger. Edit file: *userdata\etc\org.ops4j.pax.logging.cfg*

	log4j.logger.org.eclipse.smarthome.model.script.bath = DEBUG
	log4j.logger.org.eclipse.smarthome.model.script.heating = DEBUG
	log4j.logger.org.eclipse.smarthome.model.script.simulate = DEBUG

