Add function to ~/.bashrc:

```bash
function killTcpListen () {
  kill -9 $(lsof -sTCP:LISTEN -i:$1 -t)
}
```

Pull changes: `source ~/.bashrc`

And use it: `killTcpListen 3000`

https://stackoverflow.com/questions/4075287/node-express-eaddrinuse-address-already-in-use-kill-server/46276685#46276685
