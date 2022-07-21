
- **In stateless applications**, each event handled by your Kafka Streams application is processed independently of other events, and only stream views are needed by your application. In other words, your application treats each event as a self-contained insert and requires no memory of previously seen events. 

- **In statefull applicaions**, on the other hand, need to remember information about previously seen events in one or more steps of your processor topology, usually for the purpose of aggreating windowing, or joining event streams. These applications are more complex under the hood since they need to track additional data or state. 

