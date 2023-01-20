# Install Kind
```sh
brew install kind
```

# Start your Kind cluster with three masters and workers
kind create cluster --config kind-config.yaml --name dev

# Confirm that you now have 6 nodes in your cluster
kubectl get nodes -o wide

# Install Calico using Manifest
 kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml

# Verify Calico installation
watch kubectl get pods -l k8s-app=calico-node -A

# Use ctrl+c to break out of watch

# Confirm that nodes are ready
kubectl get nodes -o wide

# Installing MetalLB
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.7/config/manifests/metallb-native.yaml
kubectl apply -f https://kind.sigs.k8s.io/examples/loadbalancer/metallb-config.yaml


# Clean up
kind delete cluster --name dev

