## Setup

**requirements**

The application requires the following dependencies:

  - `jq`
  - `awscli`
  - `docker`
  - `kubetcl`
  - `helm`
  - `aws-iam-authenticator`
  - `terraform @ >= 0.12`

**pre**

Before starting the application, you must do these steps:

| Step | Command | Description |
| :---: | :---- | :---- |
| 1 | `./run_kube create_scale_app` | containerize flask app |
| 2 | `./run_kube create_spark_base` | create spark base image |
| 3 | `./run_kube create_from_spark_base` | create spark master and worker images from base |
| 4 | `./run_kube push_to_docker_hub` | push images to docker hub |
| 5 | `./run_kube gen_pg_assets` | generate hash_names.csv w/ md5_to_paths.json as intermediate |

**start application**

To start the application, you can run the following steps:

| Step | Command | Description |
| :---: | :---- | :---- |
| 1 | `./run_kube setup_eks` | setup vpc + eks cluster |
| 2 | `./run_kube helm_init` | instantiate helm + tiller |
| 3 | `./run_kube setup_monitoring` | setup monitoring |
| 4 | `./run_kube setup_dashboards` | load custom grafana dashboards |
| 5 | `./run_kube setup_scale_app` | setup scale data pipeline |

**teardown application**

To bring down the application you can run the following steps:

| Step | Command | Description |
| :---: | :---- | :---- |
| 1 | `./run_kube cleanup_scale_app` | cleanup scale data pipeline |
| 2 | `./run_kube cleanup_dashboards` | delete custom grafana dashboards |
| 3 | `./run_kube cleanup_monitoring` | cleanup monitoring |
| 4 | `./run_kube cleanup_tiller` | cleanup tiller |
| 5 | `./run_kube teardown` | destroy eks cluster + vpc |
