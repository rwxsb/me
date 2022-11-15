## Kafka Serializing and Deserializing
I was trying to build Producer/Consumer for a project, since I was lazy first used Confluent Cloud Connectors to MongoDB however then consuming and deserializing with dotnet-avro library causes problem. I should write a Producer that will also reduce the bills from Confluent Cloud

Since object in DB is directly used as a schema it is hard to Deserialize it into dotnet type, so I have to write the producer using dotnet-avro lib w/ Avro serializtion

#kafka #avro

references:
- https://github.com/ch-robinson/dotnet-avro


