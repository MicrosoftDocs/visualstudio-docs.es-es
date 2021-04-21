---
title: 'Cómo: Mover hojas de cálculo mediante programación dentro de libros'
description: Obtenga información sobre cómo puede cambiar mediante programación la posición de las hojas de cálculo con respecto a otras hojas de cálculo en un libro de Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827297"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Cómo: Mover hojas de cálculo mediante programación dentro de libros
  Mediante programación, puede cambiar la posición de las hojas de cálculo en relación con otras hojas de cálculo en un libro. Si no especifica una ubicación para la hoja movida, Excel crea un nuevo libro que la contiene.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Para mover una hoja de cálculo en una personalización de nivel de documento

1. Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Para mover una hoja de cálculo en un complemento de VSTO

1. Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
