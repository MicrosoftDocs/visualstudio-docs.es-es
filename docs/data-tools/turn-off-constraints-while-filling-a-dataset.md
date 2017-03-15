---
title: "C&#243;mo: Desactivar restricciones al llenar un conjunto de datos | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.BeginEdit"
  - "DataRow.EndEdit"
  - "DataRow.CancelEdit"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "restricciones [Visual Basic], conjuntos de datos"
  - "restricciones [Visual Basic], suspender durante la actualización de conjuntos de datos"
  - "conjuntos de datos [Visual Basic], restricciones"
  - "actualizar conjuntos de datos, restricciones"
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Desactivar restricciones al llenar un conjunto de datos
Si un conjunto de datos contiene restricciones \(como una restricción FOREIGN KEY\), es posible que se produzcan excepciones dependiendo del orden de las operaciones realizadas en el conjunto de datos.  Por ejemplo, cargar registros secundarios antes de cargar los registros principales relacionados puede ser una infracción de la restricción y producir una excepción.  Tan pronto como se carga un registro secundario, la restricción comprueba el registro principal existente y produce un error.  Si no hubiera ningún mecanismo para permitir la suspensión temporal de la restricción, se produciría un error cada vez que se intentara cargar un registro en la tabla secundaria.  Otra manera de suspender todas las restricciones de un conjunto de datos es mediante las propiedades <xref:System.Data.DataRow.BeginEdit%2A> y <xref:System.Data.DataRow.EndEdit%2A>.  
  
> [!NOTE]
>  Cuando las restricciones están desactivadas, no se producen eventos de validación \(por ejemplo, <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, y así sucesivamente\).  
  
### Para suspender las restricciones de actualización mediante programación  
  
-   En el ejemplo siguiente se muestra cómo desactivar temporalmente la comprobación de restricciones de un conjunto de datos:  
  
     [!code-cs[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### Para suspender las restricciones de actualización mediante el Diseñador de DataSet  
  
1.  Abra el conjunto de datos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Establezca la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> en `false` en la ventana **Propiedades**.  
  
## Vea también  
 [Guardar los datos en conjuntos de datos](../data-tools/save-data-back-to-the-database.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)