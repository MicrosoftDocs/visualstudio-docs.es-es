---
title: "No se declar&#243; &#39;&lt;nullconstant&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se declar&#243; &#39;&lt;nullconstant&gt;&#39;
No se declaró '\<nullconstant\>'. Ya no se admite la constante 'Null' de la base de datos; use System.DBNull en su lugar.  
  
 Una instrucción usa la palabra clave `Null`, que ya no se admite en Visual Basic.  
  
 **Identificador de error:** BC30822  
  
### Para corregir este error  
  
1.  Use <xref:System.DBNull> en lugar de `Null`. En el siguiente ejemplo se muestra cómo hacerlo.  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  Use la palabra clave [Nothing](/dotnet/visual-basic/language-reference/nothing) para las asignaciones y comparaciones al usar variables de objeto. En el siguiente ejemplo se muestra cómo hacerlo.  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## Vea también  
 <xref:System.DBNull>   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/es-es/0483590a-6309-449c-a2fa-effa26a03b95)