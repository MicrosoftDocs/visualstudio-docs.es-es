---
title: Uso de un entorno de laboratorio para DevOps
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7ec0e4eed9036a0548c4f8f162331e92a416c0cb
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144693"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Usar un entorno de laboratorio para DevOps

Un entorno de laboratorio es una colección de máquinas virtuales y físicas que se pueden usar para desarrollar y probar las aplicaciones. Un entorno de laboratorio puede contener varios roles necesarios para probar aplicaciones de varios niveles, como estaciones de trabajo, servidores web y servidores de bases de datos. Además, puede usar un flujo de trabajo de compilación-implementación-prueba con el entorno de laboratorio a fin de automatizar el proceso de compilación, implementación y ejecución de pruebas automatizadas en su aplicación.

* **Usar un plan de pruebas para ejecutar pruebas automatizadas**: puede ejecutar una colección de pruebas automatizadas, denominado *plan de pruebas*, y ver el progreso.

* **Usar un flujo de trabajo de compilación-implementación-prueba**: puede usar un flujo de trabajo de compilación-implementación-prueba para probar automáticamente aplicaciones de varios niveles. Un ejemplo típico es un flujo de trabajo que comienza con una compilación, implementa los archivos de compilación en los equipos adecuados en un entorno de laboratorio y, después, ejecuta pruebas automatizadas. Además, puede programar el flujo de trabajo para que se ejecute a intervalos específicos.

* **Recopilar datos de diagnóstico de todos los equipos, incluso durante las pruebas manuales**: puede recopilar datos de diagnóstico de varios equipos de manera simultánea. Por ejemplo, durante una serie de pruebas puede recopilar datos de IntelliTrace, impacto en las pruebas y otras formas de datos de un servidor web, un servidor de bases de datos y un cliente.

Estos son algunos ejemplos de topologías comunes de entornos de laboratorio:

| Topología | Description |
|---|---|
|![Topología de servidor único](../media/topology_backend.png)| Este entorno de laboratorio tiene una *topología de servidores*, que suele usarse para ejecutar pruebas manuales en aplicaciones de servidor y que permite a los evaluadores usar sus propios equipos cliente para comprobar errores en el entorno. En una topología de backend, el entorno de laboratorio solo contiene servidores. Al usar este tipo de topología, normalmente se conecta a los servidores del entorno de laboratorio mediante un equipo cliente que no forma parte del entorno.|
|![Entorno de laboratorio en la nube](../media/topology_cloud.png)| Este entorno de laboratorio proporciona funciones y características similares como la _topología de servidores_, pero elimina la necesidad de que las máquinas virtuales o físicas se ejecuten en un entorno local; lo que puede reducir el tiempo de preparación, simplificar el mantenimiento y minimizar costos. Configurar varios sitios web y máquinas vituales, junto con redes personalizadas, es rápido y sencillo en un entorno de nube como Microsoft Azure.|
|![Entorno de laboratorio cliente-servidor](../media/topology_clientserver.png)| Este entorno de laboratorio tiene una *topología de cliente/servidor*, que suele usarse para probar una aplicación que tiene componentes de servidor y de cliente. En una topología de cliente/servidor, todos los equipos cliente y los equipos servidor usados para probar la aplicación se encuentran en el entorno de laboratorio. Al usar esta topología, puede recopilar datos de prueba de todos los equipos que afecten a las pruebas.|

