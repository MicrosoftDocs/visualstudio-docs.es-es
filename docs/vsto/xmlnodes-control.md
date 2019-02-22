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
ms.openlocfilehash: 3650c06b38ab139c6c4bcc26033922c284dd1184
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604150"
---
# <a name="xmlnodes-control"></a>XMLNodes (control)
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 El <xref:Microsoft.Office.Tools.Word.XMLNodes> control es una colección de objetos de nodo XML asignados que expone eventos. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control sólo se crea cuando se asigna un elemento de esquema repetitivo a un documento de Microsoft Office Word. Si el elemento de repetición contiene elementos secundarios, cada uno de los elementos secundarios también se crea como un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.

 Después de que Visual Studio crea la colección de nodos XML, puede programar el control directamente sin tener que recorrer el modelo de objetos de Word. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control puede eliminarse quitando la asignación de elemento del documento.

> [!NOTE]
>  Si tiene acceso a un elemento secundario de la <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar a través de la <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propiedad, devuelve un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto en lugar de un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Para obtener más información, consulte [limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Enlazar datos al control
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> control no admite el enlace de datos. Esto es porque el <xref:Microsoft.Office.Tools.Word.XMLNodes> control no tiene capacidades de enlace de datos complejos y enlace de datos simple no puede representar datos de repetición.

## <a name="formatting"></a>Formato
 Se puede aplicar cualquier formato que se pueden aplicar al texto en el documento a un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.

## <a name="events"></a>Eventos
 Los eventos disponibles para el <xref:Microsoft.Office.Tools.Word.XMLNodes> control son:

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Comparar eventos
 Puede capturar un evento cuando el usuario mueve el cursor dentro del contexto de una determinada <xref:Microsoft.Office.Tools.Word.XMLNodes> control. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNodes> control denominado `Customer` que tiene un elemento secundario <xref:Microsoft.Office.Tools.Word.XMLNodes> control denominado `Company`, y `Company` tiene dos secundarios <xref:Microsoft.Office.Tools.Word.XMLNodes> controles denominados `CompanyName` y `CompanyRegion` como sigue:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Si desea mostrar un control en el panel de acciones cada vez que se mueve el cursor en el `Company` nodo, deberían importarle si el cursor se coloca en `CompanyName` o `CompanyRegion` porque son ambos dentro del contexto de `Company`. En este caso, puede escribir el código en el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> událostí `Company`.

 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar tanto el <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> y <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> se generan eventos. La siguiente tabla muestra las diferencias entre estos eventos.

|Seleccionar evento|Evento ContextEnter|
|------------------|------------------------|
|Se produce cuando el cursor se coloca dentro de uno de los nodos de la <xref:Microsoft.Office.Tools.Word.XMLNodes> colección.|Se produce cuando el cursor se coloca dentro de uno de los nodos o descendientes de los <xref:Microsoft.Office.Tools.Word.XMLNodes> colección desde un área fuera del contexto del nodo. En otras palabras, solo se genera cuando cambia el contexto y pueden emitirse para varios anidados <xref:Microsoft.Office.Tools.Word.XMLNodes> controles.|

 Por ejemplo, cuando mueve el cursor desde fuera de `Customer` en `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos para `Customer`, `Company`, y `CompanyName` se generan. Si, a continuación, mueve el cursor de `CompanyName` a `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos solo para `CompanyRegion` se produce porque el contexto es el mismo para ambos `Company` y `Customer`. Puede tener varios `Company` nodos en el documento. Si mueve el cursor desde el `CompanyName` nodo de uno `Company` a la `CompanyName` nodo de otro `Company`, el contexto es el mismo, por lo que solo el <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> provoca el evento.

 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> eventos y el <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> eventos.

## <a name="see-also"></a>Vea también
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode (control)](../vsto/xmlnode-control.md)
- [Cómo: Agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
