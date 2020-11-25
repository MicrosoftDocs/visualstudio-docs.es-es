---
title: Consideraciones sobre las soluciones en espacio aislado | Microsoft Docs
description: Explore soluciones en espacio aislado, que son una característica de Microsoft SharePoint que permite a los usuarios de la colección de sitios cargar sus propias soluciones de código personalizado.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17b310a3f992f80b04ad14bb6e038e05b009a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970468"
---
# <a name="sandboxed-solution-considerations"></a>Consideraciones sobre las soluciones de espacio aislado
  Las *soluciones en espacio aislado* son una característica de Microsoft SharePoint 2010 que permite a los usuarios de la colección de sitios cargar sus propias soluciones de código personalizado. Una solución en espacio aislado común es que los usuarios carguen sus propios elementos web.

 Una aplicación de SharePoint en espacio aislado se ejecuta en un proceso seguro y supervisado que tiene acceso a una parte limitada de la granja de servidores Web. Microsoft SharePoint 2010 usa una combinación de características, galerías de soluciones, supervisión de soluciones y un marco de validación para habilitar soluciones en espacio aislado.

## <a name="specify-project-trust-level"></a>Especificar el nivel de confianza del proyecto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] admite soluciones en espacio aislado a través de una propiedad de proyecto booleana denominada *solución en espacio aislado*. Esta propiedad se puede establecer en cualquier momento del proyecto o se puede especificar al crear el proyecto en el **Asistente para la personalización de SharePoint**.

> [!NOTE]
> Cambiar la propiedad de la *solución en espacio aislado* de un proyecto después de crearla puede producir errores de validación.

 La solución se considera una solución de ámbito de granja si la propiedad *solución en espacio aislado* está establecida en **false** o elige la opción **implementar como solución de granja de servidores** . Sin embargo, la solución se trata de forma diferente a partir de una solución de granja si la propiedad *solución en espacio aislado* está establecida en **true** o elige la opción **implementar como solución en espacio aislado** del asistente.

## <a name="sharepoint-site-hierarchy"></a>Jerarquía de sitios de SharePoint
 Para comprender cómo funcionan las soluciones en espacio aislado, es útil saber que los sitios de SharePoint son jerárquicos en el ámbito. El elemento superior se conoce como la granja de servidores web y otros elementos están subordinados a él:

 Granja web

 Aplicación web A

 Colección de sitios a1

 Sitio A1A

 Aplicación web B

 Colección de sitios B1

 Sitio B1a

 Sitio B1b

 Colección de sitios B2

 Sitio B2A

 Como puede ver, las granjas de servidores Web pueden contener una o más aplicaciones Web, que a su vez pueden contener una o más colecciones de sitios, que pueden tener subsitios, etc. Los cambios realizados en una colección de sitios solo afectan a esa colección de sitios. Sin embargo, los cambios realizados en el nivel de granja de servidores web afectan a todas las colecciones de sitios de la granja.

 Windows SharePoint Services (WSS) 3,0 le permite implementar soluciones solo en el nivel de granja, pero [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] le permite realizar la implementación en el nivel de granja (solución de granja de servidores) o en el nivel de colección de sitios (solución en espacio aislado).

## <a name="why-sandboxed-solutions"></a>¿Por qué soluciones en espacio aislado?
 En WSS 3,0, las soluciones solo se pueden implementar en el nivel de granja. Esto significaba que podrían implementarse soluciones potencialmente dañinas o desestabilizadores que afectaran a toda la granja de servidores web y a todas las demás colecciones de sitios y aplicaciones que se ejecutan en él. Sin embargo, mediante el uso de soluciones en espacio aislado, puede implementar sus soluciones en una subárea de la granja, una colección de sitios específica. Para proporcionar protección adicional, el ensamblado de la solución no se carga en el [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] proceso principal (*w3wp.exe*). En su lugar, se carga en un proceso independiente (*SPUCWorkerProcess.exe*). Este proceso se supervisa e implementa cuotas y limitaciones para proteger la granja de soluciones en espacio aislado que realizan actividades dañinas, como la ejecución de bucles estrechos que consumen ciclos de CPU.

## <a name="site-collection-solution-gallery"></a>Galería de soluciones de colección de sitios
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 tiene una característica que se conoce como "Galería de soluciones de colección de sitios". Puede tener acceso a esta característica desde la página Administración central de SharePoint 2010 o abriendo el menú **acciones del sitio** , eligiendo **configuración del sitio** y, a continuación, eligiendo el vínculo **soluciones** en  **galerías** en el sitio de SharePoint. Las galerías de soluciones son repositorios de soluciones que permiten a los administradores de la colección de sitios administrar soluciones en sus colecciones de sitios.

 La galería de soluciones es una biblioteca de documentos almacenada en el Web raíz del sitio de SharePoint. La galería de soluciones reemplaza a las plantillas de sitio y admite paquetes de soluciones. Cuando se carga un archivo de paquete de solución de SharePoint (*. wsp*), se procesa como una solución en espacio aislado.

## <a name="sandboxed-solution-limitations"></a>Limitaciones de la solución en espacio aislado
 Cuando se implementa una solución en espacio aislado, la matriz de la funcionalidad de SharePoint disponible para ayudarle a reducir las vulnerabilidades de seguridad que pueda tener. Entre estas limitaciones se incluyen las siguientes:

- Las soluciones en espacio aislado tienen a su disposición un subconjunto restringido de elementos de solución que se pueden implementar. Las plantillas de proyecto de SharePoint potencialmente vulnerables, como las definiciones de sitio y los flujos de trabajo, no están disponibles.

- SharePoint ejecuta el código de la solución en espacio aislado en un proceso (*SPUCWorkerProcess.exe*) independiente del proceso principal del [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] grupo de aplicaciones (*w3wp.exe*).

- No se pueden agregar carpetas asignadas al proyecto.

- Los tipos del [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ensamblado Microsoft. Office. Server no se pueden usar en soluciones en espacio aislado. Además, solo los tipos del [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ensamblado Microsoft. SharePoint se pueden usar en soluciones en espacio aislado.

  Es importante tener en cuenta que la especificación de una solución de SharePoint como una solución en espacio aislado no tiene ningún efecto en el servidor de SharePoint; solo determina cómo se implementa el proyecto de SharePoint en SharePoint desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y a qué ensamblados se enlaza. No afecta al archivo *. wsp* generado y el archivo *. wsp* no tiene datos que se correlacionan directamente con la propiedad de la *solución en espacio aislado* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funcionalidades y elementos en soluciones en espacio aislado
 Las soluciones en espacio aislado admiten los siguientes elementos y capacidades:

- Tipos de contenido/campos

- Acciones personalizadas

- Flujos de trabajo declarativos

- Receptores de eventos

- Llamadas de características

- Enumerar definiciones

- Enumerar instancias

- Módulo/archivos

- Navegación

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Compatibilidad con todos los elementos web que derivan de `System.Web.UI.WebControls.WebParts.WebPart`

- elementos web

- Elementos de característica webtemplates (en lugar de *Webtemp.xml*)

- elementos web visual

  Las soluciones en espacio aislado no admiten las siguientes funcionalidades y elementos:

- Páginas de aplicación

- Grupo de acciones personalizadas

- Características de ámbito de granja

- Elemento `HideCustomAction`

- Características con ámbito de aplicación Web

- Flujos de trabajo con código

## <a name="see-also"></a>Vea también
- [Diferencias entre soluciones en espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
