---
title: 'Cómo: mover hojas de cálculo dentro de los libros de programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5075008e3b6b2b6f9ae087c0cfe962f2a1191f52
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673904"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Cómo: mover hojas de cálculo dentro de los libros de programación
  Mediante programación, puede cambiar la posición de las hojas de cálculo en relación con otras hojas de cálculo en un libro. Si no especifica una ubicación para la hoja movida, Excel crea un nuevo libro que la contiene.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Para mover una hoja de cálculo en una personalización de nivel de documento  
  
1.  Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Para mover una hoja de cálculo en un complemento de VSTO  
  
1.  Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: ocultar hojas de cálculo de mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Cómo: eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: proteger hojas de cálculo de mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  