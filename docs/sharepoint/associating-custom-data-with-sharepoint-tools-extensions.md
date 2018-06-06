---
title: Asociar datos personalizados con SharePoint de extensiones de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 051285d1a2b3fc1c32a813fbfd8aa778befa0545
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764880"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Asociar datos personalizados con extensiones de herramientas de SharePoint
  Puede agregar datos personalizados a ciertos objetos en las extensiones de herramientas de SharePoint. Esto es útil si tiene datos en una parte de la extensión que desea tener acceso a más adelante desde otro código en la extensión. En lugar de implementar una manera personalizada para almacenar y tener acceso a datos, puede asociar los datos a un objeto en la extensión y, a continuación, recuperar los datos del mismo objeto más adelante.  
  
 Agregar datos personalizados a objetos también es útil cuando desea conservar los datos que es relevantes para un elemento específico en Visual Studio. Las extensiones de herramientas de SharePoint se cargan una sola vez en Visual Studio, por lo que la extensión podría funcionar con varios elementos diferentes (como proyectos, elementos, proyecto o **Explorador de servidores** nodos) en cualquier momento. Si tiene datos personalizados que solo es pertinentes para un elemento específico, puede agregar los datos para el objeto que representa ese elemento.  
  
 Al agregar datos personalizados a los objetos en las extensiones de herramientas de SharePoint, los datos no se conservan. Los datos están disponibles únicamente durante el tiempo de vida del objeto. Después de que el objeto sea reclamado por la recolección de elementos, se pierden los datos.  
  
 En extensiones del sistema del proyecto de SharePoint, también puede guardar los datos de cadena que se conserva después de descargar una extensión. Para obtener más información, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objetos que pueden contener datos personalizados
 Puede agregar datos personalizados a cualquier objeto en el modelo de objetos de herramientas de SharePoint que implementa el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaz. Esta interfaz define sólo una propiedad, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, que es una colección de objetos de datos personalizados. Implementan los siguientes tipos <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Agregar y recuperar datos personalizados
 Para agregar datos personalizados a un objeto en una extensión de herramientas de SharePoint, obtenga la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del objeto que desea agregar los datos y, a continuación, usar el <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> método para agregar los datos al objeto.  
  
 Para recuperar datos personalizados de un objeto en una extensión de herramientas de SharePoint, obtenga la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del objeto y, a continuación, use uno de los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Este método devuelve **true** si existe el objeto de datos, o **false** si no existe. Puede usar este método para recuperar instancias de tipos de valor o tipos de referencia.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Este método devuelve los datos de objeto si este se cierra, o **null** si no existe. Puede usar este método para recuperar instancias de tipos de referencia.  
  
 En el ejemplo de código siguiente se determina si un determinado objeto de datos ya está asociado a un elemento de proyecto. Si el objeto de datos ya no está asociado con el elemento de proyecto, el código agrega el objeto a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del elemento de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Vea también
 [Programar conceptos y características para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Cómo: Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 