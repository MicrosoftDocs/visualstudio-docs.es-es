---
title: Ediciones no confirmadas
description: Confirme las ediciones en proceso en los controles de Windows Forms enlazados a datos antes de guardar los datos. Llame a EndEdit para todos los componentes de BindingSource en un formulario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216324"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar ediciones en proceso en controles enlazados a datos antes de guardar los datos

Al editar valores en controles enlazados a datos, los usuarios deben salir del registro actual para confirmar el valor actualizado en el origen de datos subyacente al que está enlazado el control. Cuando se arrastran elementos desde la [ventana orígenes de datos](add-new-data-sources.md) hasta un formulario, el primer elemento que se coloca genera código en el evento click del botón **Guardar** de <xref:System.Windows.Forms.BindingNavigator> . Este código llama al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método de <xref:System.Windows.Forms.BindingSource> . Por consiguiente, la llamada al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método se genera solo para el primero <xref:System.Windows.Forms.BindingSource> que se agrega al formulario.

La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

Puede configurar la aplicación para que confirme los cambios automáticamente, incluso si un usuario intenta guardar los datos sin confirmar los cambios, como parte del proceso de guardar.

> [!NOTE]
> El diseñador agrega el `BindingSource.EndEdit` código solo para el primer elemento que se coloca en un formulario. Por lo tanto, tiene que agregar una línea de código para llamar al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> en el formulario. Puede Agregar manualmente una línea de código para llamar al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada una de ellas <xref:System.Windows.Forms.BindingSource> . Como alternativa, puede Agregar el `EndEditOnAllBindingSources` método al formulario y llamarlo antes de realizar un guardado.

En el código siguiente se usa una consulta [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) para recorrer en iteración todos <xref:System.Windows.Forms.BindingSource> los componentes y llamar al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada uno <xref:System.Windows.Forms.BindingSource> de ellos en un formulario.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para llamar a EndEdit para todos los componentes de BindingSource en un formulario

1. Agregue el código siguiente al formulario que contiene los <xref:System.Windows.Forms.BindingSource> componentes.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Agregue la siguiente línea de código inmediatamente antes de cualquier llamada para guardar los datos del formulario (el `TableAdapterManager.UpdateAll()` método):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Consulte también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
