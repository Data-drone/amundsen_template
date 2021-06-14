# amundsen_template
Amundsen setup to go with ml platform

```bash

# start command with ml-platform
docker-compose -f docker-compose.yml -p amundsen_module up

```

## Making Elastisearch run properly in low disk situation

```bash

# Otherwise the low and high watermarks at 85%+ can stop things running
curl -XPUT -H "Content-Type: application/json" http://localhost:9200/_cluster/settings -d '{ "transient": { "cluster.routing.allocation.disk.threshold_enabled": false } }'

```

## Understanding Amundsen

- Need to dive a bit more into what makes Amundsen tick but roughly:

-- Neo4J databuilder extractor needed to extract metadata from source systems.
-- Neo4J -> Elastisearch extractor job need to extract the metadata found by the Neo4J job into Elastisearch for searching

