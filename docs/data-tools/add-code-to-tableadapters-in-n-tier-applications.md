---
title: Agregar código a TableAdapters en aplicaciones de n niveles
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6454eb53bf6d171e469a4cf2758e0e10a76eab6e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066122"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Agregar código a TableAdapters en aplicaciones de n niveles
Puede ampliar la funcionalidad de un TableAdapter mediante la creación de un archivo de clase parcial del TableAdapter y agregarle código (en lugar de agregar código a la *DatasetName.DataSet.Designer* archivo). Las clases parciales permiten código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (tipos)](/dotnet/csharp/language-reference/keywords/partial-type).

El código que define un TableAdapter se genera cada vez que se realizan cambios en el TableAdapter en el conjunto de datos. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de TableAdapter. Para evitar que el código que se eliminen durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial de TableAdapter.

De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase discretos en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName.Designer.vb* (o *DatasetName.Designer.cs*) que contiene el código del TableAdapter. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs*) que contiene el código del conjunto de datos.

> [!NOTE]
>  Cuando los conjuntos de datos se separan de los TableAdapters (estableciendo la propiedad **DataSet Project**), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente. Las clases de conjunto de datos parciales existentes se deben mover manualmente al proyecto de conjunto de datos.

> [!NOTE]
> El conjunto de datos proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos cuando es necesaria la validación. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para agregar código de usuario a un TableAdapter en una aplicación de n niveles

1. Busque el proyecto que contiene el *.xsd* archivo.

2. Haga doble clic en el *.xsd* archivo para abrir el **Diseñador de Dataset**.

3. Haga clic en el TableAdapter que desea agregar el código a y, a continuación, seleccione **ver código**.

     Una clase parcial se crea y se abre en el Editor de código.

4. Agregue el código dentro de la declaración de clase parcial.

5. El ejemplo siguiente muestra dónde agregar código a la `CustomersTableAdapter` en el `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Vea también

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Crear y configurar TableAdapters](create-and-configure-tableadapters.md)
- [Información general sobre la actualización jerárquica](hierarchical-update.md)
