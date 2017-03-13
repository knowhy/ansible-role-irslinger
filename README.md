ansible-role-irslinger
======================

Ansible role to build and install [ir-slinger](https://github.com/bschwind/ir-slinger) C library for sending infrared packets on the Raspberry Pi.

The variables under `/defaults/main.yml` describes the configuration I need to control my Yamaha AX-10 amplifier. This role won't help to figure out how to use irslinger but it can help you to persist your configuration.

Requirements
------------

None

Role Variables
--------------

The Broadcom pin number the signal will be sent on.

	out_pin: 27

The frequency of the IR signal in Hz.

	frequency: 38000

The duty cycle of the IR signal. 0.5 means for every cycle, the LED will turn on for half the cycle time, and off the other half.

	duty_cycle: 0.5

The duration of the beginning pulse in microseconds.

	leading_pulse_duration: 9000

The duration of the gap in microseconds after the leading pulse.

	leading_gap_duration: 4500

The duration of a pulse in microseconds when sending a logical 1.

	one_pulse: 562

The duration of a pulse in microseconds when sending a logical 0.

	zero_pulse: 562

The duration of the gap in microseconds when sending a logical 1.

	one_gap: 1688

The duration of the gap in microseconds when sending a logical 0.

	zero_gap: 562

1 = Send a trailing pulse with duration equal to "onePulse" 0 = Don't send a trailing pulse.

	send_trailing_pulse: 1

Names and codes to generate binaries. List of dictonaries.

	programs:
	-
		name: power
		code: "01011110101000011111100000000111"

Notes
-----

This role copies libs from pigpio from /usr/local/lib to /usr/lib. I guess this is not the best way to deal with it but I haven't got time to investigate why irslinger does not pick up the pigpio libs from /usr/local/lib

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: knowhy.irslinger }

License
-------

GNU AGPLv3

Author Information
------------------

This role was created in 2017 by Henrik Pingel.
