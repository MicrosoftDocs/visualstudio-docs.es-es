---
title: Usar un entorno de laboratorio para DevOps | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: lab environment, test lab
ms.assetid: b435eb39-dc7c-46fa-a91b-6e6dd614f01c
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 2eb863996b430c8473adb751851777c532fcfc89
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="use-a-lab-environment-for-your-devops"></a>Usar un entorno de laboratorio para DevOps

Un entorno de laboratorio es una colección de máquinas virtuales y físicas que se pueden usar para desarrollar y probar aplicaciones. Un entorno de laboratorio puede contener varios roles necesarios para probar aplicaciones de varios niveles, como estaciones de trabajo, servidores web y servidores de bases de datos. Además, puede usar un flujo de trabajo de compilación-implementación-prueba con el entorno de laboratorio a fin de automatizar el proceso de compilación, implementación y ejecución de pruebas automatizadas en su aplicación.

* **Usar un plan de pruebas para ejecutar pruebas automatizadas**: puede ejecutar una colección de pruebas automatizadas, denominado *plan de pruebas*, y ver el progreso.  
  
* **Usar un flujo de trabajo de compilación-implementación-prueba**: puede usar un flujo de trabajo de compilación-implementación-prueba para probar automáticamente aplicaciones de varios niveles. Un ejemplo típico es un flujo de trabajo que comienza con una compilación, implementa los archivos de compilación en los equipos adecuados en un entorno de laboratorio y, después, ejecuta pruebas automatizadas. Además, puede programar el flujo de trabajo para que se ejecute a intervalos específicos.  
  
* **Recopilar datos de diagnóstico de todos los equipos, incluso durante las pruebas manuales**: puede recopilar datos de diagnóstico de varios equipos de manera simultánea. Por ejemplo, durante una serie de pruebas puede recopilar datos de IntelliTrace, impacto en las pruebas y otras formas de datos de un servidor web, un servidor de bases de datos y un cliente.  
  
Estos son algunos ejemplos comunes de entornos de laboratorio:  
  
