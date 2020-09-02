---
title: Referencia de API (extensibilidad de herramientas de SharePoint) | Microsoft Docs
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
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62987981"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>Referencia de API (extensibilidad de herramientas de SharePoint)
  Esta sección contiene la documentación de referencia de la API para extender las herramientas de SharePoint en Visual Studio.

## <a name="in-this-section"></a>En esta sección
 <xref:Microsoft.VisualStudio.SharePoint>

 Contiene los tipos que se usan para extender el sistema de proyectos de SharePoint. Por ejemplo, puede extender elementos de proyecto y proyectos SharePoint integrados, o puede crear sus propios elementos de proyecto.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 Contiene tipos que se pueden usar para crear *comandos de SharePoint*personalizados. Un comando de SharePoint es un método que llama al modelo de objetos de servidor de SharePoint desde una extensión de herramientas de SharePoint.

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
- [Información general sobre el modelo de programación de extensiones de herramientas de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Extender el nodo conexiones de SharePoint en Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
