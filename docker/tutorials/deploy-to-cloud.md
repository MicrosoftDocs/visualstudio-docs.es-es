---
title: 'Tutorial de Docker, parte 9: implementación en la nube'
description: Implementar una aplicación de Docker en un servicio en la nube para hospedar.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176929"
---
# <a name="deploy-to-the-cloud"></a>Implementación en la nube

Ahora que ha ejecutado la aplicación localmente, puede empezar a pensar en ejecutarla en la nube para que otras personas puedan tener acceso a ella y usarla. Para ello, usará contextos de Docker. Un contexto es el lugar en el que está trabajando actualmente con contenedores. En este momento, solo tiene el contexto "predeterminado", por lo que tendrá que agregar una nube e implementar la aplicación en ella.

## <a name="create-your-cloud-context"></a>Crear el contexto de nube

1. Para empezar, puede ver los contextos que tiene mirando en la sección contextos del panel de Docker:

   ![Muestra solo el contexto predeterminado](media/defaultcontext.png)

Solo debería ver el contexto predeterminado para el trabajo local.

1. Para realizar la implementación en la nube, debe crear un nuevo contexto de ACI, pero para ello, primero necesita la extensión de la cuenta de Azure para autenticarse con Azure.

   ![Incorporación de la extensión de Azure](media/addazureextension.png)

Deberá configurar una cuenta de Azure si aún no tiene una.

1. Ahora puede crear el nuevo contexto ACI. Para ello, haga clic en el botón más en la sección **contextos** de la vista de Docker.

   ![Crear el contexto de ACI](media/createnewcontext.png)

Esto le preguntará el grupo de recursos en el que desea ejecutar estos contenedores. Seleccione un grupo existente con las teclas de dirección o use la opción predeterminada para usar el nuevo grupo.

![Selección del grupo de recursos](media/selectresourcegroup.png)

Ahora puede ver el contexto de ACI en la lista y puede hacer clic con el botón derecho en él para convertirlo en el contexto de uso o en uso actual:

![Se puede seleccionar nuevo contexto ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Ejecutar contenedores en la nube

1. Ahora, use el contexto de ACI y ejecute el contenedor.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Tras ejecutarlo, ahora mire el contenedor en el contexto.

   ![Contenedor que se ejecuta en el contexto de ACI](media/contextcontainer.png)

1. Para comprobar que todo funciona correctamente, puede hacer clic con el botón derecho en el contenedor en ejecución y elegir **ver en el explorador**.

   ![Contenedor en ACI con IP pública](media/containerinaci.png)

Además, puede ver que el contenedor se está ejecutando en una dirección IP pública y que funciona correctamente.

1. Ahora, puede echar un vistazo al contenedor en ejecución para ver cómo funciona. Puede empezar por ver los registros de contenedor:
 
 ```bash
   docker logs distracted-jackson
   ```

1. También puede ejecutar el contenedor como lo haría con un contenedor local.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Por último, para limpiar el espacio de trabajo y asegurarse de que no se le cobra por seguir ejecutando el contenedor de prueba, puede hacer clic con el botón derecho en el contenedor en ejecución y elegir **quitar**.

## <a name="recap"></a>Resumen

Fantástico, ahora ha tomado la carga de trabajo y la ha implementado correctamente en la nube por primera vez. Puede hacer todo esto desde la línea de comandos también desde el contexto de ACI mediante `docker run` y también con `docker compose up` para ejecutar aplicaciones de varios contenedores. Para obtener más información sobre la ejecución de los contenedores en la nube, lea la [documentación](https://docs.docker.com/engine/context/aci-integration/)ampliada sobre el uso de ACI.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Pasos siguientes](whats-next.md)
