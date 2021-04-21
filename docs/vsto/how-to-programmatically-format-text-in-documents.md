---
title: 'Cómo: Dar formato al texto en documentos mediante programación'
description: Obtenga información sobre cómo puede usar el objeto Range para dar formato mediante programación al texto de un documento de Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b91486c193b7b3fdba3b4c5cbbe86f58ffa7f06c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827882"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Cómo: Dar formato al texto en documentos mediante programación
  Puede utilizar el objeto <xref:Microsoft.Office.Interop.Word.Range> para dar formato al texto de un documento de Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 En el siguiente ejemplo se selecciona el primer párrafo del documento y se cambia el tamaño de la fuente, el nombre de la fuente y la alineación. A continuación, se selecciona el intervalo y se muestra un cuadro de mensaje para hacer una pausa antes de ejecutar la siguiente sección de código. En la sección siguiente se llama al método Deshacer del elemento host (para una personalización de nivel de documento) o a la clase (para un complemento <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> de VSTO) tres veces. Aplica el estilo Sangría normal y muestra un cuadro de mensaje para pausar el código. A continuación, el código llama una vez al método <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> y muestra un cuadro de mensaje.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-format-text-using-a-document-level-customization"></a>Para dar formato a un texto mediante una personalización de nivel de documento

1. El siguiente ejemplo se puede usar en una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>Ejemplo para complemento de VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Para dar formato al texto mediante un complemento de VSTO

1. El siguiente ejemplo se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>Consulte también
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Insertar texto mediante programación en documentos de Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
