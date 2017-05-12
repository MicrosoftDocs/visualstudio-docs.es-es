---
title: "C&#243;mo: Rellenar rangos autom&#225;ticamente con datos que cambian de forma incremental mediante programaci&#243;n | Microsoft Docs"
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
  - "Autofill (método) [Excel]"
  - "rellenar rangos automáticamente"
  - "intervalos, rellenar automáticamente"
  - "libros, rellenar rangos"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# C&#243;mo: Rellenar rangos autom&#225;ticamente con datos que cambian de forma incremental mediante programaci&#243;n
  El método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> del objeto <xref:Microsoft.Office.Interop.Excel.Range> permite rellenar automáticamente con valores un rango de una hoja de cálculo.  El método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> se utiliza más frecuentemente para almacenar de forma incremental valores crecientes o decrecientes en un rango.  Puede especificar el comportamiento proporcionando una constante opcional de la enumeración <xref:Microsoft.Office.Interop.Excel.XlAutoFillType>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Cuando utilice <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> debe especificar dos rangos:  
  
-   El rango que llama al método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>, que especifica el punto inicial del relleno y contiene un valor inicial.  
  
-   El rango que desea rellenar, pasado como un parámetro al método <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  El rango de destino debe incluir el rango que contiene el valor inicial.  
  
    > [!NOTE]  
    >  No se puede pasar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en lugar de un rango <xref:Microsoft.Office.Interop.Excel.Range>.  Para obtener más información, vea [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## Compilar el código  
 La primera celda del rango que desee rellenar debe contener un valor inicial.  
  
 El ejemplo requiere que rellene tres regiones:  
  
-   En la columna B se van a incluir cinco días de la semana.  Para el valor inicial, escriba **Lunes** en la celda B1.  
  
-   En la columna C se van a incluir cinco meses.  Para el valor inicial, escriba **Enero** en la celda C1.  
  
-   En la columna D se va a incluir una serie de números, en incrementos de dos para cada fila.  Para los valores iniciales, escriba **4** en la celda D1 y **6** en la celda D2.  
  
## Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: Hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: Ejecutar cálculos de Excel mediante programación](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  