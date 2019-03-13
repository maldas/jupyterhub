# jupyterhub

#To start Server 
cd /etc/jupyterhub
sudo -u hubuser jupyterhub --JupyterHub.spawner_class=sudospawner.SudoSpawner --ip=0.0.0.0 --port=8888 --debug &
