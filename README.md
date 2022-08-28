# linux-i3-osx-yabai-moonlander-keymap
Source code for moonlander key map

## Start here:
https://github.com/zsa/qmk_firmware
https://github.com/zsa/qmk_firmware/tree/firmware21/keyboards/moonlander

but ignore qmk install directions and use docker container instead.

Edit the docker file to be the following:
```
FROM qmkfm/qmk_cli

VOLUME /qmk_firmware
WORKDIR /qmk_firmware

COPY . .

CMD qmk compile -kb all -km default
```

### Build the image and run the setup command
```bash
docker build \                                               
  -t qmk-firmware .

# Haven't tested this command, may need to just run /bin/bash and do setup/build from there
docker run -v $(pwd):/qmk_firmware -it /bin/bash -c 'qmk setup zsa/qmk_firmware -b firmware21'
```
### Build keybaord bin
```bash
docker build \                                               
  -t qmk-firmware .

# Haven't tested this command, may need to just run /bin/bash and do setup/build from there
docker run -v $(pwd):/qmk_firmware -it /bin/bash -c 'make moonlander:my-mapping'
```

