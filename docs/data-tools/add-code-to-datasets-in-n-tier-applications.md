---
title: Adición de código a conjuntos de datos en aplicaciones de n niveles
description: Agregue código a los conjuntos de objetos en aplicaciones de n niveles en Visual Studio. Cree un archivo de clase parcial para un conjunto de archivos y agréguele código (en lugar de a DatasetName. DataSet. Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c1a6e424fe76b94321ca79ab08496cd160969890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867534"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Adición de código a conjuntos de datos en aplicaciones de n niveles

Puede extender la funcionalidad de un conjunto de objetos creando un archivo de clase parcial para el conjunto de archivos y agregando código a él (en lugar de agregar código a *DatasetName*). Archivo DataSet. Designer). Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, [vea](/dotnet/visual-basic/language-reference/modifiers/partial) [clases y métodos](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)parciales o parciales.

El código que define un conjunto de DataSet se genera cada vez que se realizan cambios en la definición del conjunto de código (en el conjunto de tipos). Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de un conjunto de los mismos. Para evitar que se elimine el código durante la regeneración de un conjunto de DataSet, agregue código al archivo de clase parcial del conjunto de archivos.

De forma predeterminada, después de separar el código de conjunto de datos y TableAdapter, el resultado es un archivo de clase discreto en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName. Designer. VB* (o *DatasetName.Designer.CS*) que contiene el código de TableAdapter. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado *DatasetName. DataSet. Designer. vb* (o *DatasetName.DataSet.Designer.CS*). Este archivo contiene el código del conjunto de archivos.

> [!NOTE]
> Cuando se separan los conjuntos de objetos y TableAdapters (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de tipos parciales existentes en el proyecto no se moverán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
> Cuando es necesario agregar código de validación, el conjunto de los tipos proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos. Para obtener más información, vea [agregar validación a un conjunto de datos de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Para agregar código a conjuntos de valores en aplicaciones con n niveles

1. Busque el proyecto que contiene el archivo *. xsd* .

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

## <a name="see-also"></a>Vea también

- [Información general sobre las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Crear y configurar TableAdapters](create-and-configure-tableadapters.md)
- [Información general sobre la actualización jerárquica](hierarchical-update.md)
- [Herramientas de conjunto de herramientas en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
