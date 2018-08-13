# Price History Database

## Specification

### Audience

Back End Software Developer

### Purpose

To build software that continuously tracks prices
of crypto assets over time.

Other applications will build upon the data once properly
stored.

A wide range of applications will tranform
the historical data into functioning systems that benefit
real people.

Real-time payment and conversion applications will use
the data to help people trade with each other.

Algorithmic market analysis tools and trading bots to
rapidly increase the value of crypto portfolios.

And more. This price history database will server as
a mine for future exploration and knowledge.

### Data Source

CoinMarketCap.com real-time price JSON API.

One API endpoint provides a complete list of all prices
provided.

### Storing Historical Data

API response as full raw JSON as returned by CoinMarketCap,
with a timestamp.

A new document should be stored every PRICE_INTERVAL, where
PRICE_INTERVAL is a variable length of time configured as an
environment variable at run time.

Data should be stored in a MongoDB document database, which
is configured with MONGODB_URL environment variable.


### Publishing Events

When new price data is available from CoinMarketCap, publish
and event including the data to a rabbitmq broker as configured
in the AMQP_URL environment variable.

A sysadmin running the price history database services
ought to be able to configure the both the AMQP_EXCHANGE,
and AMQP_ROUTING_KEY using environment variables.

### System Configuration

The service is designed to be run as a Docker container using
twelve-factor app operating architecture.

Configure a docker-compose file to run all three sercices,
the app container, mongodb, and rabbitmq:management.

A sysadmin must be able to run `docker-compose up` and see
the mongodb filling up with price history records, and messages
being published to the rabbitmq message exchange.

### Code Contribution

Source code is maintained on GitHub.com. New code is commited
first to separate branches. When features are complete a pull
request is made to merge the branch into the `master` branch. 

### Development Environment

Must support UNIX-style operating systems. Linux, Mac OSX.

### Programming Language

Golang, Node.js, or Scala preferred.

Please document the use of your chosen language's toolchain
such as dependency management and build tools.

