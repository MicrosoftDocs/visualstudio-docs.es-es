---
title: "XMLNodes (Control) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLNodes (control)"
  - "XMLNodes (control), eventos"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# XMLNodes (Control)
  La información de**Importante** The establecida en este tema relacionada con Microsoft Word se presenta exclusivamente para el marcado y el uso de individuos y organizaciones que se encuentran fuera de los Estados Unidos y sus territorios o que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word que se autorizados por Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de la funcionalidad concreta relacionada con XML personalizado de Microsoft Word.  Puede que esta información relacionada con Microsoft Word no sea leída o utilizada por individuos u organizaciones residentes en los Estados Unidos o sus territorios que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word con licencia concedida por Microsoft después del 10 de enero de 2010; dichos productos no tendrán el mismo comportamiento que los productos con licencia anterior a esa fecha o comprados, y con licencia para su uso, fuera de los Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 El control <xref:Microsoft.Office.Tools.Word.XMLNodes> es una colección de objetos de nodo XML asignados que expone eventos.  El control <xref:Microsoft.Office.Tools.Word.XMLNodes> sólo se crea cuando se asigna un elemento de repetición de esquema a un documento de Microsoft Office Word.  Si el elemento de repetición contiene elementos secundarios, los elementos secundarios también se crearán como un control <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
 Después de que Visual Studio haya creado la colección de nodos XML, puede programar directamente para el control sin tener que pasar por el modelo de objetos de Word.  El control <xref:Microsoft.Office.Tools.Word.XMLNodes> sólo se puede eliminar quitando el elemento que asigna desde el documento.  
  
> [!NOTE]  
>  Si tiene acceso a un elemento secundario del control <xref:Microsoft.Office.Tools.Word.XMLNodes> a través de la propiedad <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>, devuelve un objeto <xref:Microsoft.Office.Interop.Word.XMLNode> en lugar de un control <xref:Microsoft.Office.Tools.Word.XMLNode>.  Para obtener más información, vea [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Enlazar datos al control  
 Los controles <xref:Microsoft.Office.Tools.Word.XMLNodes> no admiten el enlace de datos.  Esto ocurre porque el control <xref:Microsoft.Office.Tools.Word.XMLNodes> no tiene capacidades de enlace de datos complejo y el enlace de datos simple no puede representar datos de repetición.  
  
## Formato  
 A los controles <xref:Microsoft.Office.Tools.Word.XMLNodes> se puede aplicar cualquier formato que se pueda aplicar al texto del documento.  
  
## Eventos  
 Los eventos disponibles para el control <xref:Microsoft.Office.Tools.Word.XMLNodes> son:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## Comparar eventos  
 Puede capturar un evento cuando el usuario desplaza el cursor dentro del contexto de un control <xref:Microsoft.Office.Tools.Word.XMLNodes> determinado.  Por ejemplo, podría tener un control <xref:Microsoft.Office.Tools.Word.XMLNodes> denominado `Customer` que incluyera un control <xref:Microsoft.Office.Tools.Word.XMLNodes> secundario llamado `Company`, y `Company` incluye dos controles <xref:Microsoft.Office.Tools.Word.XMLNodes> secundarios denominados `CompanyName` y `CompanyRegion`, de esta manera:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si desea mostrar un control en el panel de acciones cada vez que el cursor se desplaza al nodo `Company`, debería ser indiferente si el cursor se coloca en `CompanyName` o en `CompanyRegion`, porque ambos se encuentran dentro del contexto de `Company`.  En este caso, puede escribir el código en el evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> de `Company`.  
  
 En la mayoría de los casos, cuando el cursor entra en un control <xref:Microsoft.Office.Tools.Word.XMLNodes>, se producen los eventos <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> y <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>.  En la siguiente tabla se muestran las diferencias entre estos eventos.  
  
|Evento Select|Evento ContextEnter|  
|-------------------|-------------------------|  
|Se produce cuando se coloca el cursor dentro de uno de los nodos de la colección <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Aparece cuando el cursor se coloca en el interior de uno de los nodos o nodos de descendiente de la colección <xref:Microsoft.Office.Tools.Word.XMLNodes>, desde un área situada fuera del contexto del nodo.  Dicho de otra forma, sólo se produce cuando cambia el contexto y se puede producir para varios controles <xref:Microsoft.Office.Tools.Word.XMLNodes> anidados.|  
  
 Por ejemplo, cuando mueve el cursor desde fuera de `Customer` a `CompanyName`, se provocan los eventos <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> para `Customer`, `Company` y `CompanyName`.  Si después mueve el cursor desde `CompanyName` a `CompanyRegion`, sólo se provoca el evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> para `CompanyRegion` porque el contexto es el mismo para `Company` y `Customer`.  Puede tener varios nodos `Company` en el documento.  Si mueve el cursor desde el nodo `CompanyName` de un contexto `Company` al nodo `CompanyName` de otro contexto `Company`, el contexto es igual, por lo que sólo se produce el evento <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>.  
  
 Existen las mismas diferencias entre el evento <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> y el evento <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>.  
  
## Vea también  
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode &#40;Control&#41;](../vsto/xmlnode-control.md)   
 [Cómo: Agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  