### Unpack private-iota-testnet, iri, and iota-cli
```
unzip private-iota-testnet.zip  # Downloaded from https://github.com/schierlm/private-iota-testnet.git
unzip v1.4.1.6.zip
unzip cli-app-1.0.4.zip
```

### Build private-iota-testnet and Create a Snapshot
```
cd private-iota-testnet
mvn package
java -jar target/iota-testnet-tools-0.1-SNAPSHOT-jar-with-dependencies.jar SnapshotBuilder  # This step is already done for you.
```

### Modify and Build iri
```
cd iri-1.4.1.6
cp ../Snapshot.txt src/main/resources
vim src/main/java/com/iota/iri/Snapshot.java  # Comment out L50-L82
mvn clean compile package
```

### Install iota-cli
```
cd cli-app-1.0.4
npm install -g iota-cli-app
```

### Run the Two Nodes in Different Terminals
```
# Terminal a
cd nodes/a
./iri

# Terminal b
cd nodes/b
./iri
```

### Run the Coordinator and Tell Node A to Create the First Milestone
```
cd nodes
./coordinator localhost 14700
```

### Run iota-cli and Connect to Node B
```
iota-cli
: node localhost:24700
: minWeightMagnitude 14
```
