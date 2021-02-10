---
title: XMLNode (control)
description: Obtenga información sobre que el control XMLNode es un objeto de nodo XML asignado que expone eventos y se puede enlazar a datos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9e86bfbe7af122e2557178f5d70256903d0cc740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949719"
---
# <a name="xmlnode-control"></a>XMLNode (control)
  **Importante** La información configurada en este tema con respecto a Microsoft Word se presenta exclusivamente para la ventaja y el uso de las personas y organizaciones que se encuentran fuera del Estados Unidos y de sus territorios, o bien el desarrollo de programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft antes de la 2010 de enero, cuando Microsoft quitó una implementación de funcionalidad específica relacionada con XML personalizado de Es posible que la información relativa a Microsoft Word no sea leída ni utilizada por personas u organizaciones en el Estados Unidos ni en sus territorios que utilicen o desarrollen programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010; Estos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para usarlos fuera del Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 El <xref:Microsoft.Office.Tools.Word.XMLNode> control es un objeto de nodo XML asignado que expone eventos y se puede enlazar a datos. El <xref:Microsoft.Office.Tools.Word.XMLNode> control solo se crea cuando se asigna un elemento de esquema que no es de repetición a un Microsoft Office documento de Word. Una vez que Visual Studio crea el nodo XML, puede programar directamente sin tener que recorrer el modelo de objetos de Word.

 El <xref:Microsoft.Office.Tools.Word.XMLNode> control solo se puede eliminar quitando la asignación de elementos de Word.

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> control admite el enlace de datos simple. El nodo XML se debe enlazar a un origen de datos utilizando la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propiedad. Si los datos del conjunto de datos enlazado se actualizan, el control <xref:Microsoft.Office.Tools.Word.XMLNode> reflejará los cambios.

## <a name="formatting"></a>Aplicación de formato
 El formato que se puede aplicar a un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto se puede aplicar a un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Esto incluye las fuentes, los estilos de subrayado y los estilos de carácter.

## <a name="events"></a>Events
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Comparar eventos
 Puede capturar un evento cuando el usuario mueve el cursor dentro del contexto de un <xref:Microsoft.Office.Tools.Word.XMLNode> control determinado. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNode> control denominado `Customer` que tiene un control secundario <xref:Microsoft.Office.Tools.Word.XMLNode> denominado y `Company` `Company` tiene dos <xref:Microsoft.Office.Tools.Word.XMLNode> controles secundarios denominados `CompanyName` y, `CompanyRegion` como se indica a continuación:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si desea mostrar un control en el panel de acciones siempre que el cursor se mueva al `Company` nodo, no debe importar si el cursor se coloca en `CompanyName` o `CompanyRegion` porque ambos se encuentran dentro del contexto de `Company` . En este caso, puede escribir el código en el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento de `Company` .

 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNode> control, <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> se generan los eventos y. En la tabla siguiente se muestran las diferencias entre estos eventos.

|Seleccionar evento|Evento ContextEnter|
|------------------|------------------------|
|Se produce cuando el cursor se coloca dentro de un <xref:Microsoft.Office.Tools.Word.XMLNode> .|Aparece cuando el cursor se coloca dentro de <xref:Microsoft.Office.Tools.Word.XMLNode> o uno de sus nodos descendentes, en un área situada fuera del contexto del nodo. En otras palabras, solo se genera cuando cambia el contexto.|

 Por ejemplo, cuando se mueve el cursor desde fuera de `Customer` a `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> se genera el evento para `Customer` , `Company` y `CompanyName` . Si, a continuación, mueve el cursor de `CompanyName` a `CompanyRegion` , solo <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> se genera el evento para `CompanyRegion` porque todavía está en el contexto de `Company` y de `Customer` .

 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> evento y el evento <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>Vea también
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes (control)](../vsto/xmlnodes-control.md)
- [Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
