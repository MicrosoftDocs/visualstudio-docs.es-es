---
title: 'Tutorial de Docker, parte 3: compartir la aplicación'
description: Describe cómo compartir imágenes de Docker mediante el registro de Docker Hub.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d5bd7a2d79bf6da710fd0f5803c2415781160143
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176919"
---
# <a name="share-your-app"></a>Compartir la aplicación

Ahora que hemos creado una imagen, vamos a compartirla. Para compartir imágenes de Docker, tiene que usar un registro de Docker. El registro predeterminado es Docker Hub y es donde proceden todas las imágenes que hemos usado.

## <a name="create-a-repo"></a>Creación de un repositorio

Para enviar una imagen, primero debe crear un repositorio en Docker Hub.

1. Vaya a [Docker Hub](https://hub.docker.com) e inicie sesión si es necesario.

1. Haga clic en el botón **crear repositorio** .

1. Para el nombre del repositorio, use `getting-started` . Asegúrese de que la visibilidad es `Public` .

1. Haga clic en el botón **crear** .

Si busca en el lado derecho de la página, verá una sección denominada **comandos de Docker**. Esto proporciona un comando de ejemplo que deberá ejecutar para enviarlo a este repositorio.

![Comando de Docker con ejemplo de extracción](media/push-command.png)

## <a name="push-the-image"></a>Inserte la imagen

1. En la línea de comandos, intente ejecutar el comando de inserción que aparece en Docker Hub. Tenga en cuenta que el comando usará el espacio de nombres, no "Docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    ¿Por qué se ha producido un error? El comando de extracción estaba buscando una imagen denominada Docker/Getting-Started, pero no encontró ninguna. Si ejecuta `docker image ls` , no verá ninguno.

    Para solucionarlo, debe "etiquetar" la imagen existente que hemos creado para darle otro nombre.

1. Inicie sesión en Docker Hub mediante el comando `docker login -u <username>` .

1. Use el `docker tag` comando para asignar `getting-started` un nuevo nombre a la imagen. Asegúrese de cambiar `<username>` con el identificador de Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Ahora vuelva a intentar el comando de instalación. Si va a copiar el valor de Docker Hub, puede quitar la `tagname` parte, ya que no ha agregado una etiqueta al nombre de la imagen. Si no especifica una etiqueta, Docker usará una etiqueta denominada `latest` .

    ```bash
    docker push <username>/getting-started
    ```

## <a name="run-the-image-on-a-new-instance"></a>Ejecutar la imagen en una nueva instancia

Ahora que la imagen se ha compilado e insertado en un registro, intente ejecutar la aplicación en una nueva instancia de con una marca que nunca haya encontrado esta imagen de contenedor. Para ello, usará Play con Docker.

1. Abra el explorador para [jugar con Docker](http://play-with-docker.com).

1. Inicie sesión con su cuenta de Docker Hub.

1. Una vez que haya iniciado sesión, haga clic en el vínculo "+ Agregar nueva instancia" en la barra lateral izquierda. (Si no lo ve, haga que el explorador sea un poco más amplio). Después de unos segundos, se abrirá una ventana de terminal en el explorador.

    ![Reproducir con Docker agregar nueva instancia](media/pwd-add-new-instance.png)

1. En el terminal, inicie la aplicación recién insertada.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Debería ver que la imagen se extrae y, finalmente, se inicia.

1. Haga clic en el distintivo 3000 cuando aparezca y debería ver la aplicación con sus modificaciones. Alegría! Si no aparece el distintivo 3000, puede hacer clic en el botón **abrir puerto** y escribir 3000.

## <a name="recap"></a>Resumen

En esta sección, ha aprendido a compartir imágenes mediante su inserción en un registro. A continuación, pasó a una instancia nueva de la marca y podía ejecutar la imagen insertada. Esto es bastante común en las canalizaciones de CI, donde la canalización creará la imagen e inscribirá en un registro y, a continuación, el entorno de producción puede usar la versión más reciente de la imagen.

Ahora que ya ha descubierto, recuerde que al final de la última sección, cuando reinició la aplicación, perdió todos los elementos de la lista de tareas pendientes. Obviamente, eso no es una excelente experiencia del usuario, por lo que aprenderá cómo puede conservar los datos entre reinicios.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Almacenar la base de datos](persist-your-data.md)