# Khulnasoft Kubernetes

[![Slack](https://img.shields.io/badge/slack-join-blue.svg)](https://khulnasoft.com/community/join-us-on-slack/)
[![Email](https://img.shields.io/badge/email-join-blue.svg)](https://groups.google.com/forum/#!forum/khulnasoft)
[![Documentation](https://img.shields.io/badge/docs-view-green.svg)](https://documentation.khulnasoft.com)
[![Documentation](https://img.shields.io/badge/web-view-green.svg)](https://khulnasoft.com)

Deploy a Khulnasoft cluster with a basic indexer and dashboard stack on Kubernetes.

## Branches

* `master` branch contains the latest code, be aware of possible bugs on this branch.
* `stable` branch on correspond to the last Khulnasoft stable version.


## Documentation

## Amazon EKS development

To deploy a cluster on Amazon EKS cluster read the instructions on [instructions.md](instructions.md).
Note: For Kubernetes version 1.23 or higher, the assignment of an IAM Role is necessary for the CSI driver to function correctly. Within the AWS documentation you can find the instructions for the assignment: https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html
The installation of the CSI driver is mandatory for new and old deployments if you are going to use Kubernetes 1.23 for the first time or you need to upgrade the cluster.

## Local development

To deploy a cluster on your local environment (like Minikube, Kind or Microk8s) read the instructions on [local-environment.md](local-environment.md).

## Directory structure

    ├── CHANGELOG.md
    ├── cleanup.md
    ├── envs
    │   ├── eks
    │   │   ├── dashboard-resources.yaml
    │   │   ├── indexer-resources.yaml
    │   │   ├── kustomization.yml
    │   │   ├── storage-class.yaml
    │   │   ├── khulnasoft-master-resources.yaml
    │   │   └── khulnasoft-worker-resources.yaml
    │   └── local-env
    │       ├── indexer-resources.yaml
    │       ├── kustomization.yml
    │       ├── storage-class.yaml
    │       └── khulnasoft-resources.yaml
    ├── instructions.md
    ├── LICENSE
    ├── local-environment.md
    ├── README.md
    ├── upgrade.md
    ├── VERSION
    └── khulnasoft
        ├── base
        │   ├── storage-class.yaml
        │   └── khulnasoft-ns.yaml
        ├── certs
        │   ├── dashboard_http
        │   │   └── generate_certs.sh
        │   └── indexer_cluster
        │       └── generate_certs.sh
        ├── indexer_stack
        │   ├── khulnasoft-dashboard
        │   │   ├── dashboard_conf
        │   │   │   └── opensearch_dashboards.yml
        │   │   ├── dashboard-deploy.yaml
        │   │   └── dashboard-svc.yaml
        │   └── khulnasoft-indexer
        │       ├── cluster
        │       │   ├── indexer-api-svc.yaml
        │       │   └── indexer-sts.yaml
        │       ├── indexer_conf
        │       │   ├── internal_users.yml
        │       │   └── opensearch.yml
        │       └── indexer-svc.yaml
        ├── kustomization.yml
        ├── secrets
        │   ├── dashboard-cred-secret.yaml
        │   ├── indexer-cred-secret.yaml
        │   ├── khulnasoft-api-cred-secret.yaml
        │   ├── khulnasoft-authd-pass-secret.yaml
        │   └── khulnasoft-cluster-key-secret.yaml
        └── khulnasoft_managers
            ├── khulnasoft-cluster-svc.yaml
            ├── khulnasoft_conf
            │   ├── master.conf
            │   └── worker.conf
            ├── khulnasoft-master-sts.yaml
            ├── khulnasoft-master-svc.yaml
            ├── khulnasoft-workers-svc.yaml
            └── khulnasoft-worker-sts.yaml

## Contribute

If you want to contribute to our project please don't hesitate to send a pull request. You can also join our users [mailing list](https://groups.google.com/d/forum/khulnasoft) or the [Khulnasoft Slack community channel](https://khulnasoft.com/community/join-us-on-slack/) to ask questions and participate in discussions.

## License and copyright

KHULNASOFT
Copyright (C) 2016, Khulnasoft Inc.  (License GPLv2)

## References

* [Khulnasoft website](http://khulnasoft.com)
