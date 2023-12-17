# Running Blink locally

Now, when we have learned about the configuration, only one last step left - starting Blink locally

## Start Blink

In order to start blink you can simply execute to init the Blink instance. 
> By the default Blink will try to find `blink.yaml` in the current working directory, but you may want to have your config stored 
> having different name. You can specify path to the config file by setting `-c ${fileName}` flag

```Bash
blink start
```

Start with specific config file location

```Bash
blink start --config my_blink_conf.yaml
```

Or you can start Blink using Docker

```Bash
docker run -v blink.yaml:/blink.yaml usedatabrew/blink start
```

