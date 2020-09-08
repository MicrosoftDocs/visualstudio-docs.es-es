---
title: Extensión de las herramientas de SharePoint en Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016044"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Extensión de las herramientas de SharePoint en Visual Studio
  Las herramientas de SharePoint en Visual Studio cumplen los requisitos de muchos escenarios de desarrollo de aplicaciones. Pero es posible que descubra casos en los que no proporcionan las funciones que usted u otros desarrolladores necesitan. En estos casos, puede extender las herramientas de SharePoint para crear la funcionalidad que necesita.

## <a name="how-to-extend-the-sharepoint-tools"></a>Procedimiento para extender las herramientas de SharePoint
 Puede extender el sistema de proyectos de SharePoint y el nodo **Conexiones de SharePoint** en la ventana **Explorador de servidores**.

### <a name="extend-the-sharepoint-project-system"></a>Extensión del sistema de proyectos de SharePoint
 Visual Studio incluye un conjunto de plantillas de proyecto y de elemento que puede usar para crear soluciones de SharePoint. Por ejemplo, hay plantillas para receptores de eventos, definiciones de lista, flujos de trabajo y elementos web. Pero también puede definir tipos de elementos de proyecto de SharePoint propios para crear componentes de SharePoint como campos o acciones personalizadas. También puede crear extensiones para los tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio y crear extensiones para los proyectos de SharePoint.

 Para obtener más información, vea [Extensión del sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Extensión del nodo Conexiones de SharePoint en el Explorador de servidores
 En Visual Studio, puede usar el nodo **Conexiones de SharePoint** de la ventana **Explorador de servidores** para ver muchos de los componentes de uno o varios sitios locales de SharePoint en una vista de árbol jerárquica. También puede extender el nodo **Conexiones de SharePoint** de estas formas:

- Mediante la adición de reglas propias. Esto resulta útil si quiere mostrar componentes de sitios de SharePoint que no se muestran de forma predeterminada.

- Mediante la extensión de nodos existentes. Por ejemplo, puede agregar un nuevo nodo secundario a un nodo existente, o bien agregar un elemento de menú contextual a un nodo y realizar tareas cuando un desarrollador haga clic en el elemento de menú.

  Para obtener más información, vea [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Requisitos del equipo de desarrollo
 Para crear extensiones para las herramientas de SharePoint, el equipo de desarrollo debe cumplir los mismos requisitos que para crear soluciones de SharePoint en Visual Studio.

 También se recomienda instalar el [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. El SDK incluye plantillas y herramientas de proyecto que puede usar para extender Visual Studio. En concreto, el SDK incluye una plantilla de proyecto que puede usar para crear con facilidad un paquete de extensión de Visual Studio (VSIX). Los paquetes VSIX son la manera preferida de implementar extensiones de Visual Studio en Visual Studio. Todas las extensiones de herramientas de SharePoint se deben implementar mediante paquetes VSIX. En todos los tutoriales de esta documentación se supone que tiene instalado el [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].

 Para instalar el SDK de Visual Studio, vea [Instalación del SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Para obtener más información sobre las extensiones de Visual Studio, vea [Comienzo del desarrollo de extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Consulte también

- [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Extensión del sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Conceptos y características de programación para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referencia &#40;Extensibilidad de Herramientas de SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Depuración de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)