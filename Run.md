# Run

```bash
$ pulumi stack init gcp-ts-gke-dev
$ pulumi config set gcp:project [your-gcp-project-here]
$ pulumi config set gcp:zone us-west1-a # any valid GCP zone here
$ pulumi config set password --secret [your-cluster-password-here minimum 16 chars]
```

```sh
$ pulumi up
Previewing update (gcp-ts-gke-dev):
     Type                            Name                       Plan
 +   pulumi:pulumi:Stack             gcp-ts-gke-gcp-ts-gke-dev  create
 +   ├─ gcp:container:Cluster        gke-cluster                create
 +   ├─ pulumi:providers:kubernetes  gkeK8s                     create
 +   └─ kubernetes:apps:Deployment   canary                     create
 
Resources:
    + 4 to create

Do you want to perform this update?
> yes
  no
  details
```