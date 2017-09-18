---
title: "C&#243;mo: Confirmar tareas de edici&#243;n en proceso en controles enlazados a datos antes de guardar los datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "BindingSource (clase), confirmar registros editados"
  - "confirmar registros editados"
  - "DataBinding (clase), confirmar registros editados"
  - "controles enlazados a datos, ediciones en proceso"
  - "EndEdit (método)"
  - "actualización jerárquica, confirmar registros editados"
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Confirmar tareas de edici&#243;n en proceso en controles enlazados a datos antes de guardar los datos
Al editar los valores en controles enlazados a datos, los usuarios deben navegar fuera del registro actual para confirmar el valor actualizado al origen de datos subyacente al que se enlaza el control.  Al arrastrar los elementos de la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) a un formulario, el primer elemento que se coloca genera el código en el evento Click del botón guardar de <xref:System.Windows.Forms.BindingNavigator>.  Este código llama al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> de <xref:System.Windows.Forms.BindingSource>.  Por consiguiente, la llamada al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> sólo se genera para el primer <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.  
  
 La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma cualquier cambio que esté en proceso en cualquier control con enlace a datos que se esté editando actualmente.  Por consiguiente, si un control con enlace a datos todavía tiene el foco y se hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirmarán antes de que se guarde \(método `TableAdapterManager.UpdateAll`\).  
  
 Puede configurar la aplicación para confirmar los cambios automáticamente, incluso si un usuario intenta guardar datos sin confirmar los cambios, como parte del proceso de guardar.  
  
> [!NOTE]
>  El diseñador agrega el código `BindingSource.EndEdit` únicamente en el primer elemento colocado en un formulario.  Por consiguiente, tiene que agregar una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> en el formulario.  Puede agregar manualmente una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource>.  Como alternativa, puede agregar el método `EndEditOnAllBindingSources` al formulario y llamarlo antes de realizar el proceso de guardar.  
  
 El código siguiente usa una consulta [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) para procesar una iteración en todos los componentes <xref:System.Windows.Forms.BindingSource> y llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> en un formulario.  
  
### Para llamar a EndEdit para todos los componentes BindingSource en un formulario  
  
1.  Agregue el código siguiente al formulario que contiene los componentes <xref:System.Windows.Forms.BindingSource>.  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Agregue inmediatamente la siguiente línea de código antes de cualquier llamada para guardar los datos del formulario \(método `TableAdapterManager.UpdateAll()`\):  
  
     [!code-cs[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## Vea también  
 [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md)   
 [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)