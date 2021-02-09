---
title: Asociar datos personalizados con las extensiones de herramientas de SharePoint | Microsoft Docs
description: Asociar datos personalizados con las extensiones de herramientas de SharePoint. Vea una lista de objetos que pueden contener datos personalizados. Agregar y recuperar datos personalizados.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1b4722f04ae46f85d7cc70dadf6127330e8f6616
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851725"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Asociar datos personalizados con las extensiones de herramientas de SharePoint
  Puede agregar datos personalizados a ciertos objetos en las extensiones de herramientas de SharePoint. Esto resulta útil cuando se tienen datos en una parte de la extensión a la que se desea obtener acceso más adelante desde otro código de la extensión. En lugar de implementar una manera personalizada de almacenar y obtener acceso a los datos, puede asociar los datos a un objeto en la extensión y, a continuación, recuperar los datos del mismo objeto más adelante.

 Agregar datos personalizados a objetos también es útil si desea conservar los datos relevantes para un elemento específico en Visual Studio. Las extensiones de herramientas de SharePoint se cargan una sola vez en Visual Studio, por lo que es posible que la extensión funcione con varios elementos diferentes (como proyectos, elementos de proyecto o nodos **Explorador de servidores** ) en cualquier momento. Si tiene datos personalizados que solo son relevantes para un elemento específico, puede Agregar los datos al objeto que representa ese elemento.

 Cuando se agregan datos personalizados a objetos en las extensiones de herramientas de SharePoint, los datos no se conservan. Los datos solo están disponibles durante el tiempo de vida del objeto. Una vez que la recolección de elementos no utilizados reclama el objeto, se pierden los datos.

 En las extensiones del sistema de proyectos de SharePoint, también puede guardar los datos de cadena que se conservan después de descargar una extensión. Para obtener más información, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Objetos que pueden contener datos personalizados
 Puede agregar datos personalizados a cualquier objeto del modelo de objetos de herramientas de SharePoint que implementa la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaz. Esta interfaz define solo una propiedad, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> , que es una colección de objetos de datos personalizados. Los siguientes tipos implementan <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Agregar y recuperar datos personalizados
 Para agregar datos personalizados a un objeto en una extensión de herramientas de SharePoint, obtenga la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del objeto al que desea agregar los datos y, a continuación, use el <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> método para agregar los datos al objeto.

 Para recuperar datos personalizados de un objeto en una extensión de herramientas de SharePoint, obtenga la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del objeto y, a continuación, use uno de los métodos siguientes:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Este método devuelve **true** si el objeto de datos existe o **false** si no existe. Puede utilizar este método para recuperar instancias de tipos de valor o tipos de referencia.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Este método devuelve el objeto de datos si se cierra, o **null** si no existe. Solo puede utilizar este método para recuperar instancias de tipos de referencia.

  En el siguiente ejemplo de código se determina si un determinado objeto de datos ya está asociado a un elemento de proyecto. Si el objeto de datos aún no está asociado al elemento de proyecto, el código agrega el objeto a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del elemento de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Vea también
- [Conceptos y características de programación para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
