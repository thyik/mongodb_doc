# Google Cloud Platform (GCP)

-   Qwiklab : Learning site for using GCP
-   Cloud Shell

```Cloud Shell

// spin-off a new VM instance
$ gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone us-central1-c

// help manual
$ gcloud compute instances create --help

// change default gcloud zone
$ gcloud config set compute/zone ...

// change default gcloud region
$ gcloud config set compute/region ...

// list vm instances
$ gcloud compute instances list

// describe instance
$ gcloud compute instances describe gcelab2

// describe only given state
gcloud compute instances describe gcelab2 --format="yaml(name,status,disk)"

// ssh from cloud shell to VM instance
$ gcloud compute ssh gcelab2 --zone us-central1-c

```

-   VM

```ssh
// login to root
$ sudo su -

// update package
$ apt-get update

// instal nginx server
$ apt-get install nginx -y

// check nginx server running
$ ps auwx | grep nginx
```

-   GCloud commands

```
$ gcloud compute project-info describe --project qwiklabs-gcp-04-f207032a3846

// setup environment variable
$ export PROJECT_ID=qwiklabs-gcp-04-f207032a3846
$ export ZONE=us-central1-a

// print environment variable
$ echo PROJECT_ID
$ echo ZONE

// create vm instance using environment variable
$ gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone $ZONE

// help manual
$ gcloud -h

// list configuration
$ gcloud config list

// SDK components
$ gcloud components list
```

-   GCloud Shell

```
// update cloud sdk
$ sudo apt-get install google-cloud-sdk

// interactive mode CLI (with auto complete)
$ gcloud beta interactive

```

-   VM shell

```
// change to home directory
$ cd $HOME

// edit .bashrc
$ vi ./.bashrc
```