| Topología | Descripción |  
|---|---|  
|![Topología de servidor único](../media/topology_backend.png)| Este entorno de laboratorio tiene una *topología de servidores*, que suele usarse para ejecutar pruebas manuales en aplicaciones de servidor y que permite a los evaluadores usar sus propios equipos cliente para comprobar errores en el entorno. En una topología de backend, el entorno de laboratorio solo contiene servidores. Al usar este tipo de topología, normalmente se conecta a los servidores del entorno de laboratorio mediante un equipo cliente que no forma parte del entorno.|  
|![Entorno de laboratorio en la nube](../media/topology_cloud.png)| Este entorno de laboratorio proporciona funciones y características similares como la _topología de servidores_, pero elimina la necesidad de que las máquinas virtuales o físicas se ejecuten en un entorno local; lo que puede reducir el tiempo de preparación, simplificar el mantenimiento y minimizar costos. Configurar varios sitios web y máquinas vituales, junto con redes personalizadas, es rápido y sencillo en un entorno de nube como Microsoft Azure. [Más información](#usebandrm).|  
|![Entorno de laboratorio cliente-servidor](../media/topology_clientserver.png)| Este entorno de laboratorio tiene una *topología de cliente/servidor*, que suele usarse para probar una aplicación que tiene componentes de servidor y de cliente. En una topología de cliente/servidor, todos los equipos cliente y los equipos servidor usados para probar la aplicación se encuentran en el entorno de laboratorio. Al usar esta topología, puede recopilar datos de prueba de todos los equipos que afecten a las pruebas.|  
  
Vea [Vídeo: Administración de entornos de laboratorio para pruebas](http://go.microsoft.com/fwlink/?LinkID=252614).  
  
Las técnicas típicas para configurar un entorno de laboratorio son: 
  
* **[Usar la nube con Team Services o Team Foundation Server Build &amp; Release](#usebandrm)**

* **[Usar las características de Visual Studio Lab Management de Microsoft Test Manager](#usemtmlm)**

<a name="usebandrm"></a>
## <a name="use-the-cloud-with-team-services-or-team-foundation-server-build-amp-release"></a>Usar la nube con Team Services o Team Foundation Server Build &amp; Release

Puede realizar pruebas automatizadas y una automatización de compilación-implementación-prueba con las características [Build &amp; Release](https://www.visualstudio.com/team-services/continuous-integration/) de Team Foundation Server (TFS) y Visual Studio Team Services. Estas son algunas de las ventajas:

* No necesita un controlador de compilación o Test Controller.
* Test Agent se instala mediante una tarea como parte de la compilación o versión.
* Es sencillo personalizar los pasos de implementación. Ya no está limitado a usar un solo script. También puede aprovecharse de muchas tareas que están disponibles en el producto así como en Visual Studio Marketplace.
* No tiene que mantener conjuntos de pruebas. Puede ejecutar pruebas de archivos binarios directamente.
* Obtiene una experiencia de informes en línea enriquecida para las pruebas que se han ejecutado en cada compilación o versión.
* Puede realizar un seguimiento de qué recursos (versión, compilación, elementos de trabajo, confirmaciones) están implementados y se prueban actualmente en cada entorno.
* Puede personalizar y ampliar la automatización para implementarse fácilmente en varios entornos de prueba, e incluso en la producción.
* Puede programar la automatización para que suceda cuando exista una comprobación o confirmación, o en un momento determinado de cada día.

[Más información](use-build-or-rm-instead-of-lab-management.md).

<a name="usemtmlm"></a>
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Usar las características de Visual Studio Lab Management de Microsoft Test Manager

Puede crear y administrar entornos de laboratorio con las características de Visual Studio Lab Management de Microsoft Test Manager cuando use Visual Studio Enterprise o Visual Studio Test Professional.

Lab Management instala automáticamente agentes de prueba en todos los equipos del entorno.  
  
Si usa Lab Management con System Center Virtual Machine Manager (SCVMM), también puede obtener estas ventajas al usar entornos de laboratorio:  
  
* **Reproducir rápidamente configuraciones de equipo**: puede almacenar colecciones de máquinas virtuales configuradas para recrear entornos de producción típicos. Después, puede ejecutar cada serie de pruebas en una copia nueva de un entorno almacenado.  
  
* **Reproducir las condiciones exactas de un error**: cuando una serie de pruebas produce errores, puede almacenar una copia del estado del entorno de laboratorio y acceder a esta desde los resultados de compilación o desde un elemento de trabajo.  
  
* **Ejecutar varias copias de un entorno de laboratorio de forma simultánea**: puede ejecutar varias copias del entorno de laboratorio a la vez, sin que se produzcan conflictos de nombres.  
  
### <a name="standard-environments-and-scvmm-environments"></a>Entornos estándar y entornos de SCVMM

Existen dos tipos de entornos de laboratorio que puede crear con Visual Studio Lab Management: **entornos estándar** y **entornos de SCVMM**.
Pero las capacidades de cada tipo de entorno son distintas.  
  
> **NOTA**: Lab Management **no** admite SCVMM 2016. Para obtener información sobre SCVMM, vea [Virtual Machine Manager](http://go.microsoft.com/fwlink/?LinkId=226332). 
  
Los **entornos estándar** pueden contener una combinación de máquinas virtuales y físicas. También se pueden agregar máquinas virtuales a un entorno estándar que esté administrado por marcos de virtualización de terceros. Además, los entornos estándar no requieren recursos de servidor adicionales, como un servidor SCVMM.  
  
Los **entornos de SCVMM** solo pueden contener máquinas virtuales administradas por SCVMM (System Center Virtual Machine Manager), por lo que las máquinas virtuales de entornos de SCVMM solo se pueden ejecutar en el marco de virtualización de Hyper-V. Pero los entornos de SCVMM proporcionan las siguientes características de automatización y administración que no están disponibles en los entornos estándar:  
  
- **Instantáneas de entorno:** las instantáneas de entorno contienen el estado de un entorno de laboratorio, por lo que permiten restaurar rápidamente un entorno limpio o guardar el estado de un entorno modificado. También puede usar un flujo de trabajo de compilación-implementación-prueba para automatizar el proceso de guardado y restauración de instantáneas de entorno.  
  
- **Entornos almacenados:** puede almacenar una copia de un entorno de SCVMM y, después, implementar varias copias de dicho entorno.  
  
- **Aislamiento de red:** el aislamiento de red permite ejecutar de forma simultánea varias copias idénticas de un entorno de SCVMM sin que se produzcan conflictos de nombre de equipo.  
  
- **Plantillas de máquinas virtuales:** una plantilla de máquina virtual es una máquina virtual de la que se eliminaron el nombre y otros identificadores. Cuando se implementa una plantilla de VM en un entorno de SCVMM, Microsoft Test Manager genera nuevos identificadores. Esto permite implementar varias copias de una máquina virtual en el mismo entorno (o en varios entornos) y, después, ejecutarlas de forma simultánea.  
  
- **Máquinas virtuales almacenadas:** una máquina virtual que se almacena en la biblioteca de proyecto de equipo y que incluye identificadores únicos.  
  
Para obtener más información sobre estas características, vea [Guía para crear y administrar entornos SCVMM](https://msdn.microsoft.com/en-gb/library/ee830480.aspx).  
  
Los entornos estándar y los entornos de SCVMM admiten un gran número de características similares. Pero es importante conocer algunas diferencias importantes. En la tabla siguiente se comparan las características que están disponibles para entornos estándar y para entornos de SCVMM.  
  
|Función|Entornos de SCVMM|Entornos estándar|  
|----------------|------------------------|---------------------------|  
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
  
|Término|Descripción|  
|----------|-----------------|  
|Centro de laboratorio|El área de Microsoft Test Manager donde se crean y administran los entornos de laboratorio.|  
|Laboratorio de proyecto de equipo|La colección de entornos de laboratorio que se han configurado para que pueda conectarse a estos y ejecutar sus máquinas virtuales.|  
|Biblioteca de proyecto de equipo|Un archivo de máquinas virtuales almacenadas, plantillas y entornos de laboratorio almacenados que se han importado en el grupo host del proyecto de equipo. Puede usar los elementos de la biblioteca con entornos de SCVMM, pero no puede agregarlos directamente a un entorno estándar. No puede ejecutar los elementos en la biblioteca, sino que deberá usarlos para implementar un nuevo entorno.|  
|Entorno implementado|Un entorno de laboratorio que se ha implementado en un laboratorio de proyecto de equipo para que pueda conectarse a este y ejecutar sus equipos.|  

#### <a name="related-topics"></a>Temas relacionados

* [Planear el laboratorio](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx) 
* [Administrar su laboratorio](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx) 
* [Configurar los entornos de SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx) 
* [Actualizar SCVMM 2008 R2 a SCVMM 2012](upgrade-scvmm-2008-r2-scvmm-2012.md) 
* [Administrar permisos](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx) 
* [Cambiar la configuración](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx) 
* [Solución de problemas](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)
  
### <a name="set-up-environments"></a>Configurar entornos

* [Entornos de nube de Build &amp; Release](use-build-or-rm-instead-of-lab-management.md)
* [Entornos de laboratorio estándar](https://msdn.microsoft.com/en-gb/library/ee390842.aspx)
* [Entornos de SCVMM (virtuales)](https://msdn.microsoft.com/en-gb/library/ee943322.aspx)
* [Crear y usar un entorno con aislamiento de red](https://msdn.microsoft.com/en-gb/library/ee518924.aspx)
  
## <a name="see-also"></a>Vea también
  
* [Instalar y configurar agentes de prueba](install-configure-test-agents.md)
* [Guía de Visual Studio Lab Management](http://go.microsoft.com/fwlink/?LinkID=230951)  
* [Administración de entornos de laboratorio para pruebas](http://go.microsoft.com/fwlink/?LinkID=252614)  
* [Blog de Visual Studio DevOps + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
