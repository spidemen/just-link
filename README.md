# Just Link

JustLink is an Oracle and simplifies the communication with blockchains. This initial implementation is intended for use and review by developers,
and will go on to form the basis for JustLink's decentralized oracle network. Further development of the JustLink Node and JustLink Network will happen here,
if you are interested in contributing please contact us, email: team@justlink.io

## Build

1. Install MySQL (v5.7)

2. Install Java

3. Install NodeJS (>=10.0)

4. Build
```
./gradlew clean build
```

## Run node

After build successfully, `node-{version}.jar` will be generated in dir `node/build/libs`.

1. Start MySQL first. Initializing the tables using the latest sql file in path `node/src/main/resources/db/migration`.

2. Start the JustLink node:

```
java -jar node-v1.0.jar --key key.store 2>&1 &
// customize some configuration
java -jar node-v1.0.jar --server.port=8081 --spring.profiles.active=dev --key key.store 2>&1 &
```

Note:
- The `key.store` file contain the private key that this node use. The format refer to: `node/src/main/resouces/key.store.template`.
- You can just put a new `application.yml` or `application-{ENV}.yml` in the working dir to replace the default spring config file.
- There is a set of demo contracts deployed on `nile` network, the node will listen on `nile` when starting node with the command: `--env dev`

## Project Structrue

JustLink is is a monorepo containing several logicaly separatable and relatable projects.

- `tvm-contracts` - smart contracts
- `node` - the core JustLink node
- `@node/webapp` - the webapp for JustLink node

