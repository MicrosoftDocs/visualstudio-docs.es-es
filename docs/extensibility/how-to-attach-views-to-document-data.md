---
title: 'Cómo: adjuntar vistas a datos de documento | Microsoft Docs'
description: Es posible que pueda adjuntar una nueva vista de documento a un objeto de datos de documento existente. Utilice este procedimiento para determinar si puede adjuntar la vista.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a034fc1c7cded7de4ead38cfba5d3410341c95d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057421"
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
