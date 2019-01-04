---
title: XMLNode (control)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f83d829ac5067d751cc035ac83c0fb3397178658
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927446"
---
# <a name="xmlnode-control"></a>XMLNode (control)
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 El <xref:Microsoft.Office.Tools.Word.XMLNode> control es un objeto de nodo XML asignado que expone eventos y se puede enlazar a datos. El <xref:Microsoft.Office.Tools.Word.XMLNode> control sólo se crea cuando un elemento de esquema no es de repetición se asigna a un documento de Microsoft Office Word. Después de que Visual Studio crea el nodo XML, puede programar con él directamente sin tener que recorrer el modelo de objetos de Word.  
  
 El <xref:Microsoft.Office.Tools.Word.XMLNode> control puede eliminarse quitando la asignación de elementos en Word.  
  
## <a name="bind-data-to-the-control"></a>Enlazar datos al control  
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> control admite el enlace de datos simple. El nodo XML debe enlazarse a un origen de datos mediante el uso de la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propiedad. Si los datos del conjunto de datos enlazado se actualizan, el control <xref:Microsoft.Office.Tools.Word.XMLNode> reflejará los cambios.  
  
## <a name="formatting"></a>Formato  
 El formato que se pueden aplicar a un <xref:Microsoft.Office.Interop.Word.XMLNode> objeto se puede aplicar a un <xref:Microsoft.Office.Tools.Word.XMLNode> control. Esto incluye fuentes, estilos de subrayado y estilos de carácter.  
  
## <a name="events"></a>Eventos  
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Word.XMLNode> :  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="compare-events"></a>Comparar eventos  
 Puede capturar un evento cuando el usuario mueve el cursor dentro del contexto de una determinada <xref:Microsoft.Office.Tools.Word.XMLNode> control. Por ejemplo, podría tener un <xref:Microsoft.Office.Tools.Word.XMLNode> control denominado `Customer` que tiene un elemento secundario <xref:Microsoft.Office.Tools.Word.XMLNode> control denominado `Company`, y `Company` tiene dos secundarios <xref:Microsoft.Office.Tools.Word.XMLNode> controles denominados `CompanyName` y `CompanyRegion` como sigue:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si desea mostrar un control en el panel de acciones cada vez que se mueve el cursor en el `Company` nodo, deberían importarle si el cursor se coloca en `CompanyName` o `CompanyRegion` porque son ambos dentro del contexto de `Company`. En este caso, puede escribir el código en el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> událostí `Company`.  
  
 En la mayoría de los casos, cuando el cursor entra en un <xref:Microsoft.Office.Tools.Word.XMLNode> controlar tanto el <xref:Microsoft.Office.Tools.Word.XMLNode.Select> y <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> se generan eventos. En la tabla siguiente se muestra las diferencias entre estos eventos.  
  
|Seleccionar evento|Evento ContextEnter|  
|------------------|------------------------|  
|Se produce cuando el cursor se coloca dentro de un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Se produce cuando el cursor se coloca dentro de un <xref:Microsoft.Office.Tools.Word.XMLNode> o uno de sus nodos descendientes, en un área fuera del contexto del nodo. En otras palabras, se genera solo cuando cambia el contexto.|  
  
 Por ejemplo, cuando mueve el cursor desde fuera de `Customer` en `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos para `Customer`, `Company`, y `CompanyName` se genera. Si, a continuación, mueve el cursor de `CompanyName` a `CompanyRegion`, solo el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos para `CompanyRegion` se produce porque todavía está dentro del contexto de ambos `Company` y `Customer`.  
  
 Existen las mismas diferencias entre el <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> eventos y <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> eventos.  
  
## <a name="see-also"></a>Vea también  
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes (control)](../vsto/xmlnodes-control.md)   
 [Cómo: Agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
