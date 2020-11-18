---
title: Referencia de API (extensibilidad de herramientas de SharePoint) | Microsoft Docs
description: Revise la documentación de referencia de la API para ampliar las herramientas de SharePoint en Visual Studio. Vea una lista de espacios de nombres relacionados, como Microsoft. VisualStudio. SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4599a2c305558f2ef551d19abac210bdf05269f3
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850395"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Referencia de API (extensibilidad de herramientas de SharePoint)
  Esta sección contiene la documentación de referencia de la API para extender las herramientas de SharePoint en Visual Studio.

## <a name="in-this-section"></a>En esta sección
 <xref:Microsoft.VisualStudio.SharePoint>

 Contiene los tipos que se usan para extender el sistema de proyectos de SharePoint. Por ejemplo, puede extender elementos de proyecto y proyectos SharePoint integrados, o puede crear sus propios elementos de proyecto.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contiene tipos que se pueden usar para crear *comandos de SharePoint* personalizados. Un comando de SharePoint es un método que llama al modelo de objetos de servidor de SharePoint desde una extensión de herramientas de SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 Contiene tipos que se usan para extender el proceso de implementación de proyectos de SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 Contiene los tipos que se usan para extender los nodos de SharePoint en **Explorador de servidores** o para definir sus propios tipos de nodos.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 Contiene tipos que se pueden usar para obtener información sobre los nodos **Explorador de servidores** integrados que representan los componentes individuales en un sitio de SharePoint, como un nodo que representa una lista, un campo o un tipo de contenido.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 Contiene los tipos que se usan para tener acceso a la definición de una característica en un proyecto de SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 Contiene los tipos que se usan para tener acceso a la definición del paquete de un proyecto de SharePoint.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 Contiene los tipos que se usan para autenticar y comunicarse con las aplicaciones para SharePoint que se implementan en sitios de SharePoint remotos.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 Contiene los tipos que se usan para crear comandos remotos de SharePoint, utilizados con las aplicaciones para SharePoint que se implementan en sitios de SharePoint remotos.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 Contiene los tipos que Visual Studio usa como tareas de compilación para empaquetar y depurar proyectos de SharePoint, aplicaciones para Office y aplicaciones para SharePoint. Esta API es compatible con la infraestructura de Office y SharePoint y no está diseñada para usarse directamente desde el código.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 Contiene tipos que se usan para personalizar el comportamiento de validación de paquetes y características de un proyecto de SharePoint.

## <a name="see-also"></a>Consulte también
- [Referencia &#40;extensibilidad de herramientas de SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Extensión del sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
