---
title: Agregar código a conjuntos de datos en aplicaciones de n niveles | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4308fb0aa39120704c5537188407a9686e9b13a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988164"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregar código a conjuntos de datos en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ampliar la funcionalidad de un conjunto de datos mediante la creación de un archivo de clase parcial para el conjunto de datos y agregar código a ella (en lugar de agregar código a la *DatasetName*. Archivo Dataset.Designer). Las clases parciales permiten código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [clases y métodos parciales](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

El código que define un conjunto de datos se genera cada vez que se realizan cambios en la definición del conjunto de datos. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de un conjunto de datos. Para evitar que el código que se eliminen durante la regeneración de un conjunto de datos, agregue código al archivo de clase parcial del conjunto de datos.

De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene una filenamed *DatasetName*. Designer.vb (o *DatasetName*. Designer.cs) que contiene el `TableAdapter` código. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado *DatasetName*. DataSet.Designer.vb (o *DatasetName*. (DataSet.Designer.cs). Este archivo contiene el código de conjunto de datos.

> [!NOTE]
> Al separar conjuntos de datos y `TableAdapter`s (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
> Cuando se debe agregar código de validación, el Diseñador de DataSet proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregar código a conjuntos de datos en aplicaciones de n niveles

1.  Busque el proyecto que contiene el archivo .xsd (el conjunto de datos).

2.  Seleccione el **.xsd** archivo para abrir el conjunto de datos.

3.  Haga clic en la tabla de datos a la que desea agregar el código (el nombre de tabla en la barra de título) y, a continuación, seleccione **ver código**.

     Una clase parcial se crea y se abre en el Editor de código.

4.  Agregue el código dentro de la declaración de clase parcial.

     El ejemplo siguiente muestra dónde agregar código a CustomersDataTable en NorthwindDataSet:

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

## <a name="see-also"></a>Vea también

- [Introducción a las aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Información general sobre TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Información general de la actualización jerárquica](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)