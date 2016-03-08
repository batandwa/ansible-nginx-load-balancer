Role Name
=========

Configures and executes an Nginx load-balancer Docker Container.

Requirements
------------

Requires Docker and Docker Compose to be setup on the host.

Role Variables
--------------

Sample defaults file:

```yaml
nginx_load_balancer:
    # The services to be configured.
    servers:
        # The name of the service. Will be used in the upstream
        # server directive.
        # This should be an array of the different services.
        - name: exe1
          upstream:
              # The upstream host.
              host: 1.2.3.4
              # The upstream port.
              port: 91
          domain: example.me
        - name: exe2
          upstream:
              host: 5.6.7.8
              port: 92
          domain: site2.example.me
```

```yaml
nginx_load_balancer:
    # Where the Docker Compose configuration files will be stored.
    path: "{{ ansible_user_dir }}/lb"

    container:
        # The source image.
        image: nginx
        # The name of the container.
        name: nginx-load-balancer
        # The ports that will be published by the container.
        ports:
            - "80:80"
            - "443:443"
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
          - role: angstwad.docker_ubuntu
            become: yes
          - role: batandwa.nginx-load-balancer

License
-------

MIT
