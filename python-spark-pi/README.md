# Python Spark Pi Docker dev flow example

This folder proposes an example of dev flow using Docker, as presented in https://docs.datamechanics.co/docs/packaging-code .

```bash
Available recipes:
run_cluster                 --  Run on Data Mechanics
run_locally                 --  Run locally with code auto-update
run_registry_image_locally  --  Rebuild image and run locally
update                      --  Build the image and push it to the registry
```

Variables:
```bash
api_key     := "null"
cluster_url := "https://demo.datamechanics.co"
image_name  := "gcr.io/dm-docker/python-spark-pi:dev"
```

## Example

To run the image on the demo cluster:

```bash
just api_key=<your_api_key> run_cluster
```
