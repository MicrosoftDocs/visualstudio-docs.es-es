---
title: "Cómo: abrir mediante programación los archivos de texto como libros | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 45d2b85ea8c005d56ddc076d0b758a0c9e4a2d67
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Cómo: Abrir archivos de texto como libros mediante programación
  También puede abrir un archivo de texto como un libro. Se debe pasar el nombre del archivo de texto que desea abrir. Puede especificar varios parámetros opcionales, como el número de fila para iniciar el análisis y el formato de columna de los datos en el archivo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere los siguientes componentes:  
  
-   Un archivo de texto delimitado por comas denominado `Test.txt` que contiene al menos tres líneas de texto.  
  
-   El archivo de texto `Test.txt` que se almacenará en la unidad C.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)   
 [Cómo: crear nuevos libros de mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  