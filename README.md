# http4k-kodein-exposed
This project is a sample service using [http4k](https://www.http4k.org/) (with Netty) and 
[Exposed](https://github.com/JetBrains/Exposed) ORM. At some point it will also leverage [Kodein](https://kodein.org/di/) 
for dependency injection. The ultimate goal is to incorporate a similar sample service into []() to test the performance 
various frameworks.

### Build and Run
1. `docker-compose up`
2. `./gradlew run`

### cURL Requests (w/ jq)
#### Create
To create an Offering, you must supply `name`, `tasting_notes`, `description`, `url`, and `roaster_name`.
```
curl -X POST 'http://localhost:8080/api/v1/offerings' -H 'Content-Type: application/json' -d '{                                                                            130 ↵
  "name": "Ethiopia Kochere & Yirgacheffe Jabanto",
  "tasting_notes": "Blueberry, Chocolate, Honey",
  "description": "The Jabanto group formed in 2017, after changes in the Ethiopian coffee policy permitted smallholder farmers to be able to directly export and sell their coffees. The group has worked hard to build an enterprising business from scratch and their commitment to careful harvesting and processing each year results in some of our favorite offerings. This year’s production of Jabanto Natural Sundried tastes like blueberry, chocolate, and honey.",
  "url": "https://counterculturecoffee.com/shop/coffee/jabanto-natural-sundried",
  "roaster_name": "Counter Culture Coffee"
}' | jq
```

#### Get All
```
curl 'http://localhost:8080/api/v1/offerings' | jq
```

#### Get By ID
```
curl 'http://localhost:8080/api/v1/offerings/{id}' | jq
```

#### Update
Only `description` is updatable.
```
curl -X PUT 'http://localhost:8080/api/v1/offerings/{id}' -H 'Content-Type: application/json' -d '{ "description":"Updated Description" }' | jq
```

#### Delete
```
curl -X DELETE 'http://localhost:8080/api/v1/offerings/{id}' | jq
```