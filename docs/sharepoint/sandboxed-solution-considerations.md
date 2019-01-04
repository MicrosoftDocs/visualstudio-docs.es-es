---
title: Consideraciones sobre la solución en espacio aislado | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
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
ms.openlocfilehash: 4e26c87d3280ca3cfdd44baa11b09bd007eaca08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862106"
---
# <a name="sandboxed-solution-considerations"></a>Consideraciones sobre la solución en espacio aislado
  *Soluciones en espacio aislado* son una característica de Microsoft SharePoint 2010 que permite a los usuarios de la colección de sitio cargar sus propias soluciones de código personalizado. Una solución en espacio aislado común es a los usuarios cargar sus propios elementos Web.  
  
 Una aplicación en espacio aislado de SharePoint se ejecuta en un proceso supervisado seguro que tiene acceso a una parte limitada de la granja de servidores Web. Microsoft SharePoint 2010 utiliza una combinación de características, galerías de soluciones, solución de supervisión y un marco de validación para habilitar las soluciones en espacio aislado.  
  
## <a name="specify-project-trust-level"></a>Especifique el nivel de confianza del proyecto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] admite soluciones en espacio aislado a través de una propiedad de proyecto booleana denominadas *solución en espacio aislado*. Esta propiedad puede establecerse en cualquier momento en el proyecto, o puede especificarse cuando se crea el proyecto en el **Asistente de personalización de SharePoint**.  
  
> [!NOTE]  
>  Cambiar el *solución en espacio aislado* propiedad de un proyecto después de su creación puede producir errores de validación.  
  
 La solución se considera una solución con ámbito de granja de servidores si el *solución en espacio aislado* propiedad está establecida en **false** o elegir la **implementar como solución de granja de servidores** opción. Sin embargo, la solución recibe un tratamiento diferente de una solución de granja de servidores si el *solución en espacio aislado* propiedad está establecida en **true** o elegir la **implementar como solución en espacio aislado** opción en el asistente.  
  
## <a name="sharepoint-site-hierarchy"></a>Jerarquía de sitios de SharePoint
 Para comprender las soluciones en espacio aislado cómo trabajo, resulta útil para saber que los sitios de SharePoint son jerárquicos en el ámbito. El elemento superior se conoce como la granja de servidores Web y otros elementos están subordinados a éste:  
  
 Granja de servidores Web  
  
 Aplicación Web  
  
 Colección de sitios A1  
  
 Sitio A1a  
  
 Aplicación Web B  
  
 Colección de sitios B1  
  
 Sitio B1a  
  
 Sitio B1b  
  
 B2 de colección de sitio  
  
 Sitio B2a  
  
 Como puede ver, granjas de servidores Web pueden contener uno o más aplicaciones Web, que a su vez pueden contener una o varias colecciones de sitios, que pueden tener subsitios y así sucesivamente. Cambia realizadas a un efecto de colección de sitio solo esa colección y ninguna otra. Sin embargo, los cambios realizados en el nivel de granja de servidores Web afectan a todas las colecciones de sitios en la granja de servidores.  
  
 Windows SharePoint Services (WSS) 3.0 le permite implementar las soluciones sólo en el nivel de granja, pero [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] permite implementar en el nivel de granja (solución de granja) o el nivel de colección de sitios (solución en espacio aislado).  
  
## <a name="why-sandboxed-solutions"></a>¿Por qué soluciones en espacio aislado?
 WSS 3.0, las soluciones podrían implementarse solo en el nivel de granja. Esto significaba que podrían implementarse potencialmente dañinos o desestabilizadores se realizaron las soluciones que afecta a toda la granja Web y a todas las otras colecciones de sitios y aplicaciones que se ejecutan en él. Sin embargo, mediante el uso de soluciones en espacio aislado, puede implementar sus soluciones en una subárea de la granja, una colección de sitios específica. Para proporcionar protección adicional, el ensamblado de la solución no se carga en el método main [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] proceso (*w3wp.exe*). En su lugar, se carga en un proceso independiente (*SPUCWorkerProcess.exe*). Este proceso se supervisa e implementa cuotas y limitación para proteger la granja de servidores de soluciones en espacio aislado que realizan actividades perjudiciales, como la ejecución de bucles de pequeñas dimensiones que consumen ciclos de CPU.  
  
