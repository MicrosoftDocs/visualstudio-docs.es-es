---
title: Extender elementos de proyecto de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967401"
---
# <a name="extend-sharepoint-project-items"></a>Extender elementos de proyecto de SharePoint
  Cree una extensión de elemento de proyecto cuando desee agregar funcionalidad a un tipo de elemento de proyecto de SharePoint que ya está instalado en Visual Studio. Por ejemplo, puede crear una extensión para los elementos de proyecto de **definición de lista** o **receptor de eventos** integrados en Visual Studio, o puede crear una extensión para un tipo de elemento de proyecto personalizado. También puede crear una extensión para todos los tipos de elementos de proyecto de SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Tareas para extender elementos de proyecto de SharePoint
 Para extender un elemento de proyecto, cree un ensamblado de extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaz. Para obtener más información, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Al extender un elemento de proyecto, también puede Agregar la siguiente funcionalidad al elemento de proyecto:

- Agregue un elemento de menú contextual al elemento de proyecto. El elemento de menú aparece al abrir el menú contextual del elemento de proyecto en **Explorador de soluciones**. Para abrir el menú contextual, haga clic con el botón secundario en el elemento de proyecto o selecciónelo y, a continuación, elija las teclas **MAYÚS** + **F10** . Para obtener más información, vea [Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Agregue una propiedad personalizada al elemento de proyecto. La propiedad aparece en la ventana **propiedades** cuando se elige el elemento de proyecto en **Explorador de soluciones**. Para obtener más información, vea [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de elemento de proyecto, vea [Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Descripción de la relación entre las extensiones de elemento de proyecto y las instancias de elemento de proyecto
 Cuando se crea una extensión de elemento de proyecto, Visual Studio carga la extensión cuando un elemento de proyecto del tipo asociado se agrega a un proyecto de SharePoint. Por ejemplo, si crea una extensión para los elementos de proyecto del **receptor de eventos** , Visual Studio carga la extensión cuando un usuario agrega un elemento de proyecto de **receptor de eventos** a un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo elemento de proyecto de **receptor de eventos** al proyecto, se usa la misma instancia de la extensión para personalizar el segundo elemento de proyecto.

 Para obtener acceso a una instancia específica del tipo de elemento de proyecto que se va a extender, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos del parámetro *projectItemType* en la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método. Por ejemplo, para determinar cuándo se agrega a un proyecto un elemento de proyecto del tipo que se va a extender, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obtener más información, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identificadores de los elementos de proyecto de SharePoint
 Cada elemento de proyecto de SharePoint tiene un identificador de cadena correspondiente. Debe conocer el identificador de un elemento de proyecto si desea realizar las tareas siguientes:

- Cree una extensión para el elemento de proyecto. En este caso, debe pasar el identificador del elemento de proyecto que desea extender al constructor de <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Para crear una extensión para todos los tipos de elemento de proyecto, pase el **\\** valor * String.

- Agregue el elemento de proyecto a un proyecto mediante programación. En este caso, debe pasar el identificador del elemento de proyecto al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> método.

  En la tabla siguiente se enumeran los identificadores de los elementos de proyecto de SharePoint que se incluyen con Visual Studio.

|Nombre del elemento de proyecto|Identificador de cadena|
|-----------------------|-----------------------|
|Modelo de Data Catalog empresarial|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Tipo de contenido|Microsoft. VisualStudio. SharePoint. ContentType|
|Receptor de eventos|Microsoft. VisualStudio. SharePoint. EventHandler|
|Elemento vacío|Microsoft. VisualStudio. SharePoint. GenericElement|
|Definición de lista<br /><br /> Definición de lista de tipo de contenido|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Instancia de lista|Microsoft. VisualStudio. SharePoint. ListInstance|
|Módulo|Microsoft. VisualStudio. SharePoint. Module|
|Flujo de trabajo secuencial<br /><br /> Flujo de trabajo de equipo de estado|Microsoft. VisualStudio. SharePoint. Workflow|
|Definición del sitio|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Elemento web visual|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Elemento web|Microsoft. VisualStudio. SharePoint. WebPart|
|Formulario de Asociación de flujo de trabajo|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Consulte también
- [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
