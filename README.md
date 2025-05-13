PARA COMPLETAR ESTE TRABAJO PRÁCTICO:

Primero, debemos instalar Minikube y el driver Docker.
Podés descargar Minikube desde el siguiente enlace:
https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download

También necesitás instalar Kubectl, que es la herramienta para interactuar con Kubernetes mediante la terminal:
https://kubernetes.io/docs/tasks/tools/

Y no olvides instalar Git, que te permitirá clonar los repositorios necesarios:
https://git-scm.com/downloads

PASOS INICIALES

Una vez que tengas todo instalado, creá una carpeta en tu computadora donde quieras trabajar, y accedé a ella usando el comando cd desde la terminal.

Dentro de esa carpeta, ejecutá los siguientes comandos:

git init
git clone https://github.com/"nombre del usuario"/manifiestosTD5.git
git clone https://github.com/"nombre del usuario"/static-website2.git

INICIAR MINIKUBE

Con los repositorios clonados, volvemos al directorio principal y arrancamos Minikube con el siguiente comando:

minikube start --mount --mount-string="/ruta/a/tu/static-website2:/mnt/web"

Asegurate de reemplazar "/ruta/a/tu/static-website2" con la ruta real donde está la carpeta del HTML.

APLICAR LOS MANIFIESTOS

Una vez que la máquina virtual esté corriendo, navegá con cd a la carpeta donde están los manifiestos (excepto los de ingress) y aplicalos con:

kubectl apply -f .

Esto iniciará tu pod. Podés monitorear su estado con:

kubectl get pods

Vas a ver algo como static-site-XXX-XXX. El estado pasará por Pending, ContainerCreating, y finalmente Running.

Cuando el pod esté en estado Running, podés exponer el servicio y abrir la web con:

minikube service static-site-service

Esto abrirá automáticamente una pestaña en tu navegador con tu página web.

¡FELICITACIONES! 
¡Acabás de levantar tu primer servicio en Kubernetes!


