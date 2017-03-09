---
title: "C&#243;mo: Confirmar cambios en un conjunto de datos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conjuntos de datos [Visual Basic], confirmar cambios"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Confirmar cambios en un conjunto de datos
Mientras se están realizando cambios en un conjunto de datos mediante la actualización, inserción y eliminación de registros, el conjunto de datos mantiene las versiones original y actual de los registros.  Además, se realiza el seguimiento de la propiedad <xref:System.Data.DataRow.RowState%2A> de cada fila para indicar si los registros están en su estado original o si se han actualizado, insertado o eliminado.  Esta información es útil cuando se necesita encontrar una versión concreta de una fila.  Lo normal es obtener un subconjunto de registros modificados para enviarlo a otro proceso.  Para obtener más información, vea [Cómo: Recuperar filas modificadas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  Después de procesar todas las filas modificadas, puede confirmar los cambios llamando al método `AcceptChanges` de <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o <xref:System.Data.DataRow>.  Se llama al método `AcceptChanges` de forma automática al llamar a los métodos de actualización de un [TableAdapter](../data-tools/tableadapter-overview.md) o adaptador de datos.  Llame a `AcceptChanges` después de enviar los cambios a una base de datos.  
  
 Al llamar a <xref:System.Data.DataSet.AcceptChanges%2A> del <xref:System.Data.DataSet>, cualquier objeto <xref:System.Data.DataRow> que aún esté en el modo de edición finaliza correctamente el proceso de edición.  La propiedad <xref:System.Data.DataRow.RowState%2A> de cada <xref:System.Data.DataRow> también cambia; las filas <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState> se convierten en <xref:System.Data.DataRowState>, y se quitan las filas <xref:System.Data.DataRowState>.  
  
 Si <xref:System.Data.DataSet> contiene objetos <xref:System.Data.ForeignKeyConstraint>, si se invoca el método <xref:System.Data.DataSet.AcceptChanges%2A>, también se fuerza <xref:System.Data.AcceptRejectRule>.  
  
### Para confirmar los cambios en un conjunto de datos  
  
-   Llame al método `AcceptChanges` en un <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o <xref:System.Data.DataRow> para confirmar los cambios en aquellos objetos.  
  
     En el ejemplo siguiente, se muestra cómo llamar al método `AcceptChanges` para confirmar los cambios de la tabla `Customers` después de actualizar un origen de datos:  
  
     [!code-cs[VbRaddataEditing#11](../data-tools/codesnippet/CSharp/how-to-commit-changes-in-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#11](../data-tools/codesnippet/VisualBasic/how-to-commit-changes-in-a-dataset_1.vb)]  
  
## Vea también  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Guardar datos](../data-tools/saving-data.md)   
 [Cómo: Recuperar filas modificadas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)