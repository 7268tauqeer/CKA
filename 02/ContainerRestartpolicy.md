Docker containers will not start when they exit or when docker daemon in restarted

Container Restart policy:
    no : Do not automatically restart the container, this is default policy
    on-failure: which docker container exits with an error i.e. exits with a no-zero exit code
    unelss-stopped: Restart the container unless it is explicitly stopped or Docker service inself is stopped or restarted
    always: always restart container