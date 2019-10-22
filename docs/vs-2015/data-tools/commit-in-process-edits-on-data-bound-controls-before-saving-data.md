---
title: Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662448"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al editar valores en controles enlazados a datos, los usuarios deben salir del registro actual para confirmar el valor actualizado en el origen de datos subyacente al que está enlazado el control. Al arrastrar elementos desde la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) hasta un formulario, el primer elemento que se coloca genera código en el evento click del botón **Guardar** del <xref:System.Windows.Forms.BindingNavigator>. Este código llama al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del <xref:System.Windows.Forms.BindingSource>. Por consiguiente, la llamada al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> se genera solo para el primer <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.

 La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

 Puede configurar la aplicación para que confirme los cambios automáticamente, incluso si un usuario intenta guardar los datos sin confirmar los cambios, como parte del proceso de guardar.

> [!NOTE]
> El diseñador agrega el código `BindingSource.EndEdit` solo para el primer elemento que se coloca en un formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> del formulario. Puede Agregar manualmente una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, puede Agregar el método `EndEditOnAllBindingSources` al formulario y llamarlo antes de realizar un guardado.

 En el código siguiente se usa una consulta [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) para recorrer en iteración todos los componentes de <xref:System.Windows.Forms.BindingSource> y llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> de cada <xref:System.Windows.Forms.BindingSource> en un formulario.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes de BindingSource en un formulario

1. Agregue el código siguiente al formulario que contiene los componentes de <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Agregue la siguiente línea de código inmediatamente antes de cualquier llamada para guardar los datos del formulario (el método `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Vea también
 [Enlazar controles de Windows Forms a datos en](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) la [actualización jerárquica](../data-tools/hierarchical-update.md) de Visual Studio
