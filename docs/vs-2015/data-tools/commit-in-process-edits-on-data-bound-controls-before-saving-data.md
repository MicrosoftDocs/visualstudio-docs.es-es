---
title: Confirmar tareas de edición en proceso en controles enlazados a datos antes de guardar datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae5d345da49ee33841a50622f3d1c59e2309890c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106298"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al editar los valores de los controles enlazados a datos, deben ir a los usuarios desactivar el registro para confirmar el valor actualizado en el origen de datos subyacente que está enlazado el control actual. Cuando se arrastran elementos desde la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) en un formulario, el primer elemento que se introducen genera código en el **guardar** evento de clic de botón el <xref:System.Windows.Forms.BindingNavigator>. Este código llama a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método de la <xref:System.Windows.Forms.BindingSource>. Por lo tanto, la llamada a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> se genera el método sólo durante los primeros <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.  
  
 La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).  
  
 Puede configurar la aplicación para confirmar automáticamente los cambios, incluso si un usuario intenta guardar los datos sin confirmar los cambios, como parte de la operación de guardar proceso.  
  
> [!NOTE]
>  El diseñador agrega el `BindingSource.EndEdit` código sólo para el primer elemento se coloca en un formulario. Por lo tanto, tiene que agregar una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en el formulario. Puede agregar manualmente una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, puede agregar el `EndEditOnAllBindingSources` método al formulario y llámelo antes de realizar una operación de guardar.  
  
 El siguiente código utiliza un [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) consulta para recorrer en iteración todos <xref:System.Windows.Forms.BindingSource> componentes y llame a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en un formulario.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes BindingSource en un formulario  
  
1. Agregue el siguiente código al formulario que contiene el <xref:System.Windows.Forms.BindingSource> componentes.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2. Agregue la siguiente línea de código inmediatamente antes de llamar a guardar los datos del formulario (la `TableAdapterManager.UpdateAll()` método):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)
