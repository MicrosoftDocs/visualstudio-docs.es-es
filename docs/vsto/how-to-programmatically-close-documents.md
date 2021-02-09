---
title: 'Cómo: cerrar documentos mediante programación'
description: Obtenga información acerca de cómo puede cerrar el documento activo o puede especificar un Microsoft Office documento de Word para cerrarlo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 96a18245e477000e1d4969a3e1e597443c6f3372
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903723"
---
# <a name="how-to-programmatically-close-documents"></a>Cómo: cerrar documentos mediante programación
  Puede cerrar el documento activo o especificar el documento que se va a cerrar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Cerrar el documento activo
 Hay dos procedimientos para cerrar el documento activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Para cerrar el documento activo en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.Close%2A> de la clase `ThisDocument` del proyecto para cerrar el documento asociado a la personalización. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` .

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Para cerrar el documento activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A> de la propiedad <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> para cerrar el documento activo. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>Cerrar un documento que se especifica por nombre
 La manera en que se cierra un documento que se especifica por nombre es el mismo para las personalizaciones de nivel de documento y las de complemento de VSTO.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Para cerrar un documento que se especifica por el nombre

1. Especifique el nombre del documento como argumento para la colección <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> y, después, llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . En el siguiente ejemplo de código, se supone que un documento llamado **NewDocument** está abierto en Word.

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>Vea también
- [Cómo: abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Cómo: guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
