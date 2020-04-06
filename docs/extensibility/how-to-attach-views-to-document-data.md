---
title: 'Cómo: Adjuntar vistas a datos de documentos ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711085"
---
# <a name="how-to-attach-views-to-document-data"></a>Cómo: Adjuntar vistas a los datos del documento
Si tiene una nueva vista de documento, es posible que pueda adjuntarla a un objeto de datos de documento existente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar si puede adjuntar una vista a un objeto de datos de documento existente

1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. En la `IVsEditorFactory::CreateEditorInstance`implementación `QueryInterface` de , llame al objeto de `CreateEditorInstance` datos de documento existente cuando el IDE llame a la implementación.

    La `QueryInterface` llamada le permite examinar el objeto de datos `punkDocDataExisting` de documento existente, que se especifica en el parámetro.

    Las interfaces exactas que debe consultar, sin embargo, dependen del editor que abra el documento, como se describe en el paso 4.

3. Si no encuentra las interfaces adecuadas en el objeto de datos de documento existente, devuelva un código de error al editor que indique que el objeto de datos de documento es incompatible con el editor.

    En la implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>IDE de , un cuadro de mensaje le notifica que el documento está abierto en otro editor y le pregunta si desea cerrarlo.

4. Si cierra este documento, Visual Studio llama al generador del editor por segunda vez. En esta llamada, el `DocDataExisting` parámetro es igual a NULL. A continuación, la implementación de fábrica del editor puede abrir el objeto de datos de documento en su propio editor.

   > [!NOTE]
   > Para determinar si puede trabajar con un objeto de datos de documento existente, también puede [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] usar el conocimiento privado de la implementación de la interfaz mediante la conversión de un puntero a la clase real de la implementación privada. Por ejemplo, todos los `IVsPersistFileFormat`editores estándar <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>implementan , que hereda de . Por lo tanto, puede llamar `QueryInterface` a <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, y si el identificador de clase en el objeto de datos de documento existente coincide con el identificador de clase de la implementación, puede trabajar con el objeto de datos de documento.

## <a name="robust-programming"></a>Programación sólida
 Cuando Visual Studio llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> a la implementación del método, devuelve un `punkDocDataExisting` puntero al objeto de datos de documento existente en el parámetro, si existe uno. Examine el objeto de `punkDocDataExisting` datos de documento devuelto para determinar si el objeto de datos de documento es adecuado para el editor como se describe en la nota del paso 4 del procedimiento de este tema. Si es apropiado, el generador del editor debe proporcionar una segunda vista para los datos como se describe en [Admitir varias vistas](../extensibility/supporting-multiple-document-views.md)de documentos. Si no es así, debe mostrar un mensaje de error adecuado.

## <a name="see-also"></a>Vea también
- [Soporta múltiples vistas de documentos](../extensibility/supporting-multiple-document-views.md)
- [Datos de documentos y vista de documentos en editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)
