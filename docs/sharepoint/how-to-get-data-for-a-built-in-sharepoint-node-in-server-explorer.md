---
title: Procedimiento Obtener datos para un nodo integrado de SharePoint en el Explorador de servidores | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef3377b7c90aac183c1fc624743ea2882685eb27
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870368"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procedimiento Obtener datos para un nodo integrado de SharePoint en el Explorador de servidores
  Para cada nodo integrado de SharePoint en **Explorador de servidores**, puede obtener datos para el componente de SharePoint subyacente que representa el nodo. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo obtener datos para la lista de SharePoint subyacente que representa un nodo de lista en **Explorador de servidores**. De forma predeterminada, los nodos de la lista tienen una **ver en el explorador** elemento de menú contextual que puede hacer clic para abrir las listas en un explorador Web. Este ejemplo amplía los nodos de la lista mediante la adición de un **vista en Visual Studio** elemento de menú contextual que se abre las listas directamente en Visual Studio. El código tiene acceso a los datos de lista para el nodo obtener la dirección URL de la lista para abrir en Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 En este ejemplo se usa el servicio de proyecto de SharePoint para obtener el <xref:EnvDTE.DTE> enumera el objeto que se usa para abrir en Visual Studio. Para obtener más información sobre el servicio de proyecto de SharePoint, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Para obtener más información acerca de las tareas básicas para crear una extensión para un nodo de SharePoint, vea [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compile-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar el **Explorador de servidores** extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
