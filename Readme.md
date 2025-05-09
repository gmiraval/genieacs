#Instalacion de genieacs en cluster kubernetes

##Build a docker image and push it to the docker hub

docker build -t genieacs:1.2.9 .
docker tag genieacs:1.2.9 miravallesg/genieacs:1.2.9
docker push miravallesg/genieacs:1.2.9

##configuramos secret con jwt para ui
SECRET=$(node -e "console.log(require('crypto').randomBytes(128).toString('hex'))")

kubectl create secret generic ui-jwt-secret \
  --namespace=genieacs \
  --from-literal=jwt-secret="$SECRET"

##ejecutar los kubectl create -f en orden de los yaml


#configurar genieacs
conectarse a https://uigenieacs.kube.cablevision-labs.com.ar/
y ahi seguir wizard -> click ABRACADABRA!

pop up:
An administrator user has been created for you. Use admin/admin to log in. Don't forget to change the default password.

Initialization complete -> Open Sesame!
Configurationhas been modified, please reload the page -> Reload

hacer click en login con user y pwd default. Luego dentro de ui ir a Admin-> users -> Admin y cambiar pwd:
p: embe..... w/#s


#troubleshoot
C:\Users\u606348>kubectl -n genieacs exec -it genieacs-5f667bd855-xnz2v -- bash
root@genieacs-5f667bd855-xnz2v:/var/log/genieacs# tail -f /var/log/genieacs/genieacs-cwmp.log



