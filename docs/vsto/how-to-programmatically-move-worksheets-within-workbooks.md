---
title: "C&#243;mo: Mover hojas de c&#225;lculo dentro de libros mediante programaci&#243;n"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "hojas de cálculo, mover"
  - "libros, mover hojas de cálculo"
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Mover hojas de c&#225;lculo dentro de libros mediante programaci&#243;n
  Mediante programación, puede cambiar la posición de las hojas de cálculo en relación con otras hojas de cálculo en un libro. Si no especifica una ubicación para la hoja movida, Excel crea un nuevo libro que la contiene.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para mover una hoja de cálculo en una personalización de nivel de documento  
  
1.  Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#24)]  
  
### Para mover una hoja de cálculo en un complemento VSTO  
  
1.  Asigne el número total de hojas del libro a una variable y mueva la primera hoja de cálculo para que se convierta en la última.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#16)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  