---
title: 'Cómo: abrir documentos de Visio mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para abrir un documento de Visio mediante programación con los métodos Open o OpenEx.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cb24851562beec0b40a8e66a38db202745f4771e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903655"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Cómo: abrir documentos de Visio mediante programación
  Existen dos métodos para abrir documentos de Visio existentes Microsoft Office: Open y OpenEx. El método OpenEx es idéntico al método Open, salvo que proporciona argumentos en los que el llamador puede especificar cómo se abre el documento.

 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA para el método [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) y el método [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Abrir un documento de Visio

### <a name="to-open-a-visio-document"></a>Para abrir un documento de Visio

- Llame al método `Microsoft.Office.Interop.Visio.Documents.Open` y facilite la ruta de acceso completa del documento de Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Abrir un documento de Visio con argumentos especificados

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir un documento de Visio como de solo lectura y acoplado

- Llame al método `Microsoft.Office.Interop.Visio.Documents.OpenEx`, facilite la ruta de acceso completa del documento de Visio e incluya los argumentos que desea utilizar; en este caso, Docked y Read-only.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento de Visio denominado `myDrawing.vsd` debe encontrarse en un directorio denominado `Test` en la carpeta *Mis documentos* (para Windows XP y versiones anteriores) o en la carpeta *documentos* (para Windows Vista).

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
- [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)
