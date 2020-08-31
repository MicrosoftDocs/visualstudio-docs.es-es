---
title: 'Tutorial de Docker: pasos siguientes'
description: Describe las opciones para ampliar las aplicaciones de Docker con orquestación, mediante proyectos de Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176789"
---
# <a name="whats-next"></a>Pasos adicionales

Aunque haya terminado con el tutorial, todavía hay mucha más información sobre los contenedores.
No vamos a profundizar aquí, pero aquí tiene algunas otras áreas que puede ver a continuación.

## <a name="container-orchestration"></a>Orquestación de contenedores

La ejecución de contenedores en producción es difícil. No quiere iniciar sesión en un equipo y simplemente ejecutar un `docker run` o `docker-compose up` . ¿Por qué no? ¿Qué ocurre si los contenedores se mueren? ¿Cómo se puede escalar en varias máquinas? La orquestación de contenedores resuelve este problema. Herramientas como Kubernetes, Swarm, Nomad y AKS All ayudan a resolver este problema de maneras ligeramente diferentes.

La idea general es que tiene "administradores" que reciben el **estado esperado**. Este estado puede ser "deseo ejecutar dos instancias de mi aplicación web y exponer el puerto 80". A continuación, los administradores examinan todas las máquinas del clúster y delegan el trabajo en nodos de "trabajo". Los administradores inspeccionan los cambios (como el cierre de un contenedor) y, a continuación, trabajan para que el **estado real** refleje el estado esperado.

## <a name="cloud-native-computing-foundation-projects"></a>Proyectos de Cloud Native Computing Foundation

CNCF es un hogar independiente del proveedor para varios proyectos de código abierto, como Kubernetes, Prometheus, envío, Linkerd, NAT, etc. Puede ver los [proyectos graduados e incubados aquí](https://www.cncf.io/projects/) y todo el [panorama de CNCF aquí](https://landscape.cncf.io/). Hay muchos proyectos que le ayudarán a resolver problemas relacionados con la supervisión, el registro, la seguridad, los registros de imágenes, la mensajería, etc.

Por lo tanto, si no está familiarizado con el entorno de contenedor y el desarrollo de aplicaciones nativas de la nube, ¡ Bienvenido! Póngase en contacto con la comunidad, formule preguntas y siga aprendiendo. Nos complace tener tu cuenta.

## <a name="working-with-docker-in-vs-code"></a>Trabajar con Docker en VS Code

Más información sobre el uso de la extensión Docker de VS Code:

- [Información general sobre la extensión de Docker VS Code](https://code.visualstudio.com/docs/containers/overview)
- [Introducción a Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introducción a Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introducción a .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Depuración de aplicaciones en contenedor](https://code.visualstudio.com/docs/containers/debug-common)
