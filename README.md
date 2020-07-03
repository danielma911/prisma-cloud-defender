# prisma-cloud-defender

# Installation Guide:

# Generate a defender.yaml file, where:
The following command connects to Console’s API (specified in --address) as user <ADMIN> (specified in --user), and generates a Defender DaemonSet YAML config file according to the configuration options passed to twistcli.
The --cluster-address option specifies the address Defender uses to connect to Console. For Defenders deployed in the cluster where Console runs, specify Prisma Cloud Console’s service name, twistlock-console. For Defenders deployed outside the cluster, specify either Console’s external IP address, exposed by the LoadBalancer, or better, Console’s DNS name, which you must manually set up separately.
The following command directs Defender to connect to Console using its service name. Use it for deploying a Defender DaemonSet inside a cluster.
  
$ <PLATFORM>/twistcli defender export kubernetes \
  --address https://yourconsole.example.com:8083 \
  --user <ADMIN_USER> \
  --cluster-address twistlock-console
<PLATFORM> can be linux or osx.
<ADMIN_USER> is the name of the initial admin user you just created.
  
# Deploy the Defender DaemonSet.
$ kubectl create -f defender.yaml
