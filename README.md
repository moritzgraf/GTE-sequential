Game Theory Explorer with Sequential Equilibrium Solver
=======================================================

This is a helper repository for running the Game Theory Explorer with a sequential equilibrium solver in a dockerized environment.

Our sequential equilibrium solver is described in detail here:

Moritz Graf, Thorsten Engesser, and Bernhard Nebel.
Symbolic Computation of Sequential Equilibria.
Proceedings of AAMAS 2024, to appear.


Prerequisites
-------------

Make sure that [Git](https://git-scm.com/), [Docker Engine](https://docs.docker.com/engine/install/), and [Docker Compose](https://docs.docker.com/compose/install/) are installed on your system.

The sequential equilibrium solver requires a free license for the Wolfram Engine, which can be obtained from <https://wolfram.com/engine/free-license/>.


Installation
------------

First, clone this repository and its submodules:

```
git clone --recurse-submodules https://github.com/tengesser/GTE-sequential.git
cd GTE-sequential
```

Then build the docker images and create and run the containers:

```
docker compose build
docker compose up -d
```

By default, the front-end listens on port 4200. You can access it locally using <http://localhost:4200>.

You can now use the following commands to stop and restart the containers:

```
docker compose stop
docker compose start
```


Activating the Wolfram Engine
-----------------------------

To use the sequential equilibrium solver, you must first activate the Wolfram Engine inside the docker container. Use the following command while the containers are running and follow the instructions carefully:

```
docker compose exec gte-backend wolframscript
```


Using the Sequential Equilibrium Solver
---------------------------------------

Open <http://localhost:4200> in your browser (Chrome and Firefox should work).

You can now edit the game tree (if you need help, see the YouTube video on the start screen). The sequential solver can be started by selecting **SE** in the top right corner and then clicking on **Solve**.


Troubleshooting
---------------

* Make sure you are accessing <http://localhost:4200> with http, not https.

* Make sure you are accessing <http://localhost:4200> from the local machine where you are running the docker containers. Running the solvers from a remote machine is currently not possible without manually changing some configuration files.

* When solving sequential equilibria, it may take a few seconds to connect to the Wolfram Kernel. If it takes more than a few seconds, there is a good chance that the Wolfram Engine was not properly activated.
