---
title: 'Cómo: Crear nuevos documentos mediante programación'
description: Obtenga información sobre cómo puede crear nuevos documentos en Microsoft Word mediante programación mediante Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4ba9aed0194804354af62fb1fd582b8ea12ac6b1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825191"
---
# <a name="how-to-programmatically-create-new-documents"></a>Cómo: Crear nuevos documentos mediante programación
  Al crear un documento mediante programación, el nuevo documento es un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo. Este objeto no tiene los eventos y capacidades de enlace de datos adicionales de un elemento host <xref:Microsoft.Office.Tools.Word.Document>. Para obtener más información, vea [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Al desarrollar un proyecto de nivel de documento, no se pueden agregar elementos host <xref:Microsoft.Office.Tools.Word.Document> al proyecto mediante programación. En un proyecto de complemento de VSTO, puede convertir cualquier objeto <xref:Microsoft.Office.Interop.Word.Document> en un elemento host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución. Para obtener más información, vea Extender documentos de Word y libros de Excel en [complementos vsTO en tiempo de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Para crear un documento nuevo basado en la plantilla Normal

- Use el método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Documents> para crear un nuevo documento basado en la plantilla Normal. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet1":::

## <a name="use-custom-templates"></a>Uso de plantillas personalizadas
 El método tiene un argumento Template opcional para crear un nuevo documento <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> basado en una plantilla que no sea la plantilla Normal.  Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Para crear un documento nuevo basado en una plantilla personalizada

- Llame al método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Documents> y especifique la ruta de acceso a la plantilla. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet2":::

## <a name="see-also"></a>Consulte también
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
