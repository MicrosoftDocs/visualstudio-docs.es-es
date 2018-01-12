---
title: "Cómo: obtener datos para un nodo integrado de SharePoint en el Explorador de servidores | Documentos de Microsoft"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cf70fe2e24f88ba64ab648d18d93907de0ddbfaf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Cómo: Obtener datos para un nodo integrado de SharePoint en el Explorador de servidores
  Para cada nodo integrado de SharePoint en **Explorador de servidores**, puede obtener datos para el componente de SharePoint subyacente que representa el nodo. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo obtener datos de la lista de SharePoint subyacente que representa un nodo de lista de **Explorador de servidores**. De forma predeterminada, los nodos de lista tienen una **ver en el explorador** elemento del menú contextual que puede hacer clic para abrir las listas en un explorador Web. En este ejemplo extiende los nodos de la lista mediante la adición de un **vista en Visual Studio** elemento del menú contextual que se abre las listas directamente en Visual Studio. El código tiene acceso a los datos de lista para el nodo que se va a obtener la dirección URL de la lista para abrir en Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 Este ejemplo utiliza el servicio de proyecto de SharePoint para obtener el <xref:EnvDTE.DTE> enumera el objeto que se usa para abrir en Visual Studio. Para obtener más información sobre el servicio de proyecto de SharePoint, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Para obtener más información acerca de las tareas básicas para crear una extensión para un nodo de SharePoint, vea [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la **Explorador de servidores** extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  