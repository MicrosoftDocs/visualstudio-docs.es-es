---
title: Extender las herramientas de SharePoint en Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016044"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Extender las herramientas de SharePoint en Visual Studio
  Las herramientas de SharePoint en Visual Studio cumplen los requisitos de muchos escenarios de desarrollo de aplicaciones. Sin embargo, es posible que descubra los casos en los que no proporcionan funciones que usted u otros desarrolladores necesiten. En estos casos, puede extender las herramientas de SharePoint para crear la funcionalidad que necesita.

## <a name="how-to-extend-the-sharepoint-tools"></a>Cómo extender las herramientas de SharePoint
 Puede extender el sistema de proyectos de SharePoint y el nodo **conexiones de SharePoint** en la ventana **Explorador de servidores** .

### <a name="extend-the-sharepoint-project-system"></a>Extender el sistema de proyectos de SharePoint
 Visual Studio incluye un conjunto de plantillas de proyecto y plantillas de elementos que puede usar para crear soluciones de SharePoint. Por ejemplo, hay plantillas para receptores de eventos, definiciones de lista, flujos de trabajo y elementos web. Sin embargo, también puede definir sus propios tipos de elementos de proyecto de SharePoint para crear componentes de SharePoint como campos o acciones personalizadas. También puede crear extensiones para los tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio y puede crear extensiones para los proyectos de SharePoint.

 Para obtener más información, vea [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Extender el nodo conexiones de SharePoint en Explorador de servidores
 En Visual Studio, puede usar el nodo **conexiones de SharePoint** de la ventana de **Explorador de servidores** para ver muchos de los componentes de uno o varios sitios de SharePoint locales en una vista de árbol jerárquica. También puede extender el nodo **conexiones de SharePoint** de las siguientes maneras:

- Agregando sus propios nodos. Esto resulta útil si desea mostrar los componentes de los sitios de SharePoint que no se muestran de forma predeterminada.

- Mediante la extensión de los nodos existentes. Por ejemplo, puede Agregar un nuevo nodo secundario a un nodo existente, o puede Agregar un elemento de menú contextual a un nodo y realizar tareas cuando un desarrollador hace clic en el elemento de menú.

  Para obtener más información, vea [extender el nodo conexiones de SharePoint en explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Requisitos del equipo de desarrollo
 Para crear extensiones para las herramientas de SharePoint, el equipo de desarrollo debe cumplir los mismos requisitos para crear soluciones de SharePoint en Visual Studio.

 También se recomienda instalar el [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . El SDK incluye plantillas y herramientas de proyecto que puede usar para extender Visual Studio. En concreto, el SDK incluye una plantilla de proyecto que puede usar para crear fácilmente un paquete de extensión de Visual Studio (VSIX). Los paquetes VSIX son la manera preferida de implementar extensiones de Visual Studio en Visual Studio. Todas las extensiones de herramientas de SharePoint deben implementarse mediante paquetes VSIX. En todos los tutoriales de esta documentación se supone que tiene [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] instalado.

 Para instalar el SDK de Visual Studio, consulte [instalación del SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Para obtener más información sobre las extensiones de Visual Studio, consulte [empezar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Consulte también

- [Información general sobre el modelo de programación de extensiones de herramientas de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Extender el nodo conexiones de SharePoint en Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Conceptos y características de programación para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referencia &#40;extensibilidad de herramientas de SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Depurar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)