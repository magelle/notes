# Elixir Phoenix Commanded 

## Mix
Run a specific env config
```
MIX_ENV=prod mix phx.server
```

## Creating the database

Create the docker container
```
sudo docker run --name train_train_postgres -e POSTGRES_PASSWORD=traintrain -p 5432:5432 -d postgres
```

Run the docker container
```
sudo systemctl start docker.service
sudo docker start train_train_postgres
```

Create the database
```
sudo docker exec -ti train_train_postgres bash
psql -U postgres -W -d train_train_dev
create role train_train_user WITH LOGIN createdb PASSWORD 'train_train_password';

create database train_train_dev OWNER = train_train_user;
create database train_train_test OWNER = train_train_user;
```

## Initiate the Phoenix project 

Create the phoenix poject
```
mix phx.new --umbrella --database postgres train_train
cd train_train_umbrella
mix ecto.create
mix phx.server
iex -S mix phx.server
```

Create the json resource
```
cd app/train_train_web
mix phx.gen.html Fleet Train trains name:string number_of_seats:integer
```

Add the route
```
resources "/trains", TrainController
```

## Ecto

Create the database
```
mix ecto.drop
mix ecto.create
mix ecto.migrate
```

## Commanded

Dispatch a command
```
TrainTicket.Application.dispatch(%TrainTicket.Commands.Create{uuid: "6d406027-5271-413d-bc8b-77c9a45cc93d", name: "My Aggregate"})
```

Create the eventstore database : 
```MIX_ENV=dev mix do event_store.create, event_store.init```

### Projections using https://github.com/commanded/commanded-ecto-projections

