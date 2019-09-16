# Benchmark
This project is a POC for to test performance of various gateway.

## How To Run Locally

### Build Backend
To build docker images for backend run following command:

```sh
mvn clean install -N
```

```sh
mvn clean install -Ddocker
```

## How To Run on Kubernetes

Run any one of the stack

### SCG 
#### Run
```
kubectl apply -f k8s\SCG
```
#### Delete
```
kubectl delete -f k8s\SCG
```

### Zuul 
#### Run
```
kubectl apply -f k8s\Zuul
```
#### Delete
```
kubectl delete -f k8s\Zuul
```

## Kubernetes expose

### Locally

Using post-forward

```
kubectl port-forward svc/zuul 7777:7777
```

Logs
```
kubectl logs -f <pod>
```

## Endpoints

### Test Service (REST)

Endpoints:

 - `/address/company` returns a text/plain response.
 - `/users/{id}` returns a JSON response.
 - `/users/multiple{?ids}` returns a JSON array.
 - `/users/headers` returns a MultiValueMap headers map that the service received.

## Testing

### WRK

Install based on OS [here](https://github.com/wg/wrk/wiki/Installing-wrk-on-Linux)

To test:

```
wrk -t 10 -c 200 -d 30s http://localhost:8888/address/company
```

### AB (Apache Benchmark)

To test:

```
ab -n 20000 -c 200 http://localhost:8888/address/company
```


