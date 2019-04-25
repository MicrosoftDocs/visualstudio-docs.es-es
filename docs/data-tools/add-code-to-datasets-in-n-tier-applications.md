---
title: Agregar código a conjuntos de datos en aplicaciones de n niveles
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dbd65c5247a82f2a58a57e50402ecde5d330cc9b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111693"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregar código a conjuntos de datos en aplicaciones de n niveles
Puede ampliar la funcionalidad de un conjunto de datos mediante la creación de un archivo de clase parcial para el conjunto de datos y agregar código a ella (en lugar de agregar código a la *DatasetName*. Archivo Dataset.Designer). Las clases parciales permiten código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

El código que define un conjunto de datos se genera cada vez que se realizan cambios en la definición del conjunto de datos (en el conjunto de datos con tipo). Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de un conjunto de datos. Para evitar que el código que se eliminen durante la regeneración de un conjunto de datos, agregue código al archivo de clase parcial del conjunto de datos.

De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase discretos en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName.Designer.vb* (o *DatasetName.Designer.cs*) que contiene el código del TableAdapter. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs*) . Este archivo contiene el código de conjunto de datos.

> [!NOTE]
>  Al separar conjuntos de datos y TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
>  Cuando es necesario agregar código de validación, el conjunto de datos con tipo proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Para agregar código a conjuntos de datos en aplicaciones de n niveles

1. Busque el proyecto que contiene el *.xsd* archivo.

2. Seleccione el **.xsd** archivo para abrir el conjunto de datos.

3. Haga clic en la tabla de datos a la que desea agregar el código (el nombre de tabla en la barra de título) y, a continuación, seleccione **ver código**.

     Una clase parcial se crea y se abre en el Editor de código.

4. Agregue el código dentro de la declaración de clase parcial.

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

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Crear y configurar TableAdapters](create-and-configure-tableadapters.md)
- [Información general sobre la actualización jerárquica](hierarchical-update.md)
- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)