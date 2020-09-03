---
title: Agregar código a conjuntos de valores en aplicaciones con n niveles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673115"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregar código a conjuntos de datos en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender la funcionalidad de un conjunto de objetos creando un archivo de clase parcial para el conjunto de archivos y agregando código a él (en lugar de agregar código a *DatasetName*). Archivo DataSet. Designer). Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, [vea](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) [clases y métodos](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)parciales o parciales.

El código que define un conjunto de DataSet se genera cada vez que se realizan cambios en la definición del conjunto de los mismos. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de un conjunto de los mismos. Para evitar que se elimine el código durante la regeneración de un conjunto de DataSet, agregue código al archivo de clase parcial del conjunto de archivos.

De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un nombre de archivo *DatasetName*. Designer. VB (o *DatasetName*). Designer.cs) que contiene el `TableAdapter` código. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado *DatasetName*. DataSet. Designer. VB (o *DatasetName*. DataSet.Designer.cs). Este archivo contiene el código del conjunto de archivos.

> [!NOTE]
> Cuando se separan conjuntos de objetos y `TableAdapter` s (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de elementos parciales existentes en el proyecto no se moverán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
> Cuando es necesario agregar código de validación, el diseñador de DataSet proporciona la funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos. Para obtener más información, vea [agregar validación a un conjunto de datos de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregar código a conjuntos de datos en aplicaciones de n niveles

1. Busque el proyecto que contiene el archivo. xsd (el conjunto de archivos).

2. Seleccione el archivo **. xsd** para abrir el conjunto de archivos.

3. Haga clic con el botón secundario en la tabla de datos a la que desea agregar el código (el nombre de la tabla en la barra de título) y, a continuación, seleccione **Ver código**.

     Se crea una clase parcial y se abre en el editor de código.

4. Agregue código dentro de la declaración de clase parcial.

     En el ejemplo siguiente se muestra dónde agregar código a CustomersDataTable en NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Consulte también

- [Información general sobre las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Información general sobre TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Información general sobre la actualización jerárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Herramientas de conjunto de herramientas en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)