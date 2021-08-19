# NEST Desktop Singularity

Official Singularity container of NEST Desktop, a container of NEST Simulator is also provided.

Since Singularity runs only on Linux systems, it works in Linux only.

For more information, please see the
[User Documentation Page of NEST Desktop](https://nest-desktop.readthedocs.io)
as well as the
[User Documentation Page of NEST Simulator](https://nest-simulator.readthedocs.io).

## Preparation

#### Requirements

- Singularity 3.0 or higher

To install Singularity, please follow [the official guide of Singularity page](https://singularity.hpcng.org/docs).

#### Installation

##### 1. Clone a working copy from the repository:

```
git clone https://github.com/nest-desktop/nest-desktop-singularity
cd nest-desktop-singularity
```

##### 2. Register the command `nest-desktop-singularity`:

```
export PATH=$PATH:$PWD/bin
```

> | :information_source: **Info** |
> | ----------------------------- |
>
> Please keep in mind, that these changes are only temporary. If you would like to keep these permanently, you need to add the command to your `.profile` configuration file.
> `echo "export PATH=$PATH:$PWD/bin" >> ~/.profile`
> After that, you need to relogin (or restart), so that the changes are adopted.

##### 3a. Build the Singularity containers for NEST Desktop and NEST Simulator with `sudo`:

```
nest-desktop-singularity build
```

Then, it creates two image files (`nest-desktop.sif` and `nest-simulator.sif`) in the `images` subfolder.

#### 3b. Alternative: you can use fakeroot to build containers.

Add your username to the Singularity fakeroot config.

```
sudo singularity config fakeroot --add $USER
```

Then you can build containers with fakeroot (without `sudo`) in the future (e.g. when a container received updates). If you have not removed the containers before, you will be asked for confirmation before these are overwritten (`y` to confirm, `N` to abort). This is not necessary directly after the installation! If you copied this command and executed it thoughtlessly, no worries: This is not harmful, it is only inefficient to rebuild the freshly built containers.

```
nest-desktop-singularity build -f
```

## Usage

Start the instances of NEST Desktop and NEST Simulator:

```
nest-desktop-singularity start
```

Now, **NEST Desktop** is serving at [`localhost:8000`](localhost:8000)
<br/>
and **NEST Simulator** at [`localhost:5000`](localhost:5000).

#### Further methods

Get the status of both instances.

```
nest-desktop-singularity status
```

Stop both instances.

```
nest-desktop-singularity stop
```

Restart both instances.

```
nest-desktop-singularity restart
```

For more commands of Singularity, please consult the [official documentation](https://singularity.hpcng.org/user-docs/master/cli.html).

#### Execute a command for a single instance

Start a single container, e.g. NEST Desktop.

```
nest-desktop-singularity start nest-desktop
```

Restart a single container, e.g. NEST Simulator.

```
nest-desktop-singularity restart nest-simulator
```

### License

Licensed under the [MIT](LICENSE) license.