## <a name="site-collection-solution-gallery"></a>Galería de soluciones de colección de sitios
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 incluye una característica que se conoce como la "Galería de soluciones de sitio colección". Puede acceder a esta función desde la página de Administración Central de SharePoint 2010 o abriendo el **acciones del sitio** menú, elija **configuración del sitio**y, a continuación, elija el **soluciones** vincular en **galerías** en el sitio de SharePoint. Galerías de soluciones son repositorios de soluciones que permiten a los administradores de colección de sitio administrar las soluciones de sus colecciones de sitios.  
  
 La Galería de soluciones es una biblioteca de documentos almacenada en la raíz Web del sitio de SharePoint. La Galería de soluciones reemplaza las plantillas de sitio y admite paquetes de solución. Cuando un paquete de solución de SharePoint (*.wsp*) se carga el archivo, se procesa como una solución en espacio aislado.  
  
## <a name="sandboxed-solution-limitations"></a>Limitaciones de la solución en espacio aislado
 Cuando se implementa una solución en espacio aislado, se limita para ayudar a reducir las vulnerabilidades de seguridad que tenga la matriz de funcionalidad de SharePoint a su disposición. Algunas de estas limitaciones incluyen lo siguiente:  
  
- Soluciones en espacio aislado tienen un subconjunto restringido de elementos de la solución a su disposición. Plantillas de proyecto de SharePoint potencialmente vulnerables, como las definiciones de sitio y los flujos de trabajo, no están disponibles.  
  
- SharePoint ejecuta el código de la solución en espacio aislado en un proceso (*SPUCWorkerProcess.exe*) independiente de los principales [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] grupo de aplicaciones (*w3wp.exe*) proceso.  
  
- Carpetas asignadas no se puede agregar al proyecto.  
  
- Los tipos en el [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ensamblado Microsoft.Office.Server no puede utilizarse en soluciones en espacio aislado. Además, solo se escribe en el [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ensamblado Microsoft.SharePoint puede utilizarse en soluciones en espacio aislado.  
  
  Es importante tener en cuenta que si se especifica una solución de SharePoint como una solución en espacio aislado no tiene ningún efecto en el servidor de SharePoint; solo determina cómo se implementa el proyecto de SharePoint a SharePoint desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y qué ensamblados enlaza a. No afecta el generado *.wsp* archivo y el *.wsp* archivo no tiene datos que está directamente relación con la *solución en espacio aislado* propiedad.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Capacidades y elementos de soluciones en espacio aislado
 Soluciones en espacio aislado admiten las capacidades y los elementos siguientes:  
  
- Campos y tipos de contenido  
  
- Acciones personalizadas  
  
- Flujos de trabajo declarativos  
  
- Receptores de eventos  
  
- Llamadas de función  
  
- Definiciones de lista  
  
- Instancias de lista  
  
- Módulo/archivos  
  
- Navegación  
  
- *Onet.Xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Soporte técnico para todos los elementos Web que se derivan de `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Elementos Web  
  
- Elementos de la característica WebTemplate (en lugar de *Webtemp.xml*)  
  
- Elementos Web visuales  
  
  Soluciones en espacio aislado no admiten las capacidades y los elementos siguientes:  
  
- Páginas de aplicación  
  
- Grupo de acciones personalizadas  
  
- Características del ámbito de granja de servidores  
  
- `HideCustomAction` (elemento)  
  
- Características del ámbito de la aplicación Web  
  
- Flujos de trabajo con código  
  
## <a name="see-also"></a>Vea también
 [Diferencias entre el espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
