---
title: XMLNodes (Control) | Documentos de Microsoft
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
- XMLNodes control, events
- XMLNodes control
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2950d1c9bf2edb0715ad588180cec3b5e17da265
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnodes-control"></a>XMLNodes (Control)
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 El <xref:Microsoft.Office.Tools.Word.XMLNodes> control es una colección de objetos de nodo XML asignados que expone eventos. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control sólo se crea cuando se asigna un elemento de esquema repetitivo a un documento de Microsoft Office Word. Si el elemento de repetición contiene elementos secundarios, cada uno de los elementos secundarios también se crea como un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.  
  
 Después de que Visual Studio crea la colección de nodos XML, puede programar con el control directamente sin tener que recorrer el modelo de objetos de Word. El <xref:Microsoft.Office.Tools.Word.XMLNodes> control se puede eliminar quitando la asignación de elemento del documento.  
  
> [!NOTE]  
>  Si tiene acceso a un elemento secundario de la <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar a través de la <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propiedad, devuelve un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto en lugar de un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Para obtener más información, consulta [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Enlazar datos al control  
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> control no admite el enlace de datos. Esto es porque el <xref:Microsoft.Office.Tools.Word.XMLNodes> control no tiene capacidades de enlace de datos complejo y enlace de datos simple no puede representar datos de repetición.  
  
## <a name="formatting"></a>Formato  
 El formato que se pueden aplicar al texto en el documento se puede aplicar a un <xref:Microsoft.Office.Tools.Word.XMLNodes> control.  
  
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
  
## <a name="comparing-events"></a>Comparar eventos  
 Puede capturar un evento cuando el usuario mueve su cursor dentro del contexto de una determinada <xref:Microsoft.Office.Tools.Word.XMLNodes> control. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNodes> control denominado `Customer` que tiene un elemento secundario <xref:Microsoft.Office.Tools.Word.XMLNodes> control denominado `Company`, y `Company` tiene dos secundarios <xref:Microsoft.Office.Tools.Word.XMLNodes> controles denominados `CompanyName` y `CompanyRegion` como se indica a continuación:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si desea mostrar un control en el panel de acciones cada vez que se mueve el cursor en el `Company` nodo, no es importante si el cursor se coloca en `CompanyName` o `CompanyRegion` porque son ambos en el contexto de `Company`. En este caso, puede escribir el código el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos de `Company`.  
  
 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar tanto la <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> y <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> se generan eventos. La siguiente tabla muestra las diferencias entre estos eventos.  
  
|Seleccione un evento|Evento ContextEnter|  
|------------------|------------------------|  
|Se produce cuando el cursor se coloca dentro de uno de los nodos de la <xref:Microsoft.Office.Tools.Word.XMLNodes> colección.|Se produce cuando el cursor se coloca dentro de uno de los nodos o descendientes de los <xref:Microsoft.Office.Tools.Word.XMLNodes> colección, desde un área fuera del contexto del nodo. En otras palabras, se desencadena cuando se cambia el contexto y se puede generar varios anidados <xref:Microsoft.Office.Tools.Word.XMLNodes> controles.|  
  
 Por ejemplo, cuando se mueve el cursor desde fuera de `Customer` en `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos para `Customer`, `Company`, y `CompanyName` se generan. Si, a continuación, mueve el cursor desde `CompanyName` a `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento sólo para `CompanyRegion` se produce porque el contexto es el mismo para ambos `Company` y `Customer`. Puede tener varias `Company` nodos en el documento. Si mueve el cursor desde el `CompanyName` nodo de uno `Company` a la `CompanyName` nodo de otro `Company`, el contexto es el mismo, por lo que solo el <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> evento se desencadena.  
  
 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> eventos y <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> eventos.  
  
## <a name="see-also"></a>Vea también  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode (Control)](../vsto/xmlnode-control.md)   
 [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  