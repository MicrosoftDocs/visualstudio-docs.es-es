---
title: 'Cómo: abrir archivos de texto como libros mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7a0f1b384aafb491183a750f17653ab55f2003e2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519838"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Cómo: abrir archivos de texto como libros mediante programación
  Puede abrir un archivo de texto como un libro de. Debe pasar el nombre del archivo de texto que desea abrir. Puede especificar varios parámetros opcionales, como el número de fila en el que se va a iniciar el análisis y el formato de columna de los datos del archivo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere los siguientes componentes:

- Un archivo de texto delimitado por comas denominado `Test.txt` que contiene al menos tres líneas de texto.

- Archivo de texto `Test.txt` que se va a almacenar en la unidad C.

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
