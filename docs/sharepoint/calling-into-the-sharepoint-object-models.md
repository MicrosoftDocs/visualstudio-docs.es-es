---
title: Llamar a los modelos de objetos de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62988408"
---
# <a name="call-into-the-sharepoint-object-models"></a>Llamar a los modelos de objetos de SharePoint
  Al crear extensiones para las herramientas de SharePoint en Visual Studio, es posible que tenga que llamar a las API de SharePoint para realizar determinadas tareas. Por ejemplo, si crea un paso de implementación personalizado para proyectos de SharePoint, es posible que tenga que llamar a las API de SharePoint para realizar algunas de las tareas de implementación de soluciones.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes que puede usar en las extensiones de herramientas de SharePoint: un modelo de objetos de servidor y un modelo de objetos de cliente. Cada modelo de objetos tiene ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint.

 Para obtener información general sobre los modelos de objetos de SharePoint, vea [información general del modelo de programación de las extensiones de herramientas de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Usar el modelo de objetos de cliente en los proyectos de extensión
 Al desarrollar una extensión para las herramientas de SharePoint, puede usar el modelo de objetos de cliente en el proyecto como cualquier otro conjunto de API administradas. Puede Agregar referencias a los ensamblados del modelo de objetos de cliente al proyecto, y puede llamar a las API del modelo de objetos de cliente directamente desde el código.

 Sin embargo, el modelo de objetos de cliente tiene dos inconvenientes en el contexto de las extensiones de herramientas de SharePoint:

- El modelo de objetos de cliente proporciona solo un subconjunto del modelo de objetos de servidor. Si tiene que utilizar la funcionalidad de SharePoint que no se expone en el modelo de objetos de cliente, debe utilizar el modelo de objetos de servidor.

- Aunque el uso del modelo de objetos de cliente en las extensiones de herramientas de SharePoint debería funcionar en la mayoría de los casos, podría encontrar algunos escenarios en los que las llamadas al modelo de objetos de cliente no funcionan según lo esperado. El modelo de objetos de cliente está diseñado para usarse en las aplicaciones cliente para llamar a sitios de SharePoint en un servidor o granja de servidores remotos. Las herramientas de SharePoint en Visual Studio solo funcionan con una instalación de SharePoint local en el equipo de desarrollo. Por lo tanto, cuando se usa el modelo de objetos de cliente en una extensión de herramientas de SharePoint, se llama a un sitio de SharePoint en el equipo local, que no es la forma en que se diseñó el modelo de objetos de cliente.

  Para ver un tutorial que muestra cómo usar el modelo de objetos de cliente en una extensión de las herramientas de SharePoint en Visual Studio, vea [Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Usar el modelo de objetos de servidor en proyectos de extensión
 El modelo de objetos de servidor es un supraconjunto del modelo de objetos de cliente. Al utilizar el modelo de objetos de servidor, puede usar todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponer mediante programación.

 Las extensiones de herramientas de SharePoint pueden usar las API en el modelo de objetos de servidor, pero no pueden llamar directamente a las API. Solo se puede llamar al modelo de objetos de servidor desde un proceso de 64 bits que tenga como destino el .NET Framework 3,5. Sin embargo, las extensiones de herramientas de SharePoint requieren [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y se ejecutan en el proceso de Visual Studio de 32 bits. Esto evita que las extensiones de herramientas de SharePoint hagan referencia directamente a los ensamblados del modelo de objetos de servidor de SharePoint.

 Si desea usar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API. El comando de SharePoint se define en un ensamblado secundario que puede llamar directamente al modelo de objetos de servidor. En el proyecto de extensión, se llama al comando de SharePoint indirectamente mediante el método ExecuteCommand de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.

 Para obtener más información sobre la creación y el uso de comandos de SharePoint, vea [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) y [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Para obtener información sobre cómo implementar comandos de SharePoint, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Para ver tutoriales que muestran cómo crear y usar comandos de SharePoint, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) y [tutorial: extender explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Comprender cómo se ejecutan los comandos de SharePoint
 Los ensamblados que definen los comandos de SharePoint se cargan en un proceso de host de 64 bits denominado *vssphost4.exe*. Después de llamar a un comando de SharePoint en una extensión de herramientas de SharePoint, el comando se ejecuta en *vssphost4.exe* en lugar del proceso de Visual Studio de 32 bits (*devenv.exe*). Puede controlar algunos aspectos de cómo se ejecutan los comandos de SharePoint estableciendo valores en el registro. Para obtener más información, vea [depurar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Información general sobre el modelo de programación de extensiones de herramientas de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
