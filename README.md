# Reticulum WebChat

A simple web based [LXMF](https://github.com/markqvist/lxmf) client for [Reticulum](https://github.com/markqvist/Reticulum).

## Features

- Supports sending to and receiving messages from [Sideband](https://github.com/markqvist/Sideband/) and [Nomadnet](https://github.com/markqvist/nomadnet).
- Supports receiving images sent from Sideband.
- Supports receiving file attachments sent from Sideband.

## How does it work?

- A python script (`web.py`) runs a Reticulum instance and a WebSocket server.
- The web page sends and receives lxmf packets encoded in json via the WebSocket.
- Web Browser -> WebSocket -> Python Reticulum -> (configured interfaces) -> (destination)

## How to use it?

You will need to clone the repo, and run `web.py`.

```
git clone https://github.com/liamcottle/reticulum-webchat
cd reticulum-webchat
pip install -r requirements.txt
python web.py
```

> NOTE: You should now be able to access the web interface at http://localhost:8000

## Using an existing Reticulum Identity

By default, a new identity is generated every time you run the script.

This is handy for quickly testing out the web ui, however you may want to use an existing identity when chatting to others.

To do this, you can provide a base64 encoded private key, like so;

```
python web.py --identity-private-key "GCN6mMhVemdNIK/fw97C1zvU17qjQPFTXRBotVckeGmoOwQIF8VOjXwNNem3CUOJZCQQpJuc/4U94VSsC39Phw=="
```

> NOTE: this is a randomly generated identity for example purposes. Do not use it, it has been leaked!

## TODO

- [ ] don't start Reticulum before cli args have been parsed
- [ ] allow passing in a custom Reticulum config file via cli args
- [ ] conversations/contacts list ui with unread indicators
- [ ] create/import/export identities in the web ui
- [ ] ui to configure custom name to send in announcement app data
- [ ] ui to view announcements, with names from app data
- [ ] support saving conversation history across page reloads
- [ ] send images from web ui
- [ ] send file attachments from web ui
- [ ] support for multiple (but separated) identities via the same websocket server
  - possibly allow multiple identities to simultaneously send/receive in multiple browser tabs?
