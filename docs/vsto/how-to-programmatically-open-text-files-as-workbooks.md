---
title: 'Cómo: abrir archivos de texto como libros mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7bc7caa5dbceb727394b8543b7659cc43e64a36
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257652"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Cómo: abrir archivos de texto como libros mediante programación
  Puede abrir un archivo de texto como un libro. Se debe pasar el nombre del archivo de texto que desea abrir. Puede especificar varios parámetros opcionales, como el número de fila para iniciar el análisis y el formato de columna de los datos en el archivo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compile-the-code"></a>Compile el código  
 En este ejemplo requiere los siguientes componentes:  
  
-   Un archivo de texto delimitado por comas denominado `Test.txt` que contiene al menos tres líneas de texto.  
  
-   El archivo de texto `Test.txt` se almacenen en la unidad C.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)   
 [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  