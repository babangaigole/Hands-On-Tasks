version: "2.1"
services:
  yelb-ui:
    image: mreferre/yelb-ui:0.10
    depends_on:
      - yelb-appserver
    ports:
      - 8080:80
    environment:
      - UI_ENV=prod

  yelb-appserver:
    image: mreferre/yelb-appserver:0.7
    depends_on:
      - redis-server
      - yelb-db
    ports:
      - 4567:4567
    environment:
      - RACK_ENV=prod

  redis-server:
    image: redis:4.0.2
    ports:
      - 6379:6379

  yelb-db:
    image: mreferre/yelb-db:0.6
    ports:
      - 5432:5432
