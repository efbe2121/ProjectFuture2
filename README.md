# ProjectFuture2
For 2nd phase of FutureProgram, where everything is made with love and effort
```bash
├── backups
│   ├── CoreDNS
│   │   └── DeploymentAffinity
│   ├── RKE2 Config
│   │   ├── master1
│   │   │   └── config.yaml
│   │   ├── master2
│   │   │   └── config.yaml
│   │   └── master3
│   │       └── config.yaml
│   └── RKE2 Worker Config
│       ├── worker1
│       │   └── config.yaml
│       └── worker2
│           └── config.yaml
├── cicd
│   ├── Tekton
│   │   ├── manifests
│   │   │   ├── tektondashboard.yaml
│   │   │   ├── tektonpipelines.yaml
│   │   │   ├── tektontriggerinterceptors.yaml
│   │   │   └── tektontrigger.yaml
│   │   └── Pipelines
│   │       ├── Demo0
│   │       │   ├── pipeline-hello.yaml
│   │       │   └── task-hello.yaml
│   │       ├── Demo1
│   │       │   ├── all-in-one.yaml
│   │       │   ├── git-source.yaml
│   │       │   └── task1.yaml
│   │       ├── Demo2
│   │       │   └── with-workspace.yaml
│   │       ├── realTest
│   │       │   └── gitappspipeline.yaml
│   │       ├── realTest2
│   │       │   ├── Ingress & Webhook.yaml
│   │       │   ├── patches.yaml
│   │       │   ├── tekton-secret-sa.yaml
│   │       │   ├── test.yaml
│   │       │   └── Trigger&EventListener.yaml
│   │       └── realTest3
│   │           ├── all-in-one.yaml
│   │           ├── logs
│   │           ├── pipeline.yaml
│   │           ├── task1.yaml
│   │           └── task2.yaml
│   └── TektonGit
│       ├── app
│       │   ├── index.js
│       │   ├── package.json
│       │   ├── package-lock.json
│       │   └── tests
│       │       └── integration.routes.test.js
│       ├── helloww
│       │   └── hello world.txt
│       └── README.md
├── config.yml
├── dummy pods
│   ├── dashboard.yaml
│   ├── master-dnstester.yaml
│   ├── rancher-curl.yaml
│   ├── rancher-dashboard.yaml
│   └── worker-dnstester.yaml
├── ingress
│   ├── controller
│   │   ├── deploy.yaml
│   │   └── patch.yaml
│   ├── nginx.yaml
│   └── tektondashboard.yaml
├── metallb
│   ├── configmap.yaml
│   ├── metallb.yaml
│   └── namespace.yaml
├── nfs
│   ├── nfs-provisioning
│   │   ├── default-sc.yaml
│   │   ├── deployment.yaml
│   │   ├── pvc-demo.yaml
│   │   └── rbac.yaml
│   ├── nfs-pvc.yaml
│   └── nfs-pv.yaml
├── provisioning
│   ├── envoy.sh
│   ├── inventory.ini
│   ├── master
│   │   ├── playbook.yaml
│   │   └── RKE2
│   │       ├── defaults
│   │       │   └── main.yaml
│   │       ├── tasks
│   │       │   ├── config.yaml
│   │       │   ├── install.yaml
│   │       │   ├── main.yaml
│   │       │   └── verify.yaml
│   │       └── templates
│   │           ├── config_master1.yaml.j2
│   │           └── config_master23.yaml.j2
│   ├── monitoring
│   │   ├── envoy-files
│   │   │   ├── envoy-me.yaml
│   │   │   └── envoy.service
│   │   ├── playbook.yaml
│   │   └── zabbix-templates
│   │       ├── envoy-discovery
│   │       │   ├── Capture
│   │       │   │   ├── discovery.JPG
│   │       │   │   ├── graphe.JPG
│   │       │   │   ├── item.JPG
│   │       │   │   ├── items 2.JPG
│   │       │   │   └── listener.JPG
│   │       │   └── envoy.xml
│   │       └── kubernetes
│   │           ├── k8s-zabbix-template.xml
│   │           └── zabbix_user_manifest.yaml
│   └── worker
│       ├── playbook.yaml
│       └── RKE2 Worker
│           ├── defaults
│           │   └── main.yaml
│           ├── tasks
│           │   ├── config.yaml
│           │   ├── install.yaml
│           │   ├── main.yaml
│           │   └── verify.yaml
│           └── templates
│               └── config.yaml.j2
├── secrets
│   ├── manifests
│   │   ├── dockerhub.yaml
│   │   └── githubtoken.yaml
|   ├── IngressWebhookSecrets.yaml
│   └── vars.yaml
└── Vagrantfile

48 directories, 88 files
```

░░░░░░░░░░░░▄▄░░░░░░░░░░░░░░  
░░░░░░░░░░░█░░█░░░░░░░░░░░░░  
░░░░░░░░░░░█░░█░░░░░░░░░░░░░  
░░░░░░░░░░█░░░█░░░░░░░░░░░░░  
░░░░░░░░░█░░░░█░░░░░░░░░░░░░  
██████▄▄█░░░░░██████▄░░░░░░░  
▓▓▓▓▓▓█░░░░░░░░░░░░░░█░░░░░░  
▓▓▓▓▓▓█░░░░░░░░░░░░░░█░░░░░░  
▓▓▓▓▓▓█░░░░░░░░░░░░░░█░░░░░░  
▓▓▓▓▓▓█░░░░░░░░░░░░░░█░░░░░░  
▓▓▓▓▓▓█░░░░░░░░░░░░░░█░░░░░░  
▓▓▓▓▓▓█████░░░░░░░░░██░░░░░░  
█████▀░░░░▀▀████████░░░░░░░░  
░░░░░░░░░░░░░░░░░░░░░░░░░░░░  
░▀█▀░░░▀█▀░▀█▀░▀█▀░░▀█▀▀▀▀█░  
░░█░░░░░█░░░█░▄▀░░░░░█░░░░░░  
░░█░░░░░█░░░█▀▄░░░░░░█▄▄▄░░░  
░░█░░░░░█░░░█░░▀▄░░░░█░░░░░░  
░▄█▄▄█░▄█▄░▄█▄░░▄█▄░▄█▄▄▄▄█░  
░░░░░░░░░░░░░░░░░░░░░░░░░░░░  
