---
title: Obtener datos para un nodo integrado de SharePoint en Explorador de servidores
titleSuffix: ''
description: Obtener datos para el componente de SharePoint subyacente de un nodo de SharePoint integrado en la ventana de Explorador de servidores de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c58de345400c7b724a755839cb8baa1afc3cfce2
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217195"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Cómo: obtener datos para un nodo integrado de SharePoint en Explorador de servidores
  Para cada nodo integrado de SharePoint en **Explorador de servidores**, puede obtener datos del componente de SharePoint subyacente que el nodo representa. Para obtener más información, vea [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo obtener los datos de la lista de SharePoint subyacente que un nodo de lista representa en **Explorador de servidores**. De forma predeterminada, los nodos de lista tienen una vista en el elemento de menú contextual **del explorador** en el que puede hacer clic para abrir las listas en un explorador Web. En este ejemplo se amplían los nodos de lista agregando una vista en el elemento de menú contextual de **Visual Studio** que abre las listas directamente en Visual Studio. El código tiene acceso a los datos de la lista del nodo para obtener la dirección URL de la lista que se va a abrir en Visual Studio.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet10":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet10":::

 En este ejemplo se usa el servicio de proyecto de SharePoint para obtener el <xref:EnvDTE.DTE> objeto que se usa para abrir listas en Visual Studio. Para obtener más información sobre el servicio de proyecto de SharePoint, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Para obtener más información acerca de las tareas básicas para crear una extensión para un nodo de SharePoint, consulte [Cómo: extender un nodo de SharePoint en explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión de **Explorador de servidores** , cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Cómo: extender un nodo de SharePoint en Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
