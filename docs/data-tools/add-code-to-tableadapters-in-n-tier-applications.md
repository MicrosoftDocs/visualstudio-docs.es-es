---
title: Agregar código a TableAdapters en aplicaciones de n niveles
description: Agregue código a los adaptadores de tabla en aplicaciones de n niveles. Cree un archivo de clase parcial para TableAdapter y agréguele código (en lugar de a DatasetName. DataSet. Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 85e89e9800f35fc6d27346b4ed3d4757f83a8dfc
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518705"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Agregar código a TableAdapters en aplicaciones de n niveles
Puede extender la funcionalidad de un TableAdapter si crea un archivo de clase parcial para el TableAdapter y le agrega código (en lugar de agregar código al archivo *DatasetName. DataSet. Designer* ). Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, vea [partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

El código que define un TableAdapter se genera cada vez que se realizan cambios en el TableAdapter del conjunto de DataSet. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de TableAdapter. Para evitar que se elimine el código durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial de TableAdapter.

De forma predeterminada, después de separar el código de conjunto de datos y TableAdapter, el resultado es un archivo de clase discreto en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName. Designer. VB* (o *DatasetName.Designer.CS* ) que contiene el código de TableAdapter. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado *DatasetName. DataSet. Designer. vb* (o *DatasetName.DataSet.Designer.CS* ) que contiene el código del conjunto de archivos.

> [!NOTE]
> Cuando los conjuntos de datos se separan de los TableAdapters (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente. Las clases de conjunto de tipos parciales existentes deben moverse manualmente al proyecto de conjunto de DataSet.

> [!NOTE]
> El DataSet proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> controladores de eventos y cuando se necesita validación. Para obtener más información, vea [agregar validación a un conjunto de datos de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para agregar código de usuario a un TableAdapter en una aplicación de n niveles

1. Busque el proyecto que contiene el archivo *. xsd* .

2. Haga doble clic en el archivo *. xsd* para abrir el **Diseñador de DataSet**.

3. Haga clic con el botón secundario en el TableAdapter al que desea agregar código y, a continuación, seleccione **Ver código**.

     Se crea una clase parcial y se abre en el editor de código.

4. Agregue código dentro de la declaración de clase parcial.

5. En el ejemplo siguiente se muestra dónde agregar código a `CustomersTableAdapter` en `NorthwindDataSet` :

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

## <a name="see-also"></a>Consulte también

- [Información general sobre las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)
- [Agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Crear y configurar TableAdapters](create-and-configure-tableadapters.md)
- [Información general sobre la actualización jerárquica](hierarchical-update.md)
