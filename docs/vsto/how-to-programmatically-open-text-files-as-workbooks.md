---
title: 'Cómo: Abrir archivos de texto como libros mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para abrir mediante programación un archivo de texto como un libro de Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14a73d7a06c3d79c15df5b823b38efc9ddceb846
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824177"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Cómo: Abrir archivos de texto como libros mediante programación
  Puede abrir un archivo de texto como libro. Debe pasar el nombre del archivo de texto que desea abrir. Puede especificar varios parámetros opcionales, como el número de fila en el que se va a empezar a analizar y el formato de columna de los datos del archivo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere los siguientes componentes:

- Un archivo de texto delimitado por comas denominado `Test.txt` que contiene al menos tres líneas de texto.

- Archivo de texto `Test.txt` que se va a almacenar en la unidad C.

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
