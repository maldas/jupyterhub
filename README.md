# jupyterhub

To start Single node server on a VM

cd /etc/jupyterhub

sudo -u hubuser jupyterhub --JupyterHub.spawner_class=sudospawner.SudoSpawner --ip=0.0.0.0 --port=8888 --debug &

# Kubernetes

gcloud container clusters get-credentials skdtech-cluster --zone us-central1-a --project endless-elysium-231508

RELEASE=jhub

NAMESPACE=jhub

kubectl create serviceaccount --namespace kube-system tiller

kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller

kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'   

helm init --service-account tiller --upgrade

helm upgrade --install $RELEASE jupyterhub/jupyterhub --namespace $NAMESPACE --version=0.8.0 --values config.yaml

# docker
for more info check https://github.com/maldas/hubuser/blob/master/Dockerfile
