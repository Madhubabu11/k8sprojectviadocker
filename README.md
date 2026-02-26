# k8sprojectviadocker
iron&amp; steel industry simple website project

+++==================================+++
deployment.yml
+++===================================+++

apiVersion: apps/v1
kind: Deployment
metadata:
  name: notes-app-deployment
  namespace: notes-app  # make sure this namespace exists
spec:
  replicas: 2
  selector:
    matchLabels:
      app: notes-app
  template:
    metadata:
      labels:
        app: notes-app
    spec:
      containers:
        - name: notes-app
          image: vikashbabu/steel-app
          ports:
            - containerPort: 3000

+++================================================+++            
Service.yml

apiVersion: v1
kind: Service
metadata:
  name: notes-app-service
  namespace: notes-app
spec:
  selector:
    app: notes-app
  ports:
    - port: 3000
      targetPort: 3000
  type: ClusterIP
~                      
+++================================================+++
Namespace.yml
apiVersion: v1
kind: Namespace
metadata:
  name: notes-app
~                   
+++================================================+++
