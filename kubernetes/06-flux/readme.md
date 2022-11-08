# Flux test with simple python API

Api created with fastAPI framework and uvicorn server

To start api type:

```bash
uvicorn main:app --reload
```

To check swagger go to URL

```
http://127.0.0.1:8000/docs
```

```
docker build -t python_test_k8_simple .
docker tag python_test_k8_simple:latest oskarp1993/test-and-fun:python_test_k8_simple
docker login
docker push oskarp1993/test-and-fun:python_test_k8_simple
```

Flux CLI install

```
brew install fluxcd/tap/flux
```

Export vars and check prerequsites:

```
export GITHUB_TOKEN=<your-token>
export GITHUB_USER=<your-username>

flux check --pre
```

Bootstrap flux:

```
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=infra-playground \
  --branch=main \
  --path=./kubernetes/06-flux/test-cluter \
  --personal
```
