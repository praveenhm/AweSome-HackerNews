#### Kuberenete gcloud

git clone https://github.com/GoogleCloudPlatform/kubernetes-engine-samples
  
  
   17  gcloud container clusters get-credentials my-first-cluster-2 --zone us-west4-a
   18  docker build -t gcr.io/ancient-booster-298019/hello-app:v1 $PWD
   19  gcloud docker -- push gcr.io/ancient-booster-298019/hello-app:v1
   20  kubectl create deployment hello-app --image=gcr.io/ancient-booster-298019/hello-app:v1
   21  kubectl expose deployment hello-app --type="LoadBalancer" --port 8080
   22  kubectl get service hello-app --watch
   23  kubectl scale deployment hello-app --replicas=4
   24  kubectl get deployment
   25  kubectl get pods
   26  sed -i -e 's/1.0.0/2.0.0/g' main.go
   27  docker build -t gcr.io/ancient-booster-298019/hello-app:v2 $PWD
   28  gcloud docker -- push gcr.io/ancient-booster-298019/hello-app:v2
   29  kubectl set image deployment/hello-app hello-app=gcr.io/ancient-booster-298019/hello-app:v2 && echo 'image updated'
