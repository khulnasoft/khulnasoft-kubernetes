# Clean up

Steps to perform a clean up of our deployments, services and volumes used in our environment.

## Delete the cluster

To delete your Khulnasoft cluster just use `kubectl delete -k envs/<ENVIRONMENT>` from this repository directory. (being <ENVIRONMENT> one of `EKS` or `local-env`)

## Delete the persistent volumes manually.

Since we use `reclaimPolicy: Retain` in the storage class definition you must delete volumes manually if you want to clean these as well.


```
ubuntu@k8s-control-server:~$ kubectl get persistentvolume
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS        CLAIM                                                         STORAGECLASS             REASON    AGE
pvc-024466da-f7c5-11e8-b9b8-022ada63b4ac   10Gi       RWO            Retain           Released      khulnasoft/khulnasoft-manager-worker-khulnasoft-manager-worker-1             khulnasoft-storage                      6d
pvc-b3226ad3-f7c4-11e8-b9b8-022ada63b4ac   30Gi       RWO            Retain           Bound         khulnasoft/khulnasoft-elasticsearch-khulnasoft-elasticsearch-0               khulnasoft-storage                      6d
pvc-fb821971-f7c4-11e8-b9b8-022ada63b4ac   10Gi       RWO            Retain           Released      khulnasoft/khulnasoft-manager-master-khulnasoft-manager-master-0             khulnasoft-storage                      6d
pvc-ffe7bf66-f7c4-11e8-b9b8-022ada63b4ac   10Gi       RWO            Retain           Released      khulnasoft/khulnasoft-manager-worker-khulnasoft-manager-worker-0             khulnasoft-storage                      6d
```

```
ubuntu@k8s-control-server:~$ kubectl delete persistentvolume pvc-b3226ad3-f7c4-11e8-b9b8-022ada63b4ac
```

Once these steps are completed, our Khulnasoft deployment will have been removed from the Kubernetes environment.
