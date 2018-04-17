---
title: Consideraciones sobre las soluciones en espacio aislado | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff85f3407fb24d6d49856bb11ff1852c544cad35
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *Soluciones en espacio aislado* son una característica de Microsoft SharePoint 2010 que permite a los usuarios de la colección de sitios cargar sus propias soluciones de código personalizado. Una solución en espacio aislado habitual es a los usuarios cargar sus propios elementos Web.  
  
 Una aplicación de SharePoint en espacio aislado se ejecuta en un proceso seguro y supervisado que tiene acceso a una parte limitada de la granja de servidores Web. Microsoft SharePoint 2010 utiliza una combinación de características, galerías de soluciones, solución de supervisión y un marco de validación para habilitar las soluciones en espacio aislado.  
  
## <a name="specifying-project-trust-level"></a>Especificar el nivel de confianza del proyecto  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] admite soluciones en espacio aislado a través de una propiedad de proyecto booleana denominadas *solución en espacio aislado*. Esta propiedad puede establecerse en cualquier momento en el proyecto, o puede especificarse cuando se crea el proyecto en el **Asistente para personalización de SharePoint**.  
  
> [!NOTE]  
>  Cambiar el *solución en espacio aislado* propiedad de un proyecto tras su creación puede provocar errores de validación.  
  
 La solución se considera una solución de granja de servidores de ámbito si la *solución en espacio aislado* propiedad está establecida en **false** o elegir la **implementar como solución de granja de servidores** opción. Sin embargo, la solución recibe un tratamiento diferente de una solución de granja de servidores si la *solución en espacio aislado* propiedad está establecida en **true** o elegir la **implementar como una solución en espacio aislado** opción en el asistente.  
  
## <a name="sharepoint-site-hierarchy"></a>Jerarquía de sitios de SharePoint  
 Para comprender las soluciones en espacio aislado cómo funcionan, resulta útil para saber que los sitios de SharePoint son jerárquicos en ámbito. El elemento superior se conoce como la granja de servidores Web y otros elementos son subordinados a éste:  
  
 Granja de servidores Web  
  
 Aplicación Web A  
  
 Colección de sitios A1  
  
 Sitio A1a  
  
 Aplicación Web B  
  
 Colección de sitios B1  
  
 Sitio B1a  
  
 Sitio B1b  
  
 B2 de colección de sitio  
  
 Sitio B2a  
  
 Como puede ver, las granjas de servidores Web pueden contener una o más aplicaciones Web, que a su vez pueden contener una o varias colecciones de sitios, que pueden tener subsitios y así sucesivamente. Cambios efectuados en un efecto de la colección de sitio solo esa colección de sitios y ninguna otra. Sin embargo, los cambios realizados en el nivel de granja de servidores Web afectan a todas las colecciones de sitios en la granja de servidores.  
  
 Windows SharePoint Services (WSS) 3.0 le permite implementar soluciones en el nivel de granja, pero [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] le permite implementar el nivel de granja (solución de granja de servidores) o el nivel de colección de sitios (solución en espacio aislado).  
  
## <a name="why-sandboxed-solutions"></a>¿Por qué soluciones en espacio aislado?  
 En WSS 3.0, las soluciones se pudieron implementar sólo en el nivel de granja de servidores. Esto significaba que era posible implementar soluciones potencialmente dañinas o desestabilizadoras que afecta a toda la granja Web y todas las otras colecciones de sitios y aplicaciones que se ejecutan en él. Sin embargo, con las soluciones en espacio aislado, puede implementar sus soluciones en una subárea de la granja, una colección de sitios específica. Para proporcionar protección adicional, el ensamblado de la solución no se carga en el método main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] proceso (w3wp.exe). En su lugar, que se carga en un proceso independiente (SPUCWorkerProcess.exe). Este proceso se supervisa e implementa cuotas y limitación para proteger la granja de servidores de soluciones en espacio aislado que realizan actividades dañinas, como la ejecución de los bucles de pequeñas dimensiones que consumen ciclos de CPU.  
  
## <a name="site-collection-solution-gallery"></a>Galería de soluciones de colecciones de sitios  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 incluye una característica que se conoce como el "Galería de soluciones de sitio colección". Puede acceder a esta función desde la página de Administración Central de SharePoint 2010 o abriendo el **acciones del sitio** menú, elija **configuración del sitio**y, a continuación, elija la **soluciones** vincular en **galerías** en el sitio de SharePoint. Galerías de soluciones son repositorios de soluciones que permiten a los administradores de colección de sitio administrar las soluciones de sus colecciones de sitios.  
  
 La Galería de soluciones es una biblioteca de documentos almacenada en la raíz Web del sitio de SharePoint. La Galería de soluciones reemplaza las plantillas de sitio y admite paquetes de soluciones. Cuando se carga un archivo de paquete (.wsp) de solución de SharePoint, se procesa como una solución en espacio aislado.  
  
## <a name="sandboxed-solution-limitations"></a>Limitaciones de las soluciones en espacio aislado  
 Cuando se implementa una solución en espacio aislado, la matriz de funcionalidad de SharePoint a su disposición está limitada a ayudar a reducir las vulnerabilidades de seguridad puede tener. Algunas de estas limitaciones son las siguientes:  
  
-   Las soluciones en espacio aislado tienen un subconjunto restringido de elementos de la solución que se pueden implementar a su disposición. Plantillas de proyecto de SharePoint potencialmente vulnerables, como las definiciones de sitio y los flujos de trabajo, no están disponibles.  
  
-   SharePoint ejecuta código de la solución en espacio aislado en un proceso (SPUCWorkerProcess.exe) independiente en la página principal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] proceso (w3wp.exe) del grupo de aplicaciones.  
  
-   No se puede agregar las carpetas asignadas al proyecto.  
  
-   Tipos en la [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ensamblado Microsoft.Office.Server no se puede usar en soluciones en espacio aislado. Además, solo los tipos en el [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ensamblado Microsoft.SharePoint puede utilizarse en soluciones en espacio aislado.  
  
 Es importante tener en cuenta que si se especifica una solución de SharePoint como una solución en espacio aislado no tiene ningún efecto en el servidor de SharePoint; sólo determina cómo se implementa el proyecto de SharePoint en SharePoint desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y qué ensamblados enlaza a. No afecta al archivo .wsp generado, y el archivo .wsp no tiene datos que se correlaciona directamente con el *solución en espacio aislado* propiedad.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Capacidades y elementos de soluciones en espacio aislado  
 Soluciones en espacio aislado admiten las capacidades y elementos siguientes:  
  
-   Campos de tipos de contenido  
  
-   Acciones personalizadas  
  
-   Flujos de trabajo declarativos  
  
-   Receptores de eventos  
  
-   Llamadas de función  
  
-   Definiciones de lista  
  
-   Instancias de lista  
  
-   Módulo/archivos  
  
-   Navegación  
  
-   onet.Xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Compatibilidad con todos los elementos Web que se derivan de `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Elementos Web  
  
-   Elementos de la característica WebTemplate (en lugar de Webtemp.xml)  
  
-   Elementos Web visuales  
  
 Soluciones en espacio aislado no admiten las funciones y los elementos siguientes:  
  
-   Páginas de aplicación  
  
-   Grupo de acciones personalizadas  
  
-   Características de los ámbitos de granja de servidores  
  
-   `HideCustomAction` (elemento)  
  
-   Características de ámbito de la aplicación Web  
  
-   Flujos de trabajo con código  
  
## <a name="see-also"></a>Vea también  
 [Diferencias entre en un espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  