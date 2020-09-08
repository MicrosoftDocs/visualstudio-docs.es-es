---
title: 'Tutorial de Docker - Parte 9: Implementación en la nube'
description: Implemente una aplicación de Docker en un servicio en la nube para hospedaje.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176929"
---
# <a name="deploy-to-the-cloud"></a>Implementación en la nube

Ahora que ha ejecutado la aplicación de forma local, puede empezar a pensar en ejecutarla en la nube para que otros usuarios puedan acceder a ella y utilizarla. Para ello, usará contextos de Docker. Un contexto es el lugar en el que trabaja actualmente con contenedores. En este momento, solo tiene el contexto "predeterminado", por lo que tendrá que agregar uno de nube en el que implementar la aplicación.

## <a name="create-your-cloud-context"></a>Creación del contexto de nube

1. Para empezar, puede ver los contextos que tiene si examina la sección de contextos del panel de Docker:

   ![Solo se muestra el contexto predeterminado](media/defaultcontext.png)

Solo debería ver el contexto predeterminado para el trabajo local.

1. Para realizar la implementación en la nube, debe crear un contexto de ACI, pero para ello, primero necesita la extensión de la cuenta de Azure para autenticarse con Azure.

   ![Adición de la extensión de Azure](media/addazureextension.png)

Si todavía no tiene una, tendrá que crear una cuenta de Azure.

1. Ahora puede crear el contexto de ACI. Para ello, haga clic en el botón más de la sección **Contextos** de la vista de Docker.

   ![Creación del contexto de ACI](media/createnewcontext.png)

Se le preguntará el grupo de recursos en el que quiere ejecutar estos contenedores. Seleccione un grupo existente con las teclas de dirección, o bien use la opción predeterminada para utilizar el nuevo grupo.

![Selección del grupo de recursos](media/selectresourcegroup.png)

Ahora puede ver el contexto de ACI en la lista y puede hacer clic con el botón derecho en él para convertirlo en el contexto de uso actual:

![El nuevo contexto de ACI se puede seleccionar](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Ejecución de contenedores en la nube

1. Ahora, use el contexto de ACI y ejecute el contenedor.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Tras ejecutarlo, examine el contenedor en el contexto.

   ![Contenedor en ejecución en el contexto de ACI](media/contextcontainer.png)

1. Para comprobar que todo funciona correctamente, puede hacer clic con el botón derecho en el contenedor en ejecución y elegir **Ver en el explorador**.

   ![Contenedor en ACI con dirección IP pública](media/containerinaci.png)

Además, puede ver que el contenedor se ejecuta en una dirección IP pública y que funciona correctamente.

1. Ahora, puede examinar el contenedor en ejecución para ver cómo funciona. Puede empezar por ver los registros de contenedor:
 
 ```bash
   docker logs distracted-jackson
   ```

1. También puede usar exec en el contenedor como lo haría con un contenedor local.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Por último, para limpiar el espacio de trabajo y asegurarse de que no se le cobra por seguir ejecutando el contenedor de prueba, puede hacer clic con el botón derecho en el contenedor en ejecución y elegir **Quitar**.

## <a name="recap"></a>Resumen

Fantástico, ha implementado correctamente la carga de trabajo en la nube por primera vez. Puede hacerlo todo desde la línea de comandos y también desde el contexto de ACI mediante `docker run`, además de usar `docker compose up` para ejecutar aplicaciones de varios contenedores. Para obtener más información sobre la ejecución de los contenedores en la nube, lea la [documentación ampliada sobre el uso de ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Pasos adicionales](whats-next.md)
