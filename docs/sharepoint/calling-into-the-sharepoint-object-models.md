---
title: Llamar a los modelos de objetos de SharePoint | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3795b7c920415ee733e08132234de381cf610aba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="calling-into-the-sharepoint-object-models"></a>Llamar a los modelos de objetos de SharePoint
  Al crear extensiones para las herramientas de SharePoint en Visual Studio, es posible que deba llamar APIs SharePoint para realizar ciertas tareas. Por ejemplo, si crea un paso de implementación personalizado para proyectos de SharePoint, es posible que deba llamar SharePoint APIs para llevar a cabo algunas de las tareas para implementar soluciones.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes que puede usar en las extensiones de herramientas de SharePoint: un modelo de objetos de servidor y un modelo de objetos de cliente. Cada modelo de objetos tiene ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint.  
  
 Para obtener información general de los modelos de objetos de SharePoint, vea [información general de la programación de modelo de herramientas de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>Con el modelo de objetos de cliente en proyectos de extensión  
 Al desarrollar una extensión para las herramientas de SharePoint, puede utilizar el modelo de objetos de cliente en el proyecto como cualquier otro conjunto de API administradas. Puede agregar referencias a ensamblados en el modelo de objetos de cliente a su proyecto, y se pueden llamar a las API en el modelo de objetos de cliente directamente desde el código.  
  
 Sin embargo, el modelo de objetos de cliente tiene dos desventajas en el contexto de las extensiones de herramientas de SharePoint:  
  
-   El modelo de objetos de cliente proporciona solo un subconjunto del modelo de objetos de servidor. Si tiene que usar la funcionalidad de SharePoint que no se expone en el modelo de objetos de cliente, debe usar el modelo de objetos de servidor.  
  
-   Aunque con el modelo de objetos de cliente en las extensiones de herramientas de SharePoint funcionará en la mayoría de los casos, podría encontrar algunos escenarios donde las llamadas al modelo de objetos de cliente no funcionan según lo previsto. El modelo de objetos de cliente está diseñado para usarse en aplicaciones cliente para llamar a los sitios de SharePoint en un servidor remoto o una granja de servidores. Las herramientas de SharePoint en Visual Studio solo funcionan con una instalación de SharePoint local en el equipo de desarrollo. Por lo tanto, cuando se utiliza el modelo de objetos de cliente en una extensión de herramientas de SharePoint, llama a un sitio de SharePoint en el equipo local, que no es cómo el modelo de objetos de cliente se diseñó para usarse.  
  
 Para ver un tutorial que muestra cómo utilizar el modelo de objetos de cliente en una extensión de las herramientas de SharePoint en Visual Studio, vea [Tutorial: realizar llamadas en el modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>Con el modelo de objeto de servidor en proyectos de extensión  
 El modelo de objetos de servidor es un supraconjunto del modelo de objetos de cliente. Cuando se utiliza el modelo de objetos de servidor, puede usar todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponen mediante programación.  
  
 Las extensiones de herramientas de SharePoint pueden usar las API en el modelo de objetos de servidor, pero no pueden llamar a las API directamente. El modelo de objetos de servidor puede llamar solo desde un proceso de 64 bits que tiene como destino .NET Framework 3.5. Sin embargo, las extensiones de herramientas de SharePoint requieren la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y se ejecutan en el proceso de Visual Studio de 32 bits. Esto impide que las extensiones de herramientas de SharePoint que hacen referencia directamente a los ensamblados en el modelo de objetos de servidor de SharePoint.  
  
 Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear una personalizada *comando de SharePoint* para llamar a la API. Defina el comando de SharePoint en un ensamblado secundario que puede llamar directamente al modelo de objetos de servidor. En el proyecto de extensión, llame a los comandos de SharePoint indirectamente mediante el método ExecuteCommand de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obtener más información sobre cómo crear y usar los comandos de SharePoint, vea [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) y [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Para obtener información sobre cómo implementar comandos de SharePoint, vea [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Para ver tutoriales que muestran cómo crear y utilizar los comandos de SharePoint, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) y [Tutorial: Extender el Explorador de servidores para mostrar Web Elementos](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>Comprender cómo los comandos de SharePoint se ejecutan  
 Los ensamblados que definen los comandos de SharePoint se cargan en un proceso de host de 64 bits denominado vssphost4.exe. Después de llamar a un comando de SharePoint en una extensión de herramientas de SharePoint, se ejecuta el comando vssphost4.exe en lugar del proceso de Visual Studio de 32 bits (devenv.exe). Puede controlar algunos aspectos de cómo se ejecutan los comandos de SharePoint estableciendo valores en el registro. Para obtener más información, consulte [extensiones de depuración para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  