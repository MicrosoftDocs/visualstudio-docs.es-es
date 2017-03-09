---
title: "C&#243;mo: Agregar c&#243;digo a conjuntos de datos en aplicaciones con n niveles | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "aplicaciones con n capas, extender conjuntos de datos"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Agregar c&#243;digo a conjuntos de datos en aplicaciones con n niveles
Puede extender la funcionalidad de un conjunto de datos creando un archivo de clase parcial para el conjunto de datos y agregándole código \(en lugar de agregar código al archivo *DatasetName*DataSet.Designer\).  \(Las clases parciales habilitan al código para que una clase concreta se divida entre varios archivos físicos.  Para obtener más información, vea [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).\)  
  
 Se genera el código que define un conjunto de datos vez que se realizan cambios en la definición del conjunto de datos \(en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)\).  Este código también se genera cuando se realizan cambios durante el funcionamiento de cualquier asistente que modifica la configuración de un conjunto de datos.  Para evitar que el código se elimine durante la regeneración de un conjunto de datos, agregue el código al archivo de clase parcial del conjunto de datos.  
  
 De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto.  El proyecto original tiene un archivo que se denomina *DatasetName*.Designer.vb \(o *DatasetName*.Designer.cs\) que contiene el código de `TableAdapter`.  El proyecto designado en la propiedad **DataSet Project** tiene un archivo que se denomina *DatasetName*.DataSet.Designer.vb \(o *DatasetName*.DataSet.Designer.cs\) que contiene el código del conjunto de datos.  
  
> [!NOTE]
>  Cuando se separan conjuntos de datos y `TableAdapter`s \(estableciendo la propiedad **DataSet Project**\), las clases de conjunto de datos parciales existentes en el proyecto no se trasladarán automáticamente.  Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
>  El [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) también proporciona la funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y los controladores de eventos <xref:System.Data.DataTable.RowChanging> cuando se debería agregar el código de validación.  Para obtener más información, vea [Cómo: Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### Para agregar código a conjuntos de datos en aplicaciones con n niveles  
  
1.  Busque el proyecto que contiene el archivo .xsd \(el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Haga doble clic en el archivo **.xsd** para abrir el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Haga clic con el botón secundario en la tabla de datos a la que desea agregar el código \(el nombre de tabla en la barra de título\) y haga clic en **Ver código**.  
  
     Se crea una clase parcial y se abre en el Editor de código.  
  
4.  Agregue el código dentro de la declaración de clase parcial.  
  
     En el ejemplo siguiente se muestra dónde agregar el código a CustomersDataTable en el NorthwindDataSet:  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## Vea también  
 [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)   
 [Cómo: Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md)   
 [Crear aplicaciones de datos](../data-tools/creating-data-applications.md)   
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)