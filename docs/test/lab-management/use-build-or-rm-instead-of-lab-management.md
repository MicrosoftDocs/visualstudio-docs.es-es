---
title: Usar Build o Release Management para las pruebas automatizadas | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 8d843800666ae53a686a18fcab28d02eb4c16743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Usar Build y Release Management en lugar de Lab Management para las pruebas automatizadas

Si usa Microsoft Test Manager (MTM) y Lab Management para las pruebas automatizadas o para la automatización de compilación-implementación-prueba, en este tema se explica cómo puede obtener los mismos objetivos con las características de [Build &amp; Release](https://www.visualstudio.com/team-services/continuous-integration/) en Team Foundation Server (TFS) y Visual Studio Team Services:

* [Automatización de compilación-implementación-prueba](#bdtautomation)

* [Administración de autoservicio de entornos de SCVMM](#managescvmm)

Build y Release Management no admiten la creación autoservicio de entornos de SCVMM con aislamiento de red, y no existen planes para proporcionar esta compatibilidad en el futuro. En cambio, existen algunas [alternativas sugeridas](#isolatedenvir).

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>Automatización de compilación-implementación-prueba

MTM y Lab Management se basan en una definición de compilación XAML para automatizar la compilación, implementación y prueba de sus aplicaciones.
La compilación XAML se basa en varios constructores que se han creado en MTM como un entorno de laboratorio, conjuntos de pruebas y configuración de pruebas, y en varios componentes de infraestructura como un controlador de compilación, agentes de compilación, controlador de pruebas y agentes de pruebas para conseguir este objetivo. Puede conseguir lo mismo con menos pasos mediante Build o Release Management en TFS y Team Services.

| Pasos | Con la compilación XAML | Con Build o Release Management |
|-------|----------------------|-----------------|
| Identificar las máquinas donde se implementará la compilación y se ejecutarán las pruebas. | Cree un entorno de laboratorio estándar en MTM con esas máquinas. | N/D |
| Identificar las pruebas que se van a ejecutar. | Cree un conjunto de pruebas en MTM, cree casos de pruebas y asocie la automatización con cada caso de prueba. Cree una configuración de pruebas en MTM identificando el rol de las máquinas del entorno de laboratorio donde deben ejecutarse las pruebas. | Cree un conjunto de pruebas automatizado en MTM de la misma manera que si planea administrar sus pruebas mediante planes de pruebas. De manera alternativa, puede omitir esto si quiere ejecutar pruebas directamente desde archivos binarios de prueba creados mediante sus compilaciones. No hay necesidad de crear configuraciones de pruebas en ningún caso. |
| Automatizar la implementación y las pruebas. | Cree una definición de compilación XAML con LabDefaultTemplate.*.xaml. Especifique la compilación, conjuntos de pruebas y entorno de laboratorio en la definición de compilación. | Cree una [definición de compilación o una definición de versión](https://www.visualstudio.com/team-services/continuous-integration/) con un solo entorno. Ejecute el mismo script de implementación (desde la definición de compilación XAML) con la tarea de línea de comandos y ejecute pruebas automatizadas con las tareas Implementación del agente de pruebas y Ejecutar pruebas funcionales. Especifique la lista de máquinas y sus credenciales como entradas para estas tareas. |

Algunas de las ventajas de usar Build o Release Management para este escenario son:

* No necesita un controlador de compilación o Test Controller.
* Test Agent se instala mediante una tarea como parte de la compilación o versión.
* Es sencillo personalizar los pasos de implementación. Ya no está limitado a usar un solo script. También puede aprovecharse de muchas tareas que están disponibles en el producto así como en Visual Studio Marketplace.
* No tiene que mantener conjuntos de pruebas. Puede ejecutar pruebas de archivos binarios directamente.
* Obtiene una experiencia de informes en línea enriquecida para las pruebas que se han ejecutado en cada compilación o versión.
* Puede realizar un seguimiento de qué recursos (versión, compilación, elementos de trabajo, confirmaciones) están implementados y se prueban actualmente en cada entorno.
* Puede personalizar y ampliar la automatización para implementarse fácilmente en varios entornos de prueba, e incluso en la producción.
* Puede programar la automatización para que suceda cuando exista una comprobación o confirmación, o en un momento determinado de cada día.

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>Administración de autoservicio de entornos de SCVMM

El [Centro de laboratorio en Microsoft Test Manager](https://msdn.microsoft.com/library/dd997438.aspx) admite la capacidad de administrar una biblioteca de plantillas de entorno así como aprovisionar entornos bajo petición mediante un [servidor de SCVMM](https://technet.microsoft.com/system-center-docs/vmm/vmm).

Las características de aprovisionamiento de autoservicio del Centro de laboratorio tienen dos objetivos distintos:

* Proporcionar una manera más sencilla de administrar la infraestructura. Administrar plantillas de entorno y VM y crear automáticamente redes privadas para aislar clones de entornos entre sí eran ejemplos de la administración de infraestructura.

* Proporcionar una manera más sencilla para que los equipos usen las máquinas virtuales en sus actividades de implementación y pruebas. Hacer que los entornos de laboratorio sean accesibles mediante el mismo modelo de seguridad de proyectos de equipo y un uso integrado de esas máquinas virtuales en los escenarios de prueba eran ejemplos del uso sencillo.

En cambio, dada la evolución de los sistemas de administración en la nube públicos y privados enriquecidos como [Microsoft Azure](https://azure.microsoft.com/) y [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), no existe ninguna evolución de las características de administración de infraestructuras en TFS 2017 y versiones posteriores. En su lugar, el foco del uso sencillo de los recursos administrados mediante dichas infraestructuras de nube continúa.

En la tabla siguiente se resumen las actividades típicas que ha usado para realizar tareas en el centro de laboratorio y cómo puede realizarlas mediante SCVMM o Azure (si son actividades de administración de infraestructuras) o mediante TFS y Team Services (si son actividades de implementación o pruebas):

| Pasos | Con el centro de laboratorio | Con Build o Release Management |
|-------|----------------------|-----------------|
| Administrar una biblioteca de plantillas de entorno. | Cree un entorno de laboratorio. Instale el software necesario en las máquinas virtuales. Prepare el sistema y almacene el entorno como una plantilla en la biblioteca. | Use la consola de administración de SCVMM directamente para crear y administrar cualquier plantilla de máquina virtual o plantillas de servicio. Al usar Azure, seleccione una de las [plantillas de Azure Resource Manager](https://azure.microsoft.com/documentation/templates/) predefinidas de [Azure Marketplace](https://azure.microsoft.com/marketplace/) o de las [plantillas de inicio rápido de Azure](https://azure.microsoft.com/documentation/templates/). |
| Crear un entorno de laboratorio. | Seleccione una plantilla de entorno en la biblioteca e impleméntela. Proporcione los parámetros necesarios para personalizar las configuraciones de máquina virtual. | Use la consola de administración de SCVMM directamente para crear máquinas virtuales o instancias de servicio de las plantillas. Use Azure Portal directamente para crear recursos. O, cree una definición de versión con un entorno. Use las tareas de Azure o las tareas de la [extensión de integración de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) para crear máquinas virtuales. Crear una versión de esta definición es equivalente a crear un entorno en el centro de laboratorio. |
| Conectarse a las máquinas. | Abra el entorno de laboratorio en el Visor de entorno. | Use la consola de administración de SCVMM directamente para conectarse a las máquinas virtuales. De manera alternativa, use la dirección IP o los nombres DNS de las máquinas virtuales para abrir las sesiones de escritorio remoto. |
| Tomar un punto de control de un entorno o restaurar un entorno a un punto de control limpio. | Abra el entorno de laboratorio en el Visor de entorno. Seleccione la opción para tomar un punto de control o para restaurar a un punto de control anterior. | Use la consola de administración de SCVMM directamente para realizar estas operaciones en las máquinas virtuales. O, para realizar estos pasos como parte de una automatización mayor, incluya las tareas de punto de control desde la [extensión de integración de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) como parte del entorno en una definición de versión. |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>Creación autoservicio de entornos con aislamiento de red

Un entorno de laboratorio con aislamiento de red es un grupo de máquinas virtuales de SCVMM que puede clonarse de manera segura sin provocar conflictos de red. Esto se realizaba en MTM con una serie de instrucciones que usaban un conjunto de tarjetas adaptadoras de red para configurar las máquinas virtuales en una red privada, y otro conjunto de tarjetas adaptadoras de red para configurar las máquinas virtuales en una red pública.

Con la evolución de sistemas de administración de nube públicos y privados enriquecidos como [Microsoft Azure](https://azure.microsoft.com/) y [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), puede basarse más en las herramientas de administración de nube directamente para obtener funciones similares. No existe una manera equivalente de conseguir este objetivo en Build y Release Management.

Se recomienda que considere las siguientes alternativas si necesita un aislamiento de red:

* Una motivación para el aislamiento de red ha sido la facilidad de configuración de varios clones. Como cada clon es una réplica exacta del original, los nombres de equipo y las opciones de configuración se mantienen como están, y esto facilita la configuración de entornos nuevos. En cambio, la misma ventaja provoca problemas que aparecen después en el ciclo de vida (por ejemplo, en la producción) porque la manera en que las aplicaciones se implementan finalmente no es la misma. **En su lugar**, considere la configuración de nuevos entornos de la misma manera que configura la producción, y evite usar el aislamiento de red.

* Use una infraestructura de nube pública como [Microsoft Azure](https://azure.microsoft.com/) para sus necesidades de prueba. Puede usar fácilmente [plantillas de Azure Resource Manager](https://azure.microsoft.com/documentation/templates/) desde [Azure Marketplace](https://azure.microsoft.com/marketplace/) o desde las [plantillas de inicio rápido de Azure](https://azure.microsoft.com/documentation/templates/) para configurar grupos de máquinas virtuales que están conectados mediante una red privada, y están expuestos a la red pública solo con un proxy o "jumpbox".
