---
title: 'Tutorial de Docker: Pasos siguientes'
description: Se describen opciones para ampliar las aplicaciones de Docker con orquestación, mediante proyectos de Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176789"
---
# <a name="whats-next"></a>Pasos adicionales

Aunque haya terminado con el tutorial, todavía hay mucha más que aprender sobre los contenedores.
Aquí no profundizará, pero se le ofrecen otras áreas que puede examinar más adelante.

## <a name="container-orchestration"></a>Orquestación de contenedores

La ejecución de contenedores en producción es difícil. No quiere iniciar sesión en un equipo y simplemente ejecutar `docker run` o `docker-compose up`. ¿Por qué no? ¿Qué ocurre si los contenedores desaparecen? ¿Cómo puede escalar entre varios equipos? La orquestación de contenedores resuelve este problema. Herramientas como Kubernetes, Swarm, Nomad y AKS ayudan a resolver este problema de maneras ligeramente distintas.

El concepto es que tiene "administradores" que reciben un **estado esperado**. Este estado podría ser "quiero ejecutar dos instancias de la aplicación web y exponer el puerto 80". Después, los administradores examinan todos los equipos del clúster y delegan el trabajo en nodos de "trabajo". Los administradores inspeccionan los cambios (como el cierre de un contenedor) y, después, trabajan para que el **estado real** refleje el estado esperado.

## <a name="cloud-native-computing-foundation-projects"></a>Proyectos de Cloud Native Computing Foundation

CNCF es un hogar independiente del proveedor para varios proyectos de código abierto, como Kubernetes, Prometheus, Envoy, Linkerd, NATS y muchos más. Puede ver los [proyectos graduados e incubados aquí](https://www.cncf.io/projects/) y el [ecosistema completo de CNCF aquí](https://landscape.cncf.io/). Hay muchos proyectos que le ayudarán a resolver problemas relacionados con la supervisión, el registro, la seguridad, los registros de imágenes, la mensajería, etc.

Por tanto, si no está familiarizado con el ecosistema de los contenedores y el desarrollo de aplicaciones nativas de nube, bienvenido. Póngase en contacto con la comunidad, formule preguntas y siga aprendiendo. Nos complacerá su presencia.

## <a name="working-with-docker-in-vs-code"></a>Uso de Docker en VS Code

Obtenga más información sobre el uso de la extensión Docker de VS Code:

- [Introducción a la extensión Docker de VS Code](https://code.visualstudio.com/docs/containers/overview)
- [Introducción a Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introducción a Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introducción a .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Depuración de aplicaciones en contenedores](https://code.visualstudio.com/docs/containers/debug-common)
