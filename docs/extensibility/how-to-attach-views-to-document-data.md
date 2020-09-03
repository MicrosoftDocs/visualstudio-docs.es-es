---
title: 'Cómo: adjuntar vistas a datos de documento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5437e3a5d4fb0d6d33d570eb4d8923245cb287b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905894"
---
# <a name="how-to-attach-views-to-document-data"></a>Cómo: adjuntar vistas a datos de documento
Si tiene una nueva vista de documento, es posible que pueda adjuntarla a un objeto de datos de documento existente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar si puede adjuntar una vista a un objeto de datos de documento existente

1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. En la implementación de `IVsEditorFactory::CreateEditorInstance` , llame a `QueryInterface` en el objeto de datos de documento existente cuando el IDE llame a su `CreateEditorInstance` implementación.

    `QueryInterface`La llamada a le permite examinar el objeto de datos de documento existente, que se especifica en el `punkDocDataExisting` parámetro.

    Sin embargo, las interfaces exactas que se deben consultar dependen del editor que abre el documento, como se describe en el paso 4.

3. Si no encuentra las interfaces adecuadas en el objeto de datos de documento existente, devuelva un código de error al editor que indique que el objeto de datos del documento es incompatible con el editor.

    En la implementación del IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , un cuadro de mensaje le notifica que el documento está abierto en otro editor y pregunta si desea cerrarlo.

4. Si cierra este documento, Visual Studio llamará al generador de editores por segunda vez. En esta llamada, el `DocDataExisting` parámetro es igual a NULL. La implementación del generador de editores puede abrir el objeto de datos de documento en su propio editor.

   > [!NOTE]
   > Para determinar si puede trabajar con un objeto de datos de documento existente, también puede usar el conocimiento privado de la implementación de la interfaz mediante la conversión de un puntero a la [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] clase real de la implementación privada. Por ejemplo, todos los editores estándar implementan `IVsPersistFileFormat` , que hereda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Por lo tanto, puede llamar a `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> y si el identificador de clase en el objeto de datos de documento existente coincide con el identificador de clase de la implementación, puede trabajar con el objeto de datos del documento.

## <a name="robust-programming"></a>Programación sólida
 Cuando Visual Studio llama a su implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, devuelve un puntero al objeto de datos del documento existente en el `punkDocDataExisting` parámetro, si existe uno. Examine el objeto de datos de documento devuelto en `punkDocDataExisting` para determinar si el objeto de datos de documento es adecuado para el editor tal y como se describe en la nota del paso 4 del procedimiento de este tema. Si es adecuado, el generador de editores debe proporcionar una segunda vista para los datos, tal y como se describe en [compatibilidad con varias vistas de documentos](../extensibility/supporting-multiple-document-views.md). En caso contrario, debería mostrar un mensaje de error adecuado.

## <a name="see-also"></a>Consulte también
- [Compatibilidad con varias vistas de documento](../extensibility/supporting-multiple-document-views.md)
- [Datos de documento y vista de documento en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)
