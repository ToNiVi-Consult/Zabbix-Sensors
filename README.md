Simple bash script which returns {#CHIP}, {#SENSOR} and {#UNITS} macros as well as {#MIN}, {#MAX} and {#CRIT} when its defined by lm-sensor. That macros should be used with native sensor type zabbix-agent items. Script depends on lm-sensors to work.

Should work with older zabbix (but I haven't opportunity to test it). Basic template attached as an example.

Installation:

    Check that paths to egrep, cut, tr and sensors are valid.
    Run script as zabbix user, check that it returns valid output
    Drop userparameter_sensors.conf in zabbix_agentd.conf.d directory.

Example output:

{
	"data":[
		{"{#CHIP}":"fam15h_power-pci-00c4", "{#SENSOR}":"power1", "{#UNITS}":"W", "{#NAME}":"power1"},
		{"{#CHIP}":"k10temp-pci-00c3", "{#SENSOR}":"temp1", "{#UNITS}":"°C", "{#NAME}":"temp1", "{#MAX}":"70.00", "{#CRIT}":"70.00"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"temp2", "{#UNITS}":"°C", "{#NAME}":"MB Temperature", "{#MAX}":"45.00", "{#CRIT}":"75.00"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"temp1", "{#UNITS}":"°C", "{#NAME}":"CPU Temperature", "{#MAX}":"60.00", "{#CRIT}":"95.00"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"fan2", "{#UNITS}":"RPM", "{#NAME}":"Chassis Fan Speed", "{#MIN}":"600.00"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"fan1", "{#UNITS}":"RPM", "{#NAME}":"CPU Fan Speed", "{#MIN}":"600.00"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"in3", "{#UNITS}":"V", "{#NAME}":"+12V Voltage", "{#MIN}":"10.20", "{#MAX}":"13.80"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"in2", "{#UNITS}":"V", "{#NAME}":"+5V Voltage", "{#MIN}":"4.50", "{#MAX}":"5.50"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"in1", "{#UNITS}":"V", "{#NAME}":"+3.3V Voltage", "{#MIN}":"2.97", "{#MAX}":"3.63"},
		{"{#CHIP}":"atk0110-acpi-0", "{#SENSOR}":"in0", "{#UNITS}":"V", "{#NAME}":"Vcore Voltage", "{#MIN}":"0.80", "{#MAX}":"1.60"}
	]
}
