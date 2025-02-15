Actions:
- Docker Container Action : Runs on Linux only
- Composite Action 
- JavaScript Action
- Actions are defined in action.yaml file
- runs: Defined the type of action
- args/env: to pass values to action

Docker container action
- Consistent: All its dependencies is in a image
- Any language
- Slower as it takes time to retrive the image and then build the container
- Linux only

```runs:
    using: docker
    image: imageurl```


JavaScript Action
- Run directly on the runner
- Executed in NodeJS
- Faster
- Support all OS
- Node versions are associated with runners. so you should update your action when your runner image is updated
- Supports TS

```runs:
    using: node16
    main: dist/index,js
    ```

Composite Action
- Wrapper for other steps and Actions
- Shell parammeter is required in composite action

```runs:
    using: composite
    steps: 
    ```