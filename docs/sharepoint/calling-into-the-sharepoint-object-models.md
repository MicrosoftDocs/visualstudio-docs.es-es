---
title: Llamar a los modelos de objetos de SharePoint | Microsoft Docs
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
ms.openlocfilehash: 3afb988b226ccf62fae92ab02d8380d20b19605b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853439"
---
# <a name="call-into-the-sharepoint-object-models"></a>Llamar a los modelos de objetos de SharePoint
  Al crear extensiones para las herramientas de SharePoint en Visual Studio, es posible que deba llamar a SharePoint APIs para llevar a cabo ciertas tareas. Por ejemplo, si crea un paso de implementación personalizado para proyectos de SharePoint, tendrá que llamar a SharePoint APIs para llevar a cabo algunas de las tareas para implementar soluciones.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes que puede usar en las extensiones de herramientas de SharePoint: un modelo de objetos de servidor y un modelo de objetos de cliente. Cada modelo de objetos tiene ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint.  
  
 Para obtener información general de los modelos de objetos de SharePoint, vea [información general del modelo de programación de SharePoint de extensiones](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>Usar el modelo de objetos de cliente en proyectos de extensión
 Al desarrollar una extensión para las herramientas de SharePoint, puede usar el modelo de objetos de cliente en el proyecto como cualquier otro conjunto de API administradas. Puede agregar referencias a ensamblados en el modelo de objetos de cliente a su proyecto y se pueden llamar a las API en el modelo de objetos de cliente directamente desde el código.  
  
 Sin embargo, el modelo de objetos de cliente tiene dos inconvenientes en el contexto de las extensiones de herramientas de SharePoint:  
  
- El modelo de objetos de cliente proporciona solo un subconjunto del modelo de objetos de servidor. Si tiene que usar la funcionalidad de SharePoint que no se expone en el modelo de objetos de cliente, a continuación, debe usar el modelo de objetos de servidor.  
  
- Aunque con el modelo de objeto de cliente en extensiones de herramientas de SharePoint debe funcionar en la mayoría de los casos, pueden producirse algunos escenarios donde las llamadas al modelo de objetos de cliente no funcionan según lo previsto. El modelo de objetos de cliente está diseñado para usarse en aplicaciones cliente para llamar a los sitios de SharePoint en un servidor remoto o una granja de servidores. Las herramientas de SharePoint en Visual Studio solo funcionan con una instalación de SharePoint local en el equipo de desarrollo. Por lo tanto, cuando se utiliza el modelo de objetos de cliente en una extensión de herramientas de SharePoint, llama a un sitio de SharePoint en el equipo local, que no es cómo el modelo de objetos de cliente se diseñó para usarse.  
  
  Para ver un tutorial que muestra cómo utilizar el modelo de objetos de cliente en una extensión de las herramientas de SharePoint en Visual Studio, consulte [Tutorial: llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>Usar el modelo de objetos de servidor en proyectos de extensión
 El modelo de objetos de servidor es un superconjunto del modelo de objetos de cliente. Cuando se usa el modelo de objetos de servidor, puede usar todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponer mediante programación.  

 Las extensiones de herramientas de SharePoint pueden usar las API en el modelo de objetos de servidor, pero no pueden llamar a las API directamente. El modelo de objetos de servidor se puede llamar solo desde un proceso de 64 bits que tenga como destino .NET Framework 3.5. Sin embargo, las extensiones de herramientas de SharePoint requieren la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y se ejecutan en el proceso de Visual Studio de 32 bits. Esto evita que las extensiones de herramientas de SharePoint que hacen referencia directamente a los ensamblados en el modelo de objetos de servidor de SharePoint.  
  
 Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear una personalizada *comando de SharePoint* para llamar a la API. Definir el comando de SharePoint en un ensamblado secundario que puede llamar directamente al modelo de objetos de servidor. En el proyecto de extensión, llame al comando de SharePoint indirectamente mediante el método ExecuteCommand un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obtener más información sobre cómo crear y usar los comandos de SharePoint, vea [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) y [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Para obtener información sobre cómo implementar comandos de SharePoint, vea [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Para ver tutoriales que muestran cómo crear y usar los comandos de SharePoint, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) y [Tutorial: Extender el Explorador de servidores para mostrar elementos web ](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Comprender cómo se ejecutan los comandos de SharePoint
 Los ensamblados que definen los comandos de SharePoint se cargan en un proceso de host de 64 bits denominado *vssphost4.exe*. Después de llamar a un comando de SharePoint en una extensión de herramientas de SharePoint, se ejecuta el comando por *vssphost4.exe* en lugar del proceso de Visual Studio de 32 bits (*devenv.exe*). Puede controlar algunos aspectos de cómo se ejecutan los comandos de SharePoint mediante el establecimiento de valores en el registro. Para obtener más información, consulte [depurar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Información general del modelo de programación de SharePoint de extensiones](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
