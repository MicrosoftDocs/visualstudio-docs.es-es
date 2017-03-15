---
title: "C&#243;mo: Agregar c&#243;digo a TableAdapters en aplicaciones con n niveles | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "aplicaciones con n capas, extender TableAdapters"
  - "TableAdapters, aplicaciones con n capas"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Agregar c&#243;digo a TableAdapters en aplicaciones con n niveles
Puede extender la funcionalidad de `TableAdapter` creando un archivo de clase parcial para `TableAdapter` y agregándole el código \(en lugar de agregar el código al archivo *DatasetName*.DataSet.Designer\).  \(Las clases parciales habilitan al código para que una clase concreta se divida entre varios archivos físicos.  Para obtener más información, vea [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial \(Tipos\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
 Se genera el código que define `TableAdapter` cada vez que se realiza un cambio en `TableAdapter` \(en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)\).  Este código también se genera cuando se realizan cambios durante el funcionamiento de cualquier asistente que modifica la configuración de `TableAdapter`.  Para evitar que el código se elimine durante la regeneración de `TableAdapter`, agregue código al archivo de clase parcial de `TableAdapter`.  
  
 De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto.  El proyecto original tiene un archivo que se denomina *DatasetName*.Designer.vb \(o *DatasetName*.Designer.cs\) que contiene el código de `TableAdapter`.  El proyecto designado en la propiedad **DataSet Project** tiene un archivo que se denomina *DatasetName*.DataSet.Designer.vb \(o *DatasetName*.DataSet.Designer.cs\) que contiene el código del conjunto de datos.  
  
> [!NOTE]
>  Cuando se separan conjuntos de datos y `TableAdapter`s \(estableciendo la propiedad **DataSet Project**\), las clases de conjunto de datos parciales existentes en el proyecto no se trasladarán automáticamente.  Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
>  El [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) también proporciona la funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y los controladores de eventos <xref:System.Data.DataTable.RowChanging> cuando se debería agregar el código de validación.  Para obtener más información, vea [Cómo: Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para agregar el código de usuario a TableAdapter en una aplicación con n niveles  
  
1.  Busque el proyecto que contiene el archivo .xsd \(el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Haga doble clic en el archivo **.xsd** para abrir el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Haga clic con el botón secundario en el `TableAdapter` que desea agregar el código a y haga clic en **Ver código**.  
  
     Se crea una clase parcial y se abre en el Editor de código.  
  
4.  Agregue el código dentro de la declaración de clase parcial.  
  
5.  En el ejemplo siguiente se muestra donde agregar código a `CustomersTableAdapter` en `NorthwindDataSet`:  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## Vea también  
 [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)   
 [Cómo: Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md)   
 [Crear aplicaciones de datos](../data-tools/creating-data-applications.md)