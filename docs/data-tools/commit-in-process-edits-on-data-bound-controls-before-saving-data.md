---
title: Confirmar ediciones en proceso en controles enlazados a datos antes de guardar
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4a708128f827568e072c617effff17129e41e558
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586944"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos

Al editar valores en controles enlazados a datos, los usuarios deben salir del registro actual para confirmar el valor actualizado en el origen de datos subyacente al que está enlazado el control. Al arrastrar elementos desde la [ventana orígenes de datos](add-new-data-sources.md) hasta un formulario, el primer elemento que se coloca genera código en el evento click del botón **Guardar** del <xref:System.Windows.Forms.BindingNavigator>. Este código llama al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del <xref:System.Windows.Forms.BindingSource>. Por consiguiente, la llamada al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> se genera solo para el primer <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.

La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

Puede configurar la aplicación para que confirme los cambios automáticamente, incluso si un usuario intenta guardar los datos sin confirmar los cambios, como parte del proceso de guardar.

> [!NOTE]
> El diseñador agrega el código `BindingSource.EndEdit` solo para el primer elemento que se coloca en un formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource> del formulario. Puede Agregar manualmente una línea de código para llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, puede Agregar el método `EndEditOnAllBindingSources` al formulario y llamarlo antes de realizar un guardado.

En el código siguiente se usa una consulta [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) para recorrer en iteración todos los componentes de <xref:System.Windows.Forms.BindingSource> y llamar al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> de cada <xref:System.Windows.Forms.BindingSource> en un formulario.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes de BindingSource en un formulario

1. Agregue el código siguiente al formulario que contiene los componentes de <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Agregue la siguiente línea de código inmediatamente antes de cualquier llamada para guardar los datos del formulario (el método `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
