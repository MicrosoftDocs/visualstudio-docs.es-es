---
title: 'Cómo: trasladar hojas de cálculo dentro de libros mediante programación'
description: Obtenga información sobre cómo puede cambiar mediante programación la posición de las hojas de cálculo en relación con otras hojas de cálculo de un libro de Microsoft Excel.
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
ms.openlocfilehash: 427f3f47e141d9c3ae17bab4b253389c68d4dc1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888789"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Cómo: trasladar hojas de cálculo dentro de libros mediante programación
  Mediante programación, puede cambiar la posición de las hojas de cálculo en relación con otras hojas de cálculo en un libro. Si no especifica una ubicación para la hoja movida, Excel crea un nuevo libro que la contiene.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Para mover una hoja de cálculo en una personalización de nivel de documento

1. Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Para desplace una hoja de cálculo en un complemento de VSTO

1. Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Cómo: eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
