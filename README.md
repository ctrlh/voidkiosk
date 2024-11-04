# voidkiosk

This is the white, vertical self service kiosk that sits in the lobby of CTRL-H. 

This kiosk is running a embedded linux OS built via Yocto, provided by [balena.io](https://www.balena.io/). The default image on the `voidkiosk` fleet is running a `Generic x86_64 (GPT)` image.

Commits to `main` will be automatically deployed to the kiosk via github actions.

## What's the setup?

Currently, there are two containers deployed.
- `voidkiosk` - serves a basic page on the loopback
- `browser` - a container running `X11` and `chromium`. You can see [here](https://github.com/balena-io-experimental/browser) for all the environment variables. These variables are managed on the Balena cloud dashboard under the variables section.

## Running locally

You will need `docker` and `docker-compose` installed locally, and just need to run `docker-compose up voidkiosk` to start the main container.

## Pushing to the kiosk

You will need to have the `balena-cli` installed locally, as well as access to the `ctrl-h` balena cloud organization. See [here](https://docs.balena.io/learn/getting-started/generic-amd64/nodejs/#install-the-balena-cli) for getting started instructions.

After you are authenticated, all you need to do is run `balena push ctrl_h/voidkiosk` and whatever is on your machine will be released and run on the kiosk. Remember that any commits to the `main` branch in this repo will auto-deploy to the kiosk. If you want to roll back to a previous version you have deployed, you can go into the device on Balena dashboard and `pin release` to whatever you had previously pushed.

## Need help or want to make something cool?

Hit up @nucleardreamer (Flynn) in Slack!