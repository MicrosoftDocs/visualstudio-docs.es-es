---
title: Uso de Azure Pipelines para las pruebas automatizadas
ms.date: 10/19/2018
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d9bb59a383db46fdfc3b7e5a9a2f429399630873
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949959"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Uso de Azure Test Plans en lugar de Lab Management para las pruebas automatizadas

Si usa Microsoft Test Manager y Lab Management para las pruebas automatizadas o para la automatización de compilación-implementación-prueba, en este tema se explica cómo puede obtener los mismos objetivos con las características de [compilación y versión](/azure/devops/pipelines/index?view=vsts) en Team Foundation Server (TFS) y Azure Pipelines.

## <a name="build-deploy-test-automation"></a>Automatización de compilación-implementación-prueba

Microsoft Test Manager y Lab Management se basan en una definición de compilación XAML para automatizar la compilación, implementación y prueba de sus aplicaciones. La compilación XAML se basa en varios constructores que se han creado en Microsoft Test Manager como un entorno de laboratorio, conjuntos de pruebas y configuración de pruebas, y en varios componentes de infraestructura como un controlador de compilación, agentes de compilación, controlador de pruebas y agentes de pruebas para conseguir este objetivo. Puede conseguir lo mismo con menos pasos mediante Azure Pipelines o TFS.

| Pasos | Con la compilación XAML | En una compilación o versión |
|-------|----------------------|-----------------|
| Identificar las máquinas donde se implementará la compilación y se ejecutarán las pruebas. | Cree un entorno de laboratorio estándar en Microsoft Test Manager con esas máquinas. | N/D |
| Identificar las pruebas que se van a ejecutar. | Cree un conjunto de pruebas en Microsoft Test Manager, cree casos de pruebas y asocie la automatización con cada caso de prueba. Cree una configuración de pruebas en Microsoft Test Manager identificando el rol de las máquinas del entorno de laboratorio donde deben ejecutarse las pruebas. | Cree un conjunto de pruebas automatizado en Microsoft Test Manager de la misma manera que si planea administrar sus pruebas mediante planes de pruebas. De manera alternativa, puede omitir esto si quiere ejecutar pruebas directamente desde archivos binarios de prueba creados mediante sus compilaciones. No hay necesidad de crear configuraciones de pruebas en ningún caso. |
| Automatizar la implementación y las pruebas. | Cree una definición de compilación XAML con LabDefaultTemplate.*.xaml. Especifique la compilación, conjuntos de pruebas y entorno de laboratorio en la definición de compilación. | Cree una [canalización de compilación o versión](/azure/devops/pipelines/index?view=vsts) con un solo entorno. Ejecute el mismo script de implementación (desde la definición de compilación XAML) con la tarea de línea de comandos y ejecute pruebas automatizadas con las tareas Implementación del agente de pruebas y Ejecutar pruebas funcionales. Especifique la lista de máquinas y sus credenciales como entradas para estas tareas. |

Algunas de las ventajas del uso de canalizaciones de Azure Pipelines o TFS para este escenario son:

* No necesita un controlador de compilación o Test Controller.
* Test Agent se instala mediante una tarea como parte de la compilación o versión.
* Es sencillo personalizar los pasos de implementación. Ya no está limitado a usar un solo script. También puede aprovecharse de muchas tareas que están disponibles en el producto así como en Visual Studio Marketplace.
* No tiene que mantener conjuntos de pruebas. Puede ejecutar pruebas de archivos binarios directamente.
* Obtiene una experiencia de informes en línea enriquecida para las pruebas que se han ejecutado en cada compilación o versión.
* Puede realizar un seguimiento de qué recursos (versión, compilación, elementos de trabajo, confirmaciones) están implementados y se prueban actualmente en cada entorno.
* Puede personalizar y ampliar la automatización para implementarse fácilmente en varios entornos de prueba, e incluso en la producción.
* Puede programar la automatización para que suceda cuando exista una comprobación o confirmación, o en un momento determinado de cada día.

## <a name="self-service-management-of-scvmm-environments"></a>Administración de autoservicio de entornos de SCVMM

El [Centro de pruebas en Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) admite la capacidad de administrar una biblioteca de plantillas de entorno así como aprovisionar entornos bajo petición mediante un [servidor de SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Las características de aprovisionamiento de autoservicio del Centro de laboratorio tienen dos objetivos distintos:

* Proporcionar una manera más sencilla de administrar la infraestructura. Administrar plantillas de entorno y VM y crear automáticamente redes privadas para aislar clones de entornos entre sí eran ejemplos de la administración de infraestructura.

* Proporcionar una manera más sencilla para que los equipos usen las máquinas virtuales en sus actividades de implementación y pruebas. Hacer que los entornos de laboratorio sean accesibles mediante el mismo modelo de seguridad de proyectos y un uso integrado de esas máquinas virtuales en los escenarios de prueba eran ejemplos del uso sencillo.

En cambio, dada la evolución de los sistemas de administración en la nube públicos y privados enriquecidos como [Microsoft Azure](https://azure.microsoft.com/) y [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), no existe ninguna evolución de las características de administración de infraestructuras en TFS 2017 y versiones posteriores. En su lugar, el foco del uso sencillo de los recursos administrados mediante dichas infraestructuras de nube continúa.

En la tabla siguiente se resumen las actividades típicas que se realizan en el centro de laboratorio y cómo puede llevarlas a cabo mediante SCVMM o Azure (si son actividades de administración de infraestructuras) o mediante TFS y Azure DevOps Services (si son actividades de implementación o pruebas):

| Pasos | Con el centro de laboratorio | En una compilación o versión |
|-------|-----------------|-----------------------|
| Administrar una biblioteca de plantillas de entorno. | Cree un entorno de laboratorio. Instale el software necesario en las máquinas virtuales. Prepare el sistema y almacene el entorno como una plantilla en la biblioteca. | Use la consola de administración de SCVMM directamente para crear y administrar cualquier plantilla de máquina virtual o plantillas de servicio. Si usa Azure, seleccione una de las [plantillas de inicio rápido de Azure](https://azure.microsoft.com/resources/templates/). |
| Crear un entorno de laboratorio. | Seleccione una plantilla de entorno en la biblioteca e impleméntela. Proporcione los parámetros necesarios para personalizar las configuraciones de máquina virtual. | Use la consola de administración de SCVMM directamente para crear máquinas virtuales o instancias de servicio de las plantillas. Use Azure Portal directamente para crear recursos. O, cree una definición de versión con un entorno. Use las tareas de Azure o las tareas de la [extensión de integración de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) para crear máquinas virtuales. Crear una versión de esta definición es equivalente a crear un entorno en el centro de laboratorio. |
| Conectarse a las máquinas. | Abra el entorno de laboratorio en el Visor de entorno. | Use la consola de administración de SCVMM directamente para conectarse a las máquinas virtuales. De manera alternativa, use la dirección IP o los nombres DNS de las máquinas virtuales para abrir las sesiones de escritorio remoto. |
| Tomar un punto de control de un entorno o restaurar un entorno a un punto de control limpio. | Abra el entorno de laboratorio en el Visor de entorno. Seleccione la opción para tomar un punto de control o para restaurar a un punto de control anterior. | Use la consola de administración de SCVMM directamente para realizar estas operaciones en las máquinas virtuales. O, para realizar estos pasos como parte de una automatización mayor, incluya las tareas de punto de control desde la [extensión de integración de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) como parte del entorno en una definición de versión. |

## <a name="create-network-isolated-environments"></a>Creación de entornos con aislamiento de red

Un entorno de laboratorio con aislamiento de red es un grupo de máquinas virtuales de SCVMM que puede clonarse de manera segura sin provocar conflictos de red. Esto se realizaba en MTM con una serie de instrucciones que usaban un conjunto de tarjetas adaptadoras de red para configurar las máquinas virtuales en una red privada, y otro conjunto de tarjetas adaptadoras de red para configurar las máquinas virtuales en una red pública.

Con todo, el uso combinado de Azure Pipelines y TFS con la tarea de compilación e implementación de SCVMM puede servir para administrar entornos de SCVMM, para aprovisionar redes virtuales aisladas y para implementar escenarios de compilación-implementación-prueba. Por ejemplo, puede usar la tarea para lo siguiente:

* Crear, restaurar y eliminar puntos de control
* Crear máquinas virtuales con una plantilla
* Iniciar y detener máquinas virtuales
* Ejecutar scripts de PowerShell personalizados para SCVMM

Para más información, vea [Create a virtual network isolated environment for build-deploy-test scenarios](/azure/devops/pipelines/targets/create-virtual-network?view=vsts) (Creación de un entorno con aislamiento de red virtual para escenarios de compilación-implementación-prueba).
