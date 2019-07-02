# my-linux-references

## Audio

Reference commands for working with audio

### Routing USB Mixer input to speakers (Pulse Audio)

```
pactl load-module module-loopback latency_msec=1      
```

To display the input in pulse audio
```
pavucontrol
```