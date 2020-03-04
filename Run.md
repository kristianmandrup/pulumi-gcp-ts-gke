# Run

Make sure you have `pulumi` CLI installed

Run the following pulumi commands

```bash
$ pulumi stack init gcp-ts-gke-dev
$ pulumi config set gcp:project [your-gcp-project-here]
$ pulumi config set gcp:zone us-west1-a # any valid GCP zone here
$ pulumi config set password --secret [your-cluster-password-here - minimum 16 chars]
```

Example

```sh
$ pulumi config set gcp:project micro-frontend-app
$ pulumi config set gcp:zone us-west1-a
$ pulumi config set password --secret pulumi@1234@5678
```

Set node count to `1`

```sh
$ pulumi config set nodeCount 1
```

Then run `pulumi up` to create and deploy the cluster

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

## Troubleshooting

`google: could not find default credentials`. See [application-default-credentials](https://developers.google.com/accounts/docs/application-default-credentials) for more information.

### Pulumi GCP setup

See [Pulumi GCP setup](https://www.pulumi.com/docs/intro/cloud-providers/gcp/setup/)

The Pulumi Google Cloud Platform Provider needs to be configured with Google credentials before it can be used to create resources.

When developing locally, we recommend that you use gcloud login to configure your account credentials:

```sh
gcloud auth login
gcloud config set project <YOUR_GCP_PROJECT_HERE>
gcloud auth application-default login
```
