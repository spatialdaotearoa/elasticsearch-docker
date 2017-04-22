# elasticsearch-docker

Adapted from https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html to use docker-compose v2.1, and include an image for Kibana.

Note, as per the linked instructions, you will need to ensure your `sysctl` `vm.max_map_count` is at least 262144 on the **host** (i.e. your machine) before starting up:

```
sysctl vm.max_map_count=262144
```

```
docker-compose -f docker-compose.dev.yml build
docker-compose -f docker-compose.dev.yml run
```

Test it's working (default password for user `elastic` is `changeme`):

```
curl -u elastic http://127.0.0.1:9200/_cat/health
```

With Kibana running too, visit `localhost:5601/` (and `localhost:5601/status`) to interface with Elasticsearch visually.

## Notes

- Something I found useful for upgrading `docker-engine` (needs to be ≥1.12.0): https://gist.github.com/indykish/a6facea4748dc578abbaf2b09065ead5
- I also had to upgrade `docker-compose` (just reinstalled with `pip`)
