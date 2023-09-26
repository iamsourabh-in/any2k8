docker build -t cloudnxt/nodeapp:v1 .
docker push cloudnxt/nodeapp:v1

kubectl apply -f .