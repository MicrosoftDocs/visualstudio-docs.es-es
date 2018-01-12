---
title: XMLNode (Control) | Documentos de Microsoft
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
helpviewer_keywords: XMLNode control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f89c80850c5f91cdc6d147d733d2626f8641dab6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnode-control"></a>XMLNode (Control)
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 El <xref:Microsoft.Office.Tools.Word.XMLNode> control es un objeto de nodo XML asignado que expone eventos y se puede enlazar a datos. El <xref:Microsoft.Office.Tools.Word.XMLNode> control sólo se crea cuando se asigna un elemento de esquema no repetitivo en un documento de Microsoft Office Word. Después de que Visual Studio crea el nodo XML, puede programar con ella directamente sin tener que recorrer el modelo de objetos de Word.  
  
 El <xref:Microsoft.Office.Tools.Word.XMLNode> control se puede eliminar quitando la asignación de elemento en Word.  
  
## <a name="binding-data-to-the-control"></a>Enlazar datos al control  
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> control admite el enlace de datos simple. El nodo XML debe enlazarse a un origen de datos mediante el uso de la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propiedad. Si los datos del conjunto de datos enlazado se actualizan, el <xref:Microsoft.Office.Tools.Word.XMLNode> control refleja los cambios.  
  
## <a name="formatting"></a>Formato  
 Formato que se pueden aplicar a un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto puede aplicarse a un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Esto incluye fuentes, estilos de subrayado y estilos de carácter.  
  
## <a name="events"></a>Eventos  
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Word.XMLNode>:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Comparar eventos  
 Puede capturar un evento cuando el usuario mueve su cursor dentro del contexto de una determinada <xref:Microsoft.Office.Tools.Word.XMLNode> control. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNode> control denominado `Customer` que tiene un elemento secundario <xref:Microsoft.Office.Tools.Word.XMLNode> control denominado `Company`, y `Company` tiene dos secundarios <xref:Microsoft.Office.Tools.Word.XMLNode> controles denominados `CompanyName` y `CompanyRegion` como se indica a continuación:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si desea mostrar un control en el panel de acciones cada vez que se mueve el cursor en el `Company` nodo, no es importante si el cursor se coloca en `CompanyName` o `CompanyRegion` porque son ambos en el contexto de `Company`. En este caso, puede escribir el código el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos de `Company`.  
  
 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNode> controlar tanto la <xref:Microsoft.Office.Tools.Word.XMLNode.Select> y <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> se generan eventos. En la tabla siguiente se muestra las diferencias entre estos eventos.  
  
|Seleccione un evento|Evento ContextEnter|  
|------------------|------------------------|  
|Se produce cuando el cursor se coloca dentro de un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Se produce cuando el cursor se coloca dentro de un <xref:Microsoft.Office.Tools.Word.XMLNode> o uno de sus nodos descendientes, en un área fuera del contexto del nodo. En otras palabras, se desencadena cuando se cambia el contexto.|  
  
 Por ejemplo, cuando se mueve el cursor desde fuera de `Customer` en `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos para `Customer`, `Company`, y `CompanyName` se genera. Si, a continuación, mueve el cursor desde `CompanyName` a `CompanyRegion`, solo el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos para `CompanyRegion` se genera porque todavía está dentro del contexto de ambos `Company` y `Customer`.  
  
 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> eventos y <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> eventos.  
  
## <a name="see-also"></a>Vea también  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes (Control)](../vsto/xmlnodes-control.md)   
 [Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Cómo: asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  