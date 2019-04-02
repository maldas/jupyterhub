# jupyterhub

#To start Server Single Node
cd /etc/jupyterhub
sudo -u hubuser jupyterhub --JupyterHub.spawner_class=sudospawner.SudoSpawner --ip=0.0.0.0 --port=8888 --debug &

RELEASE=jhub
NAMESPACE=jhub
helm init
helm upgrade --install $RELEASE jupyterhub/jupyterhub --namespace $NAMESPACE --version=0.8.0 --values config.yaml
