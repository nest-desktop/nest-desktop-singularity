# NEST Desktop Singularity

Singularity container for NEST Desktop and NEST Simulator.

Because of the Singularity, it works only in Linux.

For more information, please see the
[User Documentation Page of NEST Desktop](https://nest-desktop.readthedocs.io)
as well as the
[User Documentation Page of NEST Simulator](https://nest-simulator.readthedocs.io).

## Preparation

#### Requirements

- Singularity 3.0 or higher

To install Singularity, please follow [the official guide of Singularity page](https://sylabs.io/docs/).

#### Installation

##### 1. Clone the working copy from repository:

```
git clone https://github.com/nest-desktop/nest-desktop-singularity
cd nest-desktop-singularity
```

##### 2. Register the command `nest-desktop-singularity`.

```
export PATH=$PATH:$PWD/bin
```

##### 3a. Build Singularity containers for NEST Desktop and NEST Simulator with `sudo`.

```
nest-desktop-singularity build
```

Then, it creates two image files (`nest-desktop.sif` and `nest-simulator.sif`) in `images` folder.

#### 3b. Alternative: you can use fakeroot to build containers.

Add your username to the Singularity fakeroot config.

```
sudo singularity config fakeroot --add $USER
```

then you can build containers with fakeroot (without `sudo`).

```
nest-desktop-singularity build -f
```

## Usage

Start the instances of NEST Desktop and NEST Simulator

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

For more commands of Singularity,

#### Execute command for a single instance

Start NEST Desktop instance.

```
nest-desktop-singularity start nest-desktop
```

Restart NEST Simulator instance.

```
nest-desktop-singularity restart nest-simulator
```

### License [MIT](LICENSE)
