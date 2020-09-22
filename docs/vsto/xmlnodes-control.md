---
title: XMLNodes (control)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ad16165924a33a25dab2b1cfb49a0a7bbfe0875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843314"
---
# <a name="xmlnodes-control"></a>XMLNodes (control)
  **Importante** La información configurada en este tema con respecto a Microsoft Word se presenta exclusivamente para la ventaja y el uso de las personas y organizaciones que se encuentran fuera del Estados Unidos y de sus territorios, o bien el desarrollo de programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft antes de la 2010 de enero, cuando Microsoft quitó una implementación de funcionalidad específica relacionada con XML personalizado de Es posible que la información relativa a Microsoft Word no sea leída ni utilizada por personas u organizaciones en el Estados Unidos ni en sus territorios que utilicen o desarrollen programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010; Estos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para usarlos fuera del Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 El <xref:Microsoft.Office.Tools.Word.XMLNodes> control es una colección de objetos de nodo XML asignados que expone eventos. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control solo se crea cuando se asigna un elemento de esquema repetido a un Microsoft Office documento de Word. Si el elemento repetido contiene elementos secundarios, cada uno de los elementos secundarios también se crea como un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.

 Después de que Visual Studio cree la colección de nodos XML, puede programar en el control directamente sin tener que recorrer el modelo de objetos de Word. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control solo se puede eliminar quitando la asignación de elementos del documento.

> [!NOTE]
> Si obtiene acceso a un elemento secundario del <xref:Microsoft.Office.Tools.Word.XMLNodes> control a través de la <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propiedad, devuelve un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto en lugar de un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Para obtener más información, vea [limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> control no admite el enlace de datos. Esto se debe <xref:Microsoft.Office.Tools.Word.XMLNodes> a que el control no tiene capacidades de enlace de datos complejas y el enlace de datos simple no puede representar datos de repetición.

## <a name="formatting"></a>Formato
 Cualquier formato que se pueda aplicar al texto dentro del documento se puede aplicar a un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.

## <a name="events"></a>Eventos
 Los eventos disponibles para el <xref:Microsoft.Office.Tools.Word.XMLNodes> control son los siguientes:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Comparar eventos
 Puede capturar un evento cuando el usuario mueve el cursor dentro del contexto de un <xref:Microsoft.Office.Tools.Word.XMLNodes> control determinado. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNodes> control denominado `Customer` que tiene un control secundario <xref:Microsoft.Office.Tools.Word.XMLNodes> denominado y `Company` `Company` tiene dos <xref:Microsoft.Office.Tools.Word.XMLNodes> controles secundarios denominados `CompanyName` y, `CompanyRegion` como se indica a continuación:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si desea mostrar un control en el panel de acciones siempre que el cursor se mueva al `Company` nodo, no debe importar si el cursor se coloca en `CompanyName` o `CompanyRegion` porque ambos se encuentran dentro del contexto de `Company` . En este caso, puede escribir el código en el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento de `Company` .

 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNodes> control, <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> se generan los eventos y. En la tabla siguiente se muestran las diferencias entre estos eventos.

|Seleccionar evento|Evento ContextEnter|
|------------------|------------------------|
|Se produce cuando se coloca el cursor dentro de uno de los nodos de la colección <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Aparece cuando el cursor se coloca en el interior de uno de los nodos o nodos de descendiente de la colección <xref:Microsoft.Office.Tools.Word.XMLNodes>, desde un área situada fuera del contexto del nodo. En otras palabras, solo se genera cuando cambia el contexto y se puede generar para varios controles anidados <xref:Microsoft.Office.Tools.Word.XMLNodes> .|

 Por ejemplo, cuando se mueve el cursor desde fuera de `Customer` a `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> se generan los eventos de `Customer` , `Company` y `CompanyName` . Si después mueve el cursor de `CompanyName` a `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> se genera el evento solo para `CompanyRegion` , porque el contexto es el mismo para y para `Company` `Customer` . Puede tener varios `Company` nodos en el documento. Si mueve el cursor del `CompanyName` nodo de uno `Company` al `CompanyName` nodo de otro `Company` , el contexto es el mismo, por lo que solo <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> se genera el evento.

 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> evento y el <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.

## <a name="see-also"></a>Vea también
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode (control)](../vsto/xmlnode-control.md)
- [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
