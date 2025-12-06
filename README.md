<p align="center">
  <a href="https://github.com/somethingsimade/roblox-ws">
  	<img width="600" src="https://raw.githubusercontent.com/somethingsimade/roblox-ws/refs/heads/main/full.png">
  </a>
</p>

*credits to [rosocket](https://github.com/RoSocket/rosocket) for the logo html for the readme*

---

roblox-ws is a Roblox WebSocket system that runs **entirely on the client**, with no use of exploits or injection.

## When to use (comparing to other methods)

| Use | Other WebSocket scripts | roblox-ws |
|:--------|:--------------|:---------------|
| **Client WebSockets** |X No|✓ Yes|
| **Server WebSockets** |✓ Yes|X No|
| **Rate limited** |✓ Yes|X No|
| **Vulnerable** |X No|⚠️Yes (Read below)|

## Why is it vulnerable?
As every good thing comes with risks, `roblox-ws` works by running **a separate process** on your computer to bridge the network connection, which means that **the data passed between the client and the process is not sandboxed**

A vulnerability in the process could be exploited by a Roblox experience, which could expose you to unauthorized code execution, **you should only use this while on a trusted Roblox experience**. This also means that your **IP address** can be accessed by the client, **ONLY** enter trusted experiences while using this.

Using this with Roblox exploits, along with risking a ban, it can abuse the way the way this method moves data from Roblox to the local process, exposing you to more vulnerabilities.

If managed correctly, you can safely use the method.

# **IF YOU ARE AWARE OF A VULNERABILITY ON THIS PROJECT, REPORT IT IMMEDIATELY IN: https://github.com/somethingsimade/roblox-ws/issues**

## Is it released yet?
No, private

## Does it work on live games, or only studio?
Both.

## Is it supported by Fishstrap, Bloxstrap or other mods?
You will be able to customize the path of the client when released.

## Why isn't it released if it fully works?
I'm making sure I can code it myself, instead of relying on AI. I don't want to release something I have put zero effort into, aside from the idea I had.

## How to use?

```lua
local WebSocket = require(game:GetService("ReplicatedStorage").roblox_ws).WebSocket
--// ^ Or whatever the path to your module is, just paste main.lua inside

local ws = WebSocket.connect("ws://localhost:8080")

ws.OnMessage:Connect(function(message)
	print(message)
end)

ws.OnClose:Connect(function()
	warn("Closed")
end)

ws:Send("Hello World!")
```

## Why is the WebSocket table returned separately when you require the module
Because, although optional, HTTP will be supported by the module.

## Can you *create* websockets using the script?
Not yet, but is a planned feature, for now you can just connect

## Will this end up as another failed project, because it was just a concept?
No, it actually works

## Disclaimer

This is an independent, unofficial project and is not affiliated with, endorsed by, or sponsored by Roblox Corporation. WebSocket is an IETF standard (RFC 6455). “Roblox” is a trademark of Roblox Corporation. Other trademarks are the property of their respective owners.
