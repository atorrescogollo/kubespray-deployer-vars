# Kubespray Deployer Vars
Variables for kubespray-deployer

## Intructions
1. Configure `env` file with needed vars. Check out [`env.template`](./env.template) file.
2. Place the following files in their corresponding paths:
  * `ssl/ca.crt`: Certificate of the CA from which all certificates were signed.
  * `ssl/ingress.crt`: Certificate for ingresses. It should have a wildcard like `*.<clustername>.intra.net`
  * `ssl/ingress.key`: Private Key of Ingress Certificate.
3. Prepare the cluster inventory (`cluster_inventory.yml`). Check out [**this example**](https://github.com/atorrescogollo/kubespray-deployer/blob/main/examples/cluster_inventory.yml)
4. Execute kubespray-deployer:
```bash
$ ssh-add ~/.ssh/id_rsa
$ docker run -it --rm \
    -v $SSH_AUTH_SOCK:/ssh-agent \
    -e "SSH_AUTH_SOCK=/ssh-agent" \
    -v $PWD:/work \
    --env-file $PWD/env \
    atorrescogollo/kubespray-deployer
```
