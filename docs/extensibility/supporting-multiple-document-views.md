---
title: Compatibilidad con varias vistas de documento | Microsoft Docs
description: Obtenga información sobre cómo proporcionar más de una vista de un documento mediante el uso de datos de documento independientes y objetos de vista de documento para el editor personalizado en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e54ee028c6a7db2d5d2ea1ab609be6c2887c9829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056212"
---
# <a name="supporting-multiple-document-views"></a>Compatibilidad con vistas de varios documentos
Puede proporcionar más de una vista de un documento creando datos de documento independientes y objetos de vista de documento para el editor. Algunos casos en los que una vista de documento adicional sería útil son:

- Nueva compatibilidad con ventanas: desea que el editor proporcione dos o más vistas del mismo tipo, de modo que un usuario que ya tenga una ventana abierta en el editor pueda abrir una nueva ventana seleccionando el comando **nueva ventana** en el menú **ventana** .

- Compatibilidad con formularios y vistas de código: desea que el editor proporcione vistas de tipos diferentes. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por ejemplo, proporciona una vista de formulario y una vista de código.

  Para obtener más información sobre esto, vea el procedimiento CreateEditorInstance en el archivo EditorFactory. CS en el proyecto de editor personalizado creado por la plantilla de paquete de Visual Studio. Para obtener más información sobre este proyecto, vea [Tutorial: crear un editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Sincronizar vistas
 Cuando se implementan varias vistas, el objeto de datos del documento es responsable de mantener todas las vistas sincronizadas con los datos. Puede utilizar las interfaces de control de eventos en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar varias vistas con los datos.

 Si no usa el <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para sincronizar varias vistas, debe implementar su propio sistema de eventos para controlar los cambios realizados en el objeto de datos del documento. Puede usar diferentes niveles de granularidad para mantener varias vistas actualizadas. Con un valor de granularidad máxima, a medida que escribe en una vista, las demás vistas se actualizan inmediatamente. Con la granularidad mínima, otras vistas no se actualizan hasta que se activan.

## <a name="determining-whether-document-data-is-already-open"></a>Determinar si los datos del documento ya están abiertos
 La tabla de documentos en ejecución (RDT) del entorno de desarrollo integrado (IDE) de ayuda a realizar un seguimiento de si los datos de un documento ya están abiertos, tal como se muestra en el diagrama siguiente.

 ![Gráfico DocDataView](../extensibility/media/docdataview.gif "Docdataview") Varias vistas

 De forma predeterminada, cada vista (objeto de vista de documento) se encuentra en su propio marco de ventana ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Como ya se ha indicado, sin embargo, los datos del documento se pueden mostrar en varias vistas. Para habilitar esto, Visual Studio comprueba el RDT para determinar si el documento en cuestión ya está abierto en un editor. Cuando el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> a para crear el editor, un valor distinto de NULL devuelto en el `punkDocDataExisting` parámetro indica que el documento ya está abierto en otro editor. Para obtener más información sobre cómo funciona RDT, vea [ejecutar la tabla de documentos](../extensibility/internals/running-document-table.md).

 En su <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementación, examine el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si los datos del documento son adecuados para el editor. (Por ejemplo, solo los datos HTML deberían mostrarse en un editor HTML). Si es adecuado, el generador de editores debe proporcionar una segunda vista para los datos. Si el `punkDocDataExisting` parámetro no es `NULL` , es posible que el objeto de datos del documento esté abierto en otro editor o, lo más probable es que los datos del documento ya estén abiertos en una vista diferente con el mismo editor. Si los datos del documento están abiertos en un editor diferente que no admite el generador de editores, Visual Studio no podrá abrir el generador de editores. Para obtener más información, vea [Cómo: adjuntar vistas a datos de documento](../extensibility/how-to-attach-views-to-document-data.md).
