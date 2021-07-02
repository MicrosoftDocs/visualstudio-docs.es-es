---
title: 'Tutorial de Docker - Parte 3: Compartición de la aplicación'
description: Se describe cómo compartir imágenes de Docker mediante el registro de Docker Hub.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d64d10c7abefc14f31c39c3b8397e95cec67e9f4
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222791"
---
# <a name="share-your-app"></a>Compartición de la aplicación

Ahora que ha creado una imagen, tendrá que compartirla. Para compartir imágenes de Docker, tiene que usar un registro de Docker. El registro predeterminado es Docker Hub, del que proceden todas las imágenes que ha usado.

## <a name="create-a-repo"></a>Creación de un repositorio

Para insertar una imagen, primero debe crear un repositorio en Docker Hub.

1. Vaya a [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) e inicie sesión si es necesario.

1. Haga clic en el botón **Create Repository** (Crear repositorio).

1. Para el nombre del repositorio, use `getting-started`. Asegúrese de que la visibilidad es `Public`.

1. Haga clic en el botón **Create** (Crear).

Si se fija en el lado derecho de la página, verá una sección denominada **Docker commands** (Comandos de Docker). Proporciona un comando de ejemplo que deberá ejecutar para insertar en este repositorio.

![Comando de Docker con ejemplo de inserción](media/push-command.png)

## <a name="push-the-image"></a>Inserción de la imagen

1. En la línea de comandos, intente ejecutar el comando de inserción que aparece en Docker Hub. Tenga en cuenta que el comando usará el espacio de nombres, no "docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    ¿Por qué se ha producido un error? El comando de inserción buscaba una imagen denominada docker/getting-started, pero no ha encontrado ninguna. Si ejecuta `docker image ls`, tampoco la verá.

    Para solucionarlo, debe "etiquetar" la imagen existente que ha creado para asignarle otro nombre.

1. Inicie sesión en Docker Hub mediante el comando `docker login -u <username>`.

1. Use el comando `docker tag` para asignar un nombre nuevo a la imagen `getting-started`. Asegúrese de cambiar `<username>` por el id. de Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Ahora vuelva a intentar el comando de inserción. Si va a copiar el valor de Docker Hub, puede quitar la parte `tagname`, ya que no ha agregado una etiqueta al nombre de la imagen. Si no especifica una etiqueta, Docker usará una etiqueta llamada `latest`.

    ```bash
    docker push <username>/getting-started
    ```

    En lugar de la línea de comandos, también puede hacer clic con el botón derecho en la etiqueta de imagen de la sección **Imágenes** de la vista de Docker y elegir **Insertar...** , después **Conectar registro...** y, a continuación, **Docker Hub**.

## <a name="run-the-image-on-a-new-instance"></a>Ejecución de la imagen en una nueva instancia

Ahora que la imagen se ha compilado e insertado en un registro, intente ejecutar la aplicación en una instancia nueva que nunca haya visto esta imagen de contenedor. Para ello, usará Play with Docker.

1. Abra el explorador en [Play with Docker](http://play-with-docker.com).

1. Inicie sesión con la cuenta de Docker Hub.

1. Una vez que haya iniciado sesión, haga clic en el vínculo "+ ADD NEW INSTANCE" (AGREGAR NUEVA INSTANCIA) en la barra lateral de la izquierda. (Si no lo ve, aumente el ancho del explorador). Después de unos segundos, se abrirá una ventana de terminal en el explorador.

    ![Nueva instancia agregada en Play with Docker](media/pwd-add-new-instance.png)

1. En el terminal, inicie la aplicación recién insertada.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Debería ver que la imagen se extrae y, en última instancia, se inicia.

1. Haga clic en la notificación 3000 cuando aparezca; debería ver la aplicación con las modificaciones. Enhorabuena. Si no aparece la notificación 3000, puede hacer clic en el botón **Open Port** (Abrir puerto) y escribir 3000.

## <a name="recap"></a>Resumen

En esta sección, ha aprendido a compartir imágenes mediante su inserción en un registro. Después, ha cambiado a una instancia nueva y ha podido ejecutar la imagen recién insertada. Esto es bastante común en las canalizaciones de CI, donde la canalización creará la imagen, la insertará en un registro y, después, el entorno de producción puede usar la versión más reciente de la imagen.

Ahora que lo ha descubierto, recuerde que al final de la última sección, cuando ha reiniciado la aplicación, se han perdido todos los elementos de la lista de tareas pendientes. Obviamente eso no es una experiencia del usuario correcta, por lo que aprenderá a conservar los datos entre reinicios.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Conservación de la base de datos](persist-your-data.md)
