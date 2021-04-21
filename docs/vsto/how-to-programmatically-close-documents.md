---
title: 'Cómo: Cerrar documentos mediante programación'
description: Obtenga información sobre cómo puede cerrar el documento activo o puede especificar un Microsoft Office word para cerrarlo.
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
ms.openlocfilehash: 1b31a35ac1fa452f526d109dd93ca8264f78947b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825360"
---
# <a name="how-to-programmatically-close-documents"></a>Cómo: Cerrar documentos mediante programación
  Puede cerrar el documento activo o especificar el documento que se va a cerrar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Cerrar el documento activo
 Hay dos procedimientos para cerrar el documento activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Para cerrar el documento activo en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.Close%2A> de la clase `ThisDocument` del proyecto para cerrar el documento asociado a la personalización. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` .

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet3":::

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Para cerrar el documento activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A> de la propiedad <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> para cerrar el documento activo. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet3":::

## <a name="close-a-document-that-you-specify-by-name"></a>Cierre un documento que especifique por nombre.
 La manera en que se cierra un documento que se especifica por nombre es el mismo para las personalizaciones de nivel de documento y las de complemento de VSTO.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Para cerrar un documento que se especifica por el nombre

1. Especifique el nombre del documento como argumento para la colección <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> y, después, llame al método <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . En el siguiente ejemplo de código, se supone que un documento llamado **NewDocument** está abierto en Word.

    > [!NOTE]
    > Este ejemplo pasa el valor <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parámetro *SaveChanges* para cerrar sin guardar los cambios ni preguntar al usuario.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet4":::

## <a name="see-also"></a>Consulte también
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Cómo: Guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
