# Python custom notebook image example

This folder shows how to use a custom image in a notebook.

# Docker registry setup

The first step is to set up a Docker registry.
This [section](https://docs.datamechanics.co/docs/packaging-code#set-up-a-docker-registry-and-push-your-image) of the Data Mechanics docs shows how it's done.

# Push the image

The justfile in this repo pushes the Docker image to a Docker registry.
Use your own with:

```bash
just image_name='<URI/of/your/docker/image>' update
```

# Create config template

Create a [config template](https://docs.datamechanics.co/docs/configuration-management#config-templates) that references the image we just built and that will be used as a kernel for the notebook.

Go to the "Templates" section of the Data Mechanics Platform UI and create a config template with a name like `custom-notebook` with the following content:

```json
{
  "type": "Python",
  "sparkVersion": "3.0.0",
  "image": "<URI/to/your/docker/image>",
  "imagePullPolicy": "Always"
}
```

# Run the notebook

Then [run a Jupyter server locally](https://docs.datamechanics.co/docs/jupyter-notebooks):
```bash
jupyter notebook --gateway-url=https://<your-cluster-url>/notebooks/ \
    --GatewayClient.auth_token=<your-user-key> \
    --GatewayClient.request_timeout=600
```
and create a new notebook from template `customer-notebook`.

You should be able to access the code that we packaged in the Docker image:
```python
import src.hello
src.hello.hello()
```
```
'hello from the Docker image!'
```
