---
title: Copiar y pegar formas en un documento de Visio mediante programación
description: Obtenga información sobre cómo copiar formas en una página de un documento mediante programación y pegarlas en una nueva página del mismo documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7cda46330967ef2b2b08db2109a030bbef8cace
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828558"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Cómo: Copiar y pegar formas en un documento de Visio mediante programación
  Puede copiar formas de la página de un documento y pegarlas en una nueva página en ese mismo documento, mediante programación. Puede decidir pegarlas en la ubicación predeterminada (el centro de la ventana activa) o en las mismas ubicaciones de coordenadas de la página original.

## <a name="copy-and-paste-shapes"></a>Copiar y pegar formas
 Para obtener detalles acerca del modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)y [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Copiar formas en el centro de otra página

- En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en el centro de la segunda página.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiar y pegar formas con las mismas posiciones
 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)y [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Si necesita controlar el formato de la información pegada y (opcionalmente) establecer un vínculo a un archivo de código fuente (por ejemplo, un documento de Microsoft Office Word), use el método PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Copiar las formas y sus ubicaciones en otra página

- En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en la segunda página junto a sus ubicaciones de coordenadas originales.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)
- [Cómo: Agregar formas a un documento de Visio mediante programación](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