:::row:::
    :::column:::
        ![icono de cámara de película para vídeo](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        [Vea un vídeo](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) sobre la administración de entornos de laboratorio para pruebas.
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Uso de la nube con Azure Pipelines o Compilación y versión de Team Foundation Server

Puede realizar pruebas automatizadas y una automatización de compilación-implementación-prueba con las características de [compilación y versión](/azure/devops/pipelines/index?view=vsts) de Team Foundation Server (TFS) y Azure Test Plans. Estas son algunas de las ventajas:

* No necesita un controlador de compilación o Test Controller.
* Test Agent se instala mediante una tarea como parte de la compilación o versión.
* Es sencillo personalizar los pasos de implementación. Ya no está limitado a usar un solo script. También puede aprovecharse de muchas tareas que están disponibles en el producto así como en Visual Studio Marketplace.
* No tiene que mantener conjuntos de pruebas. Puede ejecutar pruebas de archivos binarios directamente.
* Obtiene una experiencia de informes en línea enriquecida para las pruebas que se han ejecutado en cada compilación o versión.
* Puede realizar un seguimiento de qué recursos (versión, compilación, elementos de trabajo, confirmaciones) están implementados y se prueban actualmente en cada entorno.
* Puede personalizar y ampliar la automatización para implementarse fácilmente en varios entornos de prueba, e incluso en la producción.
* Puede programar la automatización para que suceda cuando exista una comprobación o confirmación, o en un momento determinado de cada día.

Para obtener más información, consulte [Usar Build y Release Management](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Usar las características de Visual Studio Lab Management de Microsoft Test Manager

Puede crear y administrar entornos de laboratorio con las características de Visual Studio Lab Management de Microsoft Test Manager cuando use la edición Visual Studio Enterprise.

Lab Management instala automáticamente agentes de prueba en todos los equipos del entorno.

Si usa Lab Management con System Center Virtual Machine Manager (SCVMM), también obtendrá estas ventajas al usar entornos de laboratorio:

* **Reproducir rápidamente configuraciones de equipo**: puede almacenar colecciones de máquinas virtuales configuradas para recrear entornos de producción típicos. Después, puede ejecutar cada serie de pruebas en una copia nueva de un entorno almacenado.

* **Reproducir las condiciones exactas de un error**: cuando una serie de pruebas produce errores, puede almacenar una copia del estado del entorno de laboratorio y acceder a esta desde los resultados de compilación o desde un elemento de trabajo.

* **Ejecutar varias copias de un entorno de laboratorio de forma simultánea**: puede ejecutar varias copias del entorno de laboratorio a la vez, sin que se produzcan conflictos de nombres.

### <a name="standard-environments-and-scvmm-environments"></a>Entornos estándar y entornos de SCVMM

Existen dos tipos de entornos de laboratorio que puede crear con Visual Studio Lab Management: **entornos estándar** y **entornos de SCVMM**. Pero las capacidades de cada tipo de entorno son distintas.

Los **entornos estándar** pueden contener una combinación de máquinas virtuales y físicas. También se pueden agregar máquinas virtuales a un entorno estándar que esté administrado por marcos de virtualización de terceros. Además, los entornos estándar no requieren recursos de servidor adicionales, como un servidor SCVMM.

Los **entornos de SCVMM** solo pueden contener máquinas virtuales administradas por SCVMM (System Center Virtual Machine Manager), por lo que las máquinas virtuales de entornos de SCVMM solo se pueden ejecutar en el marco de virtualización de Hyper-V. Pero los entornos de SCVMM proporcionan las siguientes características de automatización y administración que no están disponibles en los entornos estándar:

- **Instantáneas de entorno:** las instantáneas de entorno contienen el estado de un entorno de laboratorio, por lo que permiten restaurar rápidamente un entorno limpio o guardar el estado de un entorno modificado. También puede usar un flujo de trabajo de compilación-implementación-prueba para automatizar el proceso de guardado y restauración de instantáneas de entorno.

- **Entornos almacenados:** puede almacenar una copia de un entorno de SCVMM y, después, implementar varias copias de dicho entorno.

- **Aislamiento de red:** el aislamiento de red permite ejecutar de forma simultánea varias copias idénticas de un entorno de SCVMM sin que se produzcan conflictos de nombre de equipo.

- **Plantillas de máquinas virtuales:** una plantilla de máquina virtual es una máquina virtual de la que se eliminaron el nombre y otros identificadores. Cuando se implementa una plantilla de VM en un entorno de SCVMM, Microsoft Test Manager genera nuevos identificadores. Esto permite implementar varias copias de una máquina virtual en el mismo entorno (o en varios entornos) y, después, ejecutarlas de forma simultánea.

- **Máquinas virtuales almacenadas:** una máquina virtual que se almacena en la biblioteca del proyecto y que incluye identificadores únicos.

> [!NOTE]
> Lab Management no admite SCVMM 2016.

Para obtener información sobre SCVMM, vea [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts).

Los entornos estándar y los entornos de SCVMM admiten un gran número de características similares. Pero es importante conocer algunas diferencias importantes. En la tabla siguiente se comparan las características que están disponibles para entornos estándar y para entornos de SCVMM.

|Función|Entornos de SCVMM|Entornos estándar|
|-|------------------------|-|
|**Pruebas**|||
|Ejecutar pruebas manuales|Compatible|Compatible|
|Ejecutar IU codificada y otras pruebas automatizadas|Compatible|Compatible|
|Notificar sobre errores detallados mediante adaptadores de diagnóstico|Compatible|Compatible|
|**Implementación de compilaciones**|||
|Flujos de trabajo de compilación-implementación-prueba automáticos|Compatible|Compatible|
|**Creación y administración de entornos**|||
|Uso de máquinas físicas además de máquinas virtuales|No compatibles|Compatible|
|Uso de máquinas virtuales de terceros|No compatibles|Compatible|
|Instalación automática de agentes de prueba en equipos del entorno de laboratorio|Compatible|Compatible|
|Guardar e implementar el estado de un entorno de laboratorio mediante instantáneas de entorno|Compatible|No compatibles|
|Creación de entornos de laboratorio a partir de plantillas de VM|Compatible|No compatibles|
|Iniciar, detener y crear instantáneas de entornos|Compatible|No compatibles|
|Conectar al entorno mediante el Visor de entorno|Compatible|Compatible|
|Ejecutar varias copias de un entorno de forma simultánea mediante el aislamiento de red|Compatible|No compatibles|

### <a name="lab-management-concepts"></a>Conceptos de Lab Management

Estos son algunos conceptos adicionales que es importante que conozca antes de continuar:

|Término|Description|
|-|-----------------|
|Centro de laboratorio|El área de Microsoft Test Manager donde se crean y administran los entornos de laboratorio.|
|Laboratorio de proyecto de Azure DevOps|La colección de entornos de laboratorio que se han configurado para que pueda conectarse a estos y ejecutar sus máquinas virtuales.|
|Biblioteca de proyecto de Azure DevOps|Un archivo de máquinas virtuales almacenadas, plantillas y entornos de laboratorio almacenados que se han importado en el grupo host del proyecto. Puede usar los elementos de la biblioteca con entornos de SCVMM, pero no puede agregarlos directamente a un entorno estándar. No puede ejecutar los elementos en la biblioteca, sino que deberá usarlos para implementar un nuevo entorno.|
|Entorno implementado|Un entorno de laboratorio que se ha implementado en un laboratorio de proyecto para que pueda conectarse a este y ejecutar sus equipos.|

Para obtener más información acerca de Lab Management, vea:

* [Planear el laboratorio](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Administrar su laboratorio](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Configurar los entornos de SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Administrar permisos](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Cambiar la configuración](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Solución de problemas](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Para obtener información sobre la configuración de entornos, vea:

* [Entornos de nube de Build y Release](use-build-or-rm-instead-of-lab-management.md)
* [Entornos de laboratorio estándar](https://msdn.microsoft.com/library/ee390842.aspx)
* [Entornos de SCVMM (virtuales)](https://msdn.microsoft.com/library/ee943322.aspx)
* [Crear y usar un entorno con aislamiento de red](https://msdn.microsoft.com/library/ee518924.aspx)
::: moniker-end

## <a name="see-also"></a>Vea también

* [Instalar y configurar agentes de prueba](../../test/lab-management/install-configure-test-agents.md)
* [Guía de Visual Studio Lab Management](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2015/04/22/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions/)
* [Blog DevOps de Microsoft](https://devblogs.microsoft.com/devops/)
