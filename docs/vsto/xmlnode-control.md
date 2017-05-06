---
title: "XMLNode (Control)"
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
  - "XMLNode (control)"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# XMLNode (Control)
  La información de**Importante** The establecida en este tema relacionada con Microsoft Word se presenta exclusivamente para el marcado y el uso de individuos y organizaciones que se encuentran fuera de los Estados Unidos y sus territorios o que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word que se autorizados por Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de la funcionalidad concreta relacionada con XML personalizado de Microsoft Word.  Puede que esta información relacionada con Microsoft Word no sea leída o utilizada por individuos u organizaciones residentes en los Estados Unidos o sus territorios que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word con licencia concedida por Microsoft después del 10 de enero de 2010; dichos productos no tendrán el mismo comportamiento que los productos con licencia anterior a esa fecha o comprados, y con licencia para su uso, fuera de los Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 El control <xref:Microsoft.Office.Tools.Word.XMLNode> es un objeto de nodo XML asignado que expone eventos y se puede enlazar a datos.  Sólo se crea el control <xref:Microsoft.Office.Tools.Word.XMLNode> cuando un elemento de esquema que no es de repetición se asigna a un documento de Microsoft Office Word.  Una vez que Visual Studio crea el nodo XML, es posible programar directamente con el nodo sin tener que recorrer el modelo de objetos de Word.  
  
 El control <xref:Microsoft.Office.Tools.Word.XMLNode> se puede eliminar quitando la asignación de elementos en Word.  
  
## Enlazar datos al control  
 Un control <xref:Microsoft.Office.Tools.Word.XMLNode> admite un enlace de datos simple.  El nodo XML debe enlazarse a un origen de datos mediante la propiedad <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>.  Si los datos del conjunto de datos enlazado se actualizan, el control <xref:Microsoft.Office.Tools.Word.XMLNode> reflejará los cambios.  
  
## Formato  
 El formato que puede aplicarse a un objeto <xref:Microsoft.Office.Interop.Word.XMLNode> también puede aplicarse a un control <xref:Microsoft.Office.Tools.Word.XMLNode>.  Esto incluye fuentes, estilos de subrayado y estilos de carácter.  
  
## Eventos  
 Los siguientes eventos están disponibles para el control <xref:Microsoft.Office.Tools.Word.XMLNode>:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## Comparar eventos  
 Puede capturar un evento cuando el usuario desplaza el cursor dentro del contexto de un control <xref:Microsoft.Office.Tools.Word.XMLNode> determinado.  Por ejemplo, podría tener un control <xref:Microsoft.Office.Tools.Word.XMLNode> denominado `Customer` que tenga un control <xref:Microsoft.Office.Tools.Word.XMLNode> secundario denominado `Company`, y que `Company` tenga dos controles <xref:Microsoft.Office.Tools.Word.XMLNode> secundarios denominados `CompanyName` y `CompanyRegion`, tal como se indica a continuación:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Si desea mostrar un control en el panel de acciones cada vez que el cursor se desplaza al nodo `Company`, debería ser indiferente si el cursor se coloca en `CompanyName` o en `CompanyRegion`, porque ambos se encuentran dentro del contexto de `Company`.  En este caso, puede escribir el código en el evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> de `Company`.  
  
 En la mayoría de los casos, cuando el cursor entra en un control <xref:Microsoft.Office.Tools.Word.XMLNode>, se producen los eventos <xref:Microsoft.Office.Tools.Word.XMLNode.Select> y <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>.  En la siguiente tabla se muestran las diferencias entre estos eventos.  
  
|Evento Select|Evento ContextEnter|  
|-------------------|-------------------------|  
|Aparece cuando el cursor se coloca dentro de un control <xref:Microsoft.Office.Tools.Word.XMLNode>.|Aparece cuando el cursor se coloca dentro de <xref:Microsoft.Office.Tools.Word.XMLNode> o uno de sus nodos descendentes, en un área situada fuera del contexto del nodo.  Es decir, sólo se produce cuando el contexto cambia.|  
  
 Por ejemplo, cuando mueve el cursor desde fuera de `Customer` a `CompanyName`, se provoca el evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> para `Customer`, `Company` y `CompanyName`.  Si después mueve el cursor de `CompanyName` a `CompanyRegion`, sólo se provoca el evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> para `CompanyRegion` porque todavía está dentro del contexto de `Company` y `Customer`.  
  
 Existen las mismas diferencias entre el evento <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> y el evento <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>.  
  
## Vea también  
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes &#40;Control&#41;](../vsto/xmlnodes-control.md)   
 [Cómo: Agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  