---
title: 'Tutorial de Docker - Parte 2: Actualización de la aplicación'
description: Se describe cómo actualizar una aplicación de Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176921"
---
# <a name="update-the-app"></a>Actualización de la aplicación

Como solicitud de una característica pequeña, el equipo del producto le ha pedido que cambie el "texto vacío" cuando no hay elementos en la lista de tareas pendientes. Les gustaría que se cambiara por lo siguiente:

> Todavía no hay elementos pendientes. Agregue uno arriba.

Bastante sencillo, ¿verdad? Ahora se realizará el cambio.

## <a name="update-the-source-code"></a>Actualización del código fuente

1. En el archivo `src/static/js/app.js`, actualice la línea 56 para usar el nuevo texto vacío.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Compile la versión actualizada de la imagen, con el mismo comando que ha usado antes.

    ```bash
    docker build -t getting-started .
    ```

1. Inicie un contenedor nuevo con el código actualizado.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**¡Oh!** Probablemente haya observado un error similar al siguiente (los identificadores serán diferentes):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

¿Qué ha sucedido? No se ha podido iniciar el nuevo contenedor porque el anterior todavía está en ejecución. Esto es un problema porque ese contenedor usa el puerto 3000 del host y solo un proceso en el equipo (contenedores incluidos) puede escuchar en un puerto específico. Para corregirlo, quite el contenedor anterior.

## <a name="replace-the-old-container"></a>Reemplazo del contenedor anterior

Para quitar un contenedor, primero hay que detenerlo. Una vez que se ha detenido, se puede quitar. Hay dos maneras de quitar el contenedor antiguo. No dude en elegir la ruta con la que esté más cómodo.

### <a name="remove-a-container-using-the-cli"></a>Eliminación de un contenedor mediante la CLI

1. Use el comando `docker ps` para obtener el identificador del contenedor.

    ```bash
    docker ps
    ```

1. Use el comando `docker stop` para detener el contenedor.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Una vez que haya detenido el contenedor, puede quitarlo mediante el comando `docker rm`.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Puede detener y quitar un contenedor en un solo comando si agrega la marca "force" al comando `docker rm`. Por ejemplo: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Eliminación de un contenedor mediante el panel de Docker

Si abre la extensión VS Code, puede quitar un contenedor con dos clics. Es sin duda mucho más fácil que tener que buscar el identificador del contenedor y quitarlo.

1. Con la extensión abierta, navegue hasta el contenedor y haga clic con el botón derecho.

1. Haga clic en la opción **Quitar**.

1. Confirme la eliminación y ya habrá terminado.

![Panel de Docker: eliminación de un contenedor](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Inicio del contenedor de aplicación actualizado

1. Ahora, inicie la aplicación actualizada.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Actualice el explorador en [http://localhost:3000](http://localhost:3000); debería ver el texto de ayuda actualizado.

![Aplicación actualizada con el texto vacío actualizado](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Resumen

Aunque ha podido crear una actualización, es posible que haya observado dos aspectos:

- Todos los elementos existentes en la lista de tareas pendientes han desaparecido. No es una aplicación muy buena. Esto se comentará en breve.
- Se han realizado *muchos* pasos para un cambio tan pequeño. En una sección posterior, obtendrá información sobre cómo ver las actualizaciones de código sin necesidad de recompilar e iniciar un contenedor nuevo cada vez que realice un cambio.

Antes de obtener información sobre la persistencia, verá rápidamente cómo compartir estas imágenes con otros usuarios.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Uso compartido de la aplicación](share-your-app.md)
