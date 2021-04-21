---
title: 'Cómo: Restaurar selecciones mediante programación después de las búsquedas'
description: Obtenga información sobre cómo puede usar Visual Studio para restaurar mediante programación las selecciones después de las búsquedas en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824022"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Cómo: Restaurar selecciones mediante programación después de las búsquedas
  Si encuentra y reemplaza texto en un documento, es posible que desee restaurar la selección original del usuario una vez completada la búsqueda.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 El código del procedimiento de ejemplo usa dos <xref:Microsoft.Office.Interop.Word.Range> objetos . Uno almacena el actual y otro establece todo el documento que se <xref:Microsoft.Office.Interop.Word.Selection> va a usar como intervalo de búsqueda.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Para restaurar la selección original del usuario después de una búsqueda

1. Cree los <xref:Microsoft.Office.Interop.Word.Range> objetos para el documento y la selección actual.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Realice la operación de búsqueda y reemplazo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Seleccione el intervalo de inicio para restaurar la selección original del usuario.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   En el siguiente ejemplo se muestra el método completo.

## <a name="example"></a>Ejemplo
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Consulte también
- [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: Establecer opciones de búsqueda mediante programación en Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
