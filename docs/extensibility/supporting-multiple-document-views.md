---
title: Compatibilidad con múltiples vistas de documentos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699543"
---
# <a name="supporting-multiple-document-views"></a>Compatibilidad con vistas de varios documentos
Puede proporcionar más de una vista de un documento creando datos de documento y objetos de vista de documento independientes para el editor. Algunos casos en los que una vista de documento adicional sería útil son:

- Compatibilidad con ventanas nuevas: desea que el editor proporcione dos o más vistas del mismo tipo, de modo que un usuario que ya tiene una ventana abierta en el editor pueda abrir una nueva ventana seleccionando el comando **Nueva ventana** en el menú **Ventana.**

- Compatibilidad con la vista de formulario y código: desea que el editor proporcione vistas de diferentes tipos. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por ejemplo, proporciona una vista de formulario y una vista de código.

  Para obtener más información acerca de esto, vea el Procedimiento CreateEditorInstance en el archivo EditorFactory.cs en el proyecto de editor personalizado creado por la plantilla de paquete de Visual Studio. Para obtener más información acerca de este proyecto, vea [Tutorial: crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Sincronización de vistas
 Al implementar varias vistas, el objeto de datos de documento es responsable de mantener todas las vistas sincronizadas con los datos. Puede utilizar las interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> de control de eventos para sincronizar varias vistas con los datos.

 Si no utiliza <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> el objeto para sincronizar varias vistas, debe implementar su propio sistema de eventos para controlar los cambios realizados en el objeto de datos de documento. Puede utilizar diferentes niveles de granularidad para mantener varias vistas actualizadas. Con una configuración de granularidad máxima, a medida que escribe en una vista, las otras vistas se actualizan inmediatamente. Con una granularidad mínima, otras vistas no se actualizan hasta que se activan.

## <a name="determining-whether-document-data-is-already-open"></a>Determinar si los datos del documento ya están abiertos
 La tabla de documentos en ejecución (RDT) en el entorno de desarrollo integrado (IDE) ayuda a realizar un seguimiento de si los datos de un documento ya están abiertos, como se muestra en el diagrama siguiente.

 ![Gráfico DocDataView](../extensibility/media/docdataview.gif "Docdataview") Múltiples vistas

 De forma predeterminada, cada vista (objeto de vista de<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>documento) está contenida en su propio marco de ventana ( ). Sin embargo, como ya se ha indicado, los datos del documento se pueden mostrar en varias vistas. Para habilitar esto, Visual Studio comprueba el RDT para determinar si el documento en cuestión ya está abierto en un editor. Cuando el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear el editor, `punkDocDataExisting` un valor no NULL devuelto en el parámetro indica que el documento ya está abierto en otro editor. Para obtener más información sobre cómo funciona el RDT, consulte Ejecución de tabla de [documentos](../extensibility/internals/running-document-table.md).

 En <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> la implementación, examine el `punkDocDataExisting` objeto de datos de documento devuelto para determinar si los datos del documento son adecuados para el editor. (Por ejemplo, un editor HTML solo debe mostrar los datos HTML.) Si es apropiado, el generador del editor debe proporcionar una segunda vista para los datos. Si `punkDocDataExisting` el parámetro `NULL`no lo es , es posible que el objeto de datos del documento esté abierto en otro editor o, lo que es más probable, que los datos del documento ya estén abiertos en una vista diferente con el mismo editor. Si los datos del documento están abiertos en un editor diferente que el generador del editor no admite, Visual Studio no puede abrir el generador del editor. Para obtener más información, consulte [Cómo: Adjuntar vistas a datos](../extensibility/how-to-attach-views-to-document-data.md)de documento .
