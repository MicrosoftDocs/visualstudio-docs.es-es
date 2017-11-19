---
title: Extender las herramientas de SharePoint en Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b78f90df8b6e46774310bd4a8cf218fbcbc7a18b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Extender la Herramientas de SharePoint en Visual Studio
  Las herramientas de SharePoint en Visual Studio cumplen los requisitos de muchos escenarios de desarrollo de aplicaciones. No obstante, podría detectar casos donde no proporcionan una funcionalidad que requieran o el de otros desarrolladores. En estos casos, puede extender las herramientas de SharePoint para crear la funcionalidad que necesita.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Cómo extender las herramientas de SharePoint  
 Puede extender el sistema de proyectos de SharePoint y el **las conexiones de SharePoint** nodo en el **Explorador de servidores** ventana.  
  
### <a name="extending-the-sharepoint-project-system"></a>Extender el sistema de proyectos de SharePoint  
 Visual Studio incluye un conjunto de plantillas de proyecto y plantillas de elementos que puede usar para crear soluciones de SharePoint. Por ejemplo, hay plantillas para los receptores de eventos, las definiciones de lista, flujos de trabajo y elementos Web. Sin embargo, también puede definir sus propios tipos de elementos de proyecto de SharePoint para crear componentes de SharePoint, como campos o acciones personalizadas. También puede crear extensiones para tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio y puede crear extensiones para los proyectos de SharePoint.  
  
 Para obtener más información, consulte [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Extender el nodo Conexiones de SharePoint en el Explorador de servidores  
 En Visual Studio, puede usar el **las conexiones de SharePoint** nodo en el**Explorador de servidores** ventana para ver muchos de los componentes de uno o más sitios de SharePoint locales en una vista de árbol jerárquico. También puede ampliar el **las conexiones de SharePoint** nodo de las maneras siguientes:  
  
-   Al agregar sus propios nodos. Esto es útil si desea mostrar los componentes de sitios de SharePoint que no se muestran de forma predeterminada.  
  
-   Mediante la extensión de los nodos existentes. Por ejemplo, puede agregar un nuevo nodo secundario a un nodo existente, o puede agregar un elemento de menú contextual a un nodo y realizar tareas cuando un desarrollador hace clic en el elemento de menú.  
  
 Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Requisitos del equipo de desarrollo  
 Para crear extensiones para las herramientas de SharePoint, el equipo de desarrollo debe cumplir los mismos requisitos para crear soluciones de SharePoint en Visual Studio. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 También se recomienda que instale el [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. El SDK incluye plantillas de proyecto y herramientas que puede usar para ampliar Visual Studio. En concreto, el SDK incluye una plantilla de proyecto que puede usar para crear fácilmente un paquete de extensión de Visual Studio (VSIX). Los paquetes VSIX son el modo preferido para implementar extensiones de Visual Studio en Visual Studio. Todas las extensiones de herramientas de SharePoint deben implementarse mediante paquetes VSIX. Todos los tutoriales de esta documentación se suponen que tiene el [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] instalado.  
  
 Para instalar el SDK de Visual Studio, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Para obtener más información acerca de las extensiones de Visual Studio, vea [comenzar a desarrollar extensiones de Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el modelo de programación de SharePoint de extensiones de herramientas](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programar conceptos y características para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Referencia del sistema &#40; Extensibilidad de herramientas de SharePoint &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Depurar las extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  