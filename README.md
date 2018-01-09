# Get private-iota-testnet, iri, and iota-cli.
```
git clone https://github.com/schierlm/private-iota-testnet.git
unzip v1.4.1.6.zip
unzip cli-app-1.0.4.zip
```

# Create a snapshot.
```
cd private-iota-testnet
mvn package
java -jar target/iota-testnet-tools-0.1-SNAPSHOT-jar-with-dependencies.jar SnapshotBuilder  # This step is already done for you.
```

# Modify, compile, and run iri.
```
cd iri-1.4.1.6
cp ../Snapshot.txt src/main/resources
vim src/main/java/com/iota/iri/Snapshot.java  # Comment out L50-L82
mvn clean compile package
java -jar target/iri-1.4.1.6.jar --testnet -p 14700
```

# Run the coordinator to create the first milestone.
```
cd private-iota-testnet
java -jar target/iota-testnet-tools-0.1-SNAPSHOT-jar-with-dependencies.jar Coordinator localhost 14700
```

# Run iota-cli.
```
cd cli-app-1.0.4
npm install -g iota-cli-app
iota-cli
seed [YOUR SEED]
```
