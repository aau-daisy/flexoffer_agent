# FlexOffer Agent (FOA)

The FlexOffer Agent (FOA) is an extensible and highly customizable software component of the Flexibility Modeling, Management, and Trading System. It is responsible for the generation and execution of FlexOffers for one or multiple flexible loads (both production and consumption). The FOA forms individual FlexOffers, delivers them to the aggregator software (FMAN), receives disaggregated schedules from the FMAN, and activates the flexible loads according to the received schedules.

This open source version of the FOA software was developed by researchers at the DAISY group, Department of Computer Science, Aalborg University, Denmark. Its performance has been successfully demonstrated in Cyprus, Germany, and Switzerland during the H2020 GOFLEX project (https://goflex-project.eu).

## Publications

If you use this software in your research, please cite:

- B. Neupane, L. Siksnys, T. B. Pedersen, R. Hagensby, M. Aftab, B. Eck, et al., "GOFLEX: Extracting, Aggregating and Trading Flexibility Based on FlexOffers for 500+ Prosumers in 3 European Cities," *Proceedings of the Thirteenth ACM International Conference on Future Energy Systems (e-Energy '22)*, pp. 361--373, 2022. [DOI](https://dl.acm.org/doi/abs/10.1145/3538637.3538865)

- L. Siksnys, T. B. Pedersen, M. N. Aftab, and B. Neupane, "Flexibility Modeling, Management, and Trading in Bottom-up Cellular Energy Systems," *Proceedings of the Tenth ACM International Conference on Future Energy Systems (e-Energy '19)*, pp. 335--346, 2019. [DOI](https://dl.acm.org/doi/abs/10.1145/3307772.3328296)

- L. Siksnys, T. B. Pedersen, and B. Neupane, "Modeling and Managing Energy Flexibility Using FlexOffers," *IEEE International Conference on Communications, Control, and Computing Technologies for Smart Grids (SmartGridComm)*, pp. 1--7, 2018. [DOI](https://ieeexplore.ieee.org/abstract/document/8587605)

## Installation using Docker

It is easy to set up and run the app with Docker. All you need to do is build a Docker image, then either run it in a container locally or push the image to a remote server and run it there. You must install `docker` and `docker-compose` both locally and on the remote server.

### Build Project
```bash
mvn clean install -DskipTests
```

### Build Docker Image
```bash
docker-compose build
```

### Push Docker Image to Remote Private Docker Registry
```bash
# one-time login to private docker registry
docker login repo.treescale.com

docker-compose push
```

### On Remote Server, Pull and Run Docker Image
```bash
# copy docker-compose.yml to remote server
scp docker-compose.yml <username>@<remote-server-address>:/remote/dir/path

# login to remote server
ssh <username>@<remote-server-address>
cd /remote/dir/path

# one-time login to private docker registry
docker login repo.treescale.com
docker-compose pull
docker-compose up -d
```

Alternatively, deploy directly from your local machine:
```bash
cat docker-compose.yml | ssh <username>@<remote-server-address> "docker-compose -f - pull"
cat docker-compose.yml | ssh <username>@<remote-server-address> "docker-compose -f - up -d"
```

### Connect/Disconnect to a Container
```bash
# attach to a running container
docker attach <container-name>

# detach from the running container
CTRL-p, CTRL-q
```

### Redeployment After Code Changes
```bash
docker-compose build --pull <service-name>
docker-compose up --no-deps -d <service-name>
```

### Remove Unnecessary Docker Images
```bash
docker system prune -f
```

## Acknowledgments

The project Generalized Operational FLEXibility for Integrating Renewables in the Distribution Grid (GOFLEX) has received funding from the European Union's Horizon 2020 research and innovation programme under grant agreement No 731232.
