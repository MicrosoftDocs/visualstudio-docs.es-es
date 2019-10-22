---
title: Agregar código a TableAdapters en aplicaciones de n niveles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673103"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Agregar código a TableAdapters en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender la funcionalidad de un `TableAdapter` creando un archivo de clase parcial para el `TableAdapter` y agregando código a él (en lugar de agregar código al objeto *DatasetName*. Archivo DataSet. Designer). Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, vea [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 El código que define un `TableAdapter` se genera cada vez que se realizan cambios en el `TableAdapter`. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de la `TableAdapter`. Para evitar que se elimine el código durante la regeneración de un `TableAdapter`, agregue código al archivo de clase parcial del `TableAdapter`.

 De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName*. Designer. VB (o *DatasetName*). Designer.cs) que contiene el código `TableAdapter`. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado *DatasetName*. DataSet. Designer. VB (o *DatasetName*. DataSet.Designer.cs) que contiene el código del conjunto de pruebas.

> [!NOTE]
> Cuando se separan conjuntos de propiedades y `TableAdapter`s (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de tipos parciales existentes en el proyecto no se moverán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

> [!NOTE]
> El diseñador de DataSet proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos cuando se necesita validación. Para obtener más información, vea [agregar validación a un conjunto de datos de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para agregar código de usuario a un TableAdapter en una aplicación de n niveles

1. Busque el proyecto que contiene el archivo. xsd (el conjunto de archivos).

2. Haga doble clic en el archivo **. xsd** para abrir el conjunto de archivos.

3. Haga clic con el botón secundario en la `TableAdapter` a la que desea agregar código y, a continuación, seleccione**Ver código**.

     Se crea una clase parcial y se abre en el editor de código.

4. Agregue código dentro de la declaración de clase parcial.

5. En el ejemplo siguiente se muestra dónde agregar código al `CustomersTableAdapter` en el `NorthwindDataSet`:

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
 [Información general sobre aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md) [Agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) información general sobre la [actualización jerárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)