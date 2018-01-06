---
title: "Agregue código a conjuntos de datos en aplicaciones de n niveles | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 775c03583a2fac35f2b62525bf5a18a67f250cef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Agregue código a conjuntos de datos en aplicaciones de n niveles
Puede ampliar la funcionalidad de un conjunto de datos mediante la creación de un archivo de clase parcial para el conjunto de datos y agregar código a él (en lugar de agregar código a la *DatasetName*. Archivo Dataset.Designer). Clases parciales permiten al código para una clase concreta se divida entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
El código que define un conjunto de datos se genera cada vez que se realizan cambios en la definición de conjunto de datos (en el conjunto de datos con tipo). Este código también se genera cuando se realizan cambios durante el funcionamiento de cualquier asistente que modifica la configuración de un conjunto de datos. Para evitar que el código que se eliminen durante la regeneración de un conjunto de datos, agregue código al archivo de clase parcial del conjunto de datos.  
  
De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName*. Designer.vb (o *DatasetName*. Designer.cs) que contiene el código de TableAdapter. El proyecto designado en la **Dataset Project** propiedad tiene un archivo que se denomina *DatasetName*. DataSet.Designer.vb (o *DatasetName*. (DataSet.Designer.cs). Este archivo contiene el código de conjunto de datos.  
  
> [!NOTE]
>  Al separar conjuntos de datos y los TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se traslada automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
>  Cuando es necesario agregar código de validación, el conjunto de datos con tipo proporciona la funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Para agregar código a conjuntos de datos en aplicaciones de n niveles  
  
1.  Localice el proyecto que contiene el archivo .xsd. 
  
2.  Seleccione el **.xsd** archivo para abrir el conjunto de datos.  
  
3.  Haga clic en la tabla de datos a la que desea agregar el código (el nombre de tabla en la barra de título) y, a continuación, seleccione **ver código**.  
  
     Una clase parcial se crea y se abre en el Editor de código.  
  
4.  Agregue el código dentro de la declaración de clase parcial.  
  
     En el ejemplo siguiente se muestra dónde agregar código a CustomersDataTable en el NorthwindDataSet:  
  
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
[Información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)   
[Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Crear y configurar los TableAdapters](create-and-configure-tableadapters.md)  
[Información general de la actualización jerárquica](hierarchical-update.md)     
[Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)