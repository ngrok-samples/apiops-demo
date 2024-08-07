# APIOps demo for ngrok

This repo contains a simple Go app that creates an API that reponds with facts about desert tortoises.

This project is designed to be containerized and deployed to a Kubernetes cluster (see `deployment.yaml` and `gateway.yaml`), with ingress handled by the [ngrok Kubernetes Operator](https://github.com/ngrok/kubernetes-ingress-controller).

There is no database, so changes will not persist between executions.

To start the API:

```bash
git clone git@github.com:ngrok-samples/apiops-demo.git
cd apiops-demo
go get
go run main.go
```

## Usage

Get a single random fact:

```bash
curl \
  -X GET \
  http://localhost:5000/fact
```

Get all facts:

```bash
curl \
  -X GET \
  http://localhost:5000/facts
```

Add a new fact:

```bash
curl \
  -X POST \ 
  -H "Content-Type: application/json" \
  -d '{"fact": "This is a fact."}' \    
  http://localhost:5000/add
```
