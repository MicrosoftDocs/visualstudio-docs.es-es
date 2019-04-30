---
title: Procedimiento Abrir archivos de texto mediante programación como libros
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61e51f6274bc22ed0d34d33f5ff85bfbfbd927bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812466"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Procedimiento Abrir archivos de texto mediante programación como libros
  Puede abrir un archivo de texto como un libro. Se debe pasar el nombre del archivo de texto que desea abrir. Puede especificar varios parámetros opcionales, como el número de fila para iniciar el análisis y el formato de columna de los datos en el archivo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo requiere los siguientes componentes:

- Un archivo de texto delimitado por comas denominado `Test.txt` que contiene al menos tres líneas de texto.

- El archivo de texto `Test.txt` se almacenen en la unidad C.

## <a name="see-also"></a>Vea también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
