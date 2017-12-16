---
title: "Confirmar tareas de edición en proceso en controles enlazados a datos antes de guardar los datos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: d2b0ea1999c9742c04d1bb118d9a036ff2bed5ea
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar tareas de edición en proceso en controles enlazados a datos antes de guardar datos
Al editar los valores de los controles enlazados a datos, los usuarios deben salga del registro actual para confirmar el valor actualizado en el origen de datos subyacente que el control se enlaza a. Cuando se arrastran elementos desde la [ventana Orígenes de datos](add-new-data-sources.md) en un formulario, el primer elemento que se coloca genera el código en el **guardar** evento de clic de botón el <xref:System.Windows.Forms.BindingNavigator>. Este código llama el <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método de la <xref:System.Windows.Forms.BindingSource>. Por lo tanto, la llamada a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método se genera solo para el primer <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.  
  
 El <xref:System.Windows.Forms.BindingSource.EndEdit%2A> llamada confirma los cambios que están en curso, en los controles enlazados a datos que se está editando actualmente. Por lo tanto, si un control enlazado a datos aún tiene foco y hace clic en el **guardar** button, todas las ediciones pendientes en ese control se confirman antes del guardado real (el `TableAdapterManager.UpdateAll` método).  
  
 Puede configurar la aplicación para confirmar automáticamente los cambios, incluso si un usuario intenta guardar datos sin confirmar los cambios, como parte de la operación de guardar proceso.  
  
> [!NOTE]
>  El diseñador agrega la `BindingSource.EndEdit` código solo para el primer elemento se coloca en un formulario. Por tanto, tendrá que agregar una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en el formulario. Puede agregar manualmente una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, puede agregar el `EndEditOnAllBindingSources` método al formulario y se invoca antes de realizar un proceso de guardar.  
  
 El siguiente código utiliza un [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) consulta para recorrer en iteración todos los <xref:System.Windows.Forms.BindingSource> componentes y llame al método el <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en un formulario.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes BindingSource en un formulario  
  
1.  Agregue el código siguiente al formulario que contiene el <xref:System.Windows.Forms.BindingSource> componentes.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Agregue la siguiente línea de código inmediatamente antes de llamar a guardar los datos del formulario (la `TableAdapterManager.UpdateAll()` (método)):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)