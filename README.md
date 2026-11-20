# Raspberry PI Monitoring with Grafana

This folder holds the configuration-as-code for the **Raspberry PI that is monitored with Prometheus and graphed with Grafana**. It uses [Ansible] wrapped in a convenient [suitcase],
called [`promethesible`](./promethesible).

It does **not** deploy the application itself.

## Prerequisites

* A Raspberry Pi running **Any OS**.

## TL;DR

```sh
./promethesible -i
```

## What `-i` (`--install`) configures

[`roles/Dashboard/tasks/setupOs.yml`](./roles/Dashboard/tasks/setupOs.yml):

* sets the timezone to `Europe/Zurich` and the locale to `fr_CH.UTF-8`;
* stops and disables `lighttpd`, the local web server FullPageOS ships with;
* writes `https://dash.fsd.epfl.ch` to `/boot/firmware/fullpageos.txt`.
  **This file is the only place that decides which page the TV shows.**

Reboot the Pi afterwards (`ssh pi@<ip> sudo reboot`) for Chromium to pick up
the URL.

[Ansible]: https://www.ansible.com
[suitcase]: https://github.com/epfl-si/ansible.suitcase
[FullPageOS]: https://github.com/guysoft/FullPageOS
[Raspberry Pi Imager]: https://www.raspberrypi.com/software/
