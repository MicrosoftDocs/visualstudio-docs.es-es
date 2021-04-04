---
title: 'Cómo: crear una extensión de elemento de proyecto de SharePoint | Microsoft Docs'
description: Revise cómo crear una extensión de elemento de proyecto cuando desee agregar funcionalidad a un elemento de proyecto de SharePoint que ya está instalado en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8f01d3c15490a19c8cb5071cf7677fcf2b2a5384
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216623"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Cómo: crear una extensión de elemento de proyecto de SharePoint
  Cree una extensión de elemento de proyecto cuando desee agregar funcionalidad a un elemento de proyecto de SharePoint que ya está instalado en Visual Studio. Para obtener más información, vea [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Para crear una extensión de elemento de proyecto

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4. Agregue los siguientes atributos a la clase:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite a Visual Studio detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> tipo al constructor de atributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. En una extensión de elemento de proyecto, este atributo identifica el elemento de proyecto que se desea extender. Pase el identificador del elemento de proyecto al constructor de atributo. Para obtener una lista de los identificadores de los elementos de proyecto que se incluyen con Visual Studio, vea extensión de los [elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).

5. En la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método, use los miembros del parámetro *projectItemType* para definir el comportamiento de la extensión. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto que proporciona acceso a los eventos definidos en las <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces y. Para obtener acceso a una instancia específica del tipo de elemento de proyecto que se va a extender, controle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> los eventos como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo crear una extensión simple para el elemento de proyecto del receptor de eventos. Cada vez que el usuario agrega un elemento de proyecto de receptor de eventos a un proyecto de SharePoint, esta extensión escribe un mensaje en la ventana de **salida** y **lista de errores** ventana.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 En este ejemplo se usa el servicio de proyecto de SharePoint para escribir el mensaje en la ventana de **salida** y **lista de errores** ventana. Para obtener más información, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
