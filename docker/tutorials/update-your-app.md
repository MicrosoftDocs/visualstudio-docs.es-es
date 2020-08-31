---
title: 'Tutorial de Docker, parte 2: actualización de la aplicación'
description: Describe cómo actualizar una aplicación de Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176921"
---
# <a name="update-the-app"></a>Actualización de la aplicación

Como solicitud de característica pequeña, el equipo del producto le ha pedido que cambie el "texto vacío" cuando no tiene ningún elemento de la lista de tareas pendientes. Les gustaría realizar la transición a lo siguiente:

> Todavía no tiene elementos pendientes. Agregue uno arriba.

Es bastante sencillo, ¿es correcto? Vamos a hacer el cambio.

## <a name="update-the-source-code"></a>Actualización del código fuente

1. En el `src/static/js/app.js` archivo, actualice la línea 56 para usar el nuevo texto vacío.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Compile la versión actualizada de la imagen con el mismo comando que usó antes.

    ```bash
    docker build -t getting-started .
    ```

1. Inicie un nuevo contenedor con el código actualizado.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**¡Oh!** Probablemente haya observado un error similar al siguiente (los identificadores serán diferentes):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

¿Qué ha ocurrido? No se pudo iniciar el nuevo contenedor porque el contenedor anterior todavía se está ejecutando. La razón por la que se trata de un problema se debe a que ese contenedor usa el puerto 3000 del host y solo un proceso en el equipo (contenedores incluidos) puede escuchar en un puerto específico. Para solucionarlo, quite el contenedor antiguo.

## <a name="replace-the-old-container"></a>Reemplazar el contenedor anterior

Para quitar un contenedor, primero debe detenerse. Una vez que se ha detenido, se puede quitar. Tiene dos maneras de quitar el contenedor antiguo. No dude en elegir la ruta de acceso con la que está más familiarizado.

### <a name="remove-a-container-using-the-cli"></a>Eliminación de un contenedor mediante la CLI

1. Obtenga el identificador del contenedor mediante el `docker ps` comando.

    ```bash
    docker ps
    ```

1. Use el `docker stop` comando para detener el contenedor.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Una vez detenido el contenedor, puede quitarlo mediante el `docker rm` comando.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Puede detener y quitar un contenedor en un solo comando agregando la marca "Force" al `docker rm` comando. Por ejemplo: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Quitar un contenedor mediante el panel de Docker

Si abre la extensión VS Code, puede quitar un contenedor con dos clics. Ciertamente es mucho más fácil que tener que buscar el identificador del contenedor y quitarlo.

1. Con la extensión abierta, navegue hasta el contenedor y haga clic con el botón secundario.

1. Haga clic en la opción **quitar** .

1. Confirme la eliminación y ya ha terminado.

![Panel de Docker: eliminación de un contenedor](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Iniciar el contenedor de la aplicación actualizado

1. Ahora, inicie la aplicación actualizada.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Actualice el explorador en [http://localhost:3000](http://localhost:3000) y debería ver el texto de ayuda actualizado.

![Aplicación actualizada con texto vacío actualizado](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Resumen

Aunque se pudo crear una actualización, había dos cosas que podría haber observado:

- Ya no se han completado todos los elementos existentes en la lista de tareas pendientes. No es una aplicación muy buena. Hablaremos sobre esto en breve.
- Se han producido *muchos* pasos para este cambio pequeño. En una próxima sección, aprenderá a ver las actualizaciones de código sin necesidad de recompilar e iniciar un nuevo contenedor cada vez que realice un cambio.

Antes de aprender sobre la persistencia, verá rápidamente cómo compartir estas imágenes con otras personas.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Uso compartido de la aplicación](share-your-app.md)
