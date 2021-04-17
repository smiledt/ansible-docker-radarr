Docker-Radarr
=========

A role to spin up a Radarr docker container. This role was heavily inspired by (and all credit goes to) [Calvin Bui](https://calvin.me)'s other roles. This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. Any of these defaults can be overwritten by using the vars role directory. 

    radarr_name: radarr

This is the name of the container. 

    radarr_image: linuxserver/radarr

The image container. By default this pulls from linuxserver.io.

    radarr_ports:
     - 7878:7878
     - 8787:8787

These are the exported ports of the container.

    radarr_config_directory: /opt/radarr

This is the directory that config files will be stored. This is mapped to /config in the container. 

    radarr_movie_directory: /mnt/media/movies

This is the directory that Radarr will move movies and managed files to. Usually we want this directory on some sort of media network storage. This is mapped to /movies inside the container.

    radarr_movie_directory: /mnt/media/movies

This is where files will be placed for Radarr to manage, either via a download client or manually. This is mapped to /completed inside the container.

    radarr_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    radarr_docker_additional_options:
      restart_policy: unless-stopped

Another dictionary, this time of additional options for the container. By default, this sets the container to start on boot unless it was previously stopped. 

    radarr_config:
      ApiKey: "abc123"
      UrlBase: "example.com"
      LaunchBrowser: "False"
      AnalyticsEnabled: "False"

This is not currently in use - the applicable code is commented out in the task. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the Radarr Container.
      hosts: rr
      become: true
      roles:
      - role: docker-radarr

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/