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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 165d0e76eb030d8a173761733245c993115ed315
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Agregar código a TableAdapters en aplicaciones de n niveles
Puede ampliar la funcionalidad de un TableAdapter mediante la creación de un archivo de clase parcial de TableAdapter y agregando código a él (en lugar de agregar código a la *DatasetName*. Archivo DataSet.Designer). Clases parciales permiten al código para una clase concreta se divida entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (tipos)](/dotnet/csharp/language-reference/keywords/partial-type).

El código que define un TableAdapter se genera cada vez que se realizan cambios en el TableAdapter en el conjunto de datos. Este código también se genera cuando se realizan cambios durante el funcionamiento de cualquier asistente que modifica la configuración de TableAdapter. Para evitar que el código que se eliminen durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.

De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName*. Designer.vb (o *DatasetName*. Designer.cs) que contiene el código de TableAdapter. El proyecto designado en la **Dataset Project** propiedad tiene un archivo denominado *DatasetName*. DataSet.Designer.vb (o *DatasetName*. (DataSet.Designer.cs) que contiene el código de conjunto de datos.

> [!NOTE]
>  Al separar conjuntos de datos y los TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se trasladarán automáticamente. Clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
> El conjunto de datos proporciona la funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos cuando es necesaria la validación. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para agregar código de usuario a un TableAdapter en una aplicación con n niveles

1.  Localice el proyecto que contiene el archivo .xsd.

2.  Haga doble clic en el **.xsd** archivo para abrir el **Diseñador de Dataset**.

3.  Haga clic en el objeto TableAdapter que desea agregar el código a y, a continuación, seleccione **ver código**.

     Una clase parcial se crea y se abre en el Editor de código.

4.  Agregue el código dentro de la declaración de clase parcial.

5.  En el ejemplo siguiente se muestra dónde agregar código a la `CustomersTableAdapter` en el `NorthwindDataSet`:

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

- [Introducción a las aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Crear y configurar los TableAdapters](create-and-configure-tableadapters.md)
- [Información general de la actualización jerárquica](hierarchical-update.md)
