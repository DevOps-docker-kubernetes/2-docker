# Docker
# 

  1. [Caso de estudio](#case)
  2. [Comandos usados](#comand)


<hr>

<a name="case"></a>

## 1. Caso de estudio
- Se requiere desplegar la aplicación de facturación de la compañía en los entornso de integración, preproducción y producción
- Las instalaciones debe contar alta disponibilidad, excepto en integracción
### Requisitos mínimos
* Java 1.8
* Servidor Web Nginx
* Bases de datos Postgres

Si tuviésemos que implementar esta solución de forma tradicional, deberíamos replicar la instalación y configuración de Java, Nginx y Postgres en las 5 máquinas que darían el servicio para tener levantados los tres entornos. Además, si necesitamos escalar para mantener la disponibilidad, deberemos hacer lo mismo en cada una de las nuevas máquinas.

![image](./images/img1.png)

Este diagrama se simplifica mediante el uso de imágenes de docker, ya que sólamente hacemos la instalación y configuración de las herramientas necesarias una vez en el contenedor de docker. Luego este contenedor se utilizará en el Docker Engine en cada una de las máquinas que sea necesaria.

![image](./images/img2.png)


<hr>

<a name="comand"></a>
## 2. Comandos usados
Comprobamos que docker esté activo y arrancado
~~~
sudo service docker status
~~~

Agregarmos nuestro usuario actual a ese grupo de docker
~~~
sudo usermod -aG docker $USER
~~~
Intalación de docker compose

~~~
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
~~~
Permiso de ejecución
~~~
sudo chmod +x /usr/local/bin/docker-compose
~~~

Enlace simbólico
~~~
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
~~~
Version de docker
~~~
docker-version --version
~~~