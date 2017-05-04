---
title: "C&#243;mo: Abrir archivos de texto como libros mediante programaci&#243;n | Microsoft Docs"
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
  - "texto [desarrollo de Office en Visual Studio], archivos de texto"
  - "archivos de texto, abrir como libros"
  - "libros, abrir archivos de texto como"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Abrir archivos de texto como libros mediante programaci&#243;n
  Puede abrir un archivo de texto como un libro.  Es necesario pasar por el nombre del archivo de texto que desea abrir.  Puede especificar varios parámetros opcionales, como el número de fila a partir de la que iniciar el análisis y el formato de las columnas de datos del archivo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## Compilar el código  
 Este ejemplo de código requiere los siguientes componentes:  
  
-   Un archivo de texto delimitado por comas denominado `Test.txt` que contenga al menos tres líneas de texto.  
  
-   El archivo de texto `Test.txt` debe estar almacenado en la unidad C.  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)   
 [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  