---
title: Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 6c548cd7a91683da88a760e28831a0b13af433c5
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154210"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos

Al editar los valores de los controles enlazados a datos, deben ir a los usuarios desactivar el registro para confirmar el valor actualizado en el origen de datos subyacente que está enlazado el control actual. Cuando se arrastran elementos desde la [ventana Orígenes de datos](add-new-data-sources.md) en un formulario, el primer elemento que se introducen genera código en el **guardar** evento de clic de botón el <xref:System.Windows.Forms.BindingNavigator>. Este código llama a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método de la <xref:System.Windows.Forms.BindingSource>. Por lo tanto, la llamada a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> se genera el método sólo durante los primeros <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.

La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

Puede configurar la aplicación para confirmar automáticamente los cambios, incluso si un usuario intenta guardar los datos sin confirmar los cambios, como parte de la operación de guardar proceso.

> [!NOTE]
> El diseñador agrega el `BindingSource.EndEdit` código sólo para el primer elemento se coloca en un formulario. Por lo tanto, tiene que agregar una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en el formulario. Puede agregar manualmente una línea de código para llamar a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, puede agregar el `EndEditOnAllBindingSources` método al formulario y llámelo antes de realizar una operación de guardar.

El siguiente código utiliza un [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) consulta para recorrer en iteración todos <xref:System.Windows.Forms.BindingSource> componentes y llame a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en un formulario.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes BindingSource en un formulario

1.  Agregue el siguiente código al formulario que contiene el <xref:System.Windows.Forms.BindingSource> componentes.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Agregue la siguiente línea de código inmediatamente antes de llamar a guardar los datos del formulario (la `TableAdapterManager.UpdateAll()` método):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)