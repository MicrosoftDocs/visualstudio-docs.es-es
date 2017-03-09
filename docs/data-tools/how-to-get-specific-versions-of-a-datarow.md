---
title: "C&#243;mo: Obtener versiones espec&#237;ficas de una fila de datos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "DataRow (objeto)"
  - "estados de fila"
  - "actualizar conjuntos de datos, estados de fila"
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Obtener versiones espec&#237;ficas de una fila de datos
Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original \(<xref:System.Data.DataRowVersion>\) como las versiones nuevas \(<xref:System.Data.DataRowVersion>\) de la fila.  Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro \(según se defina en la enumeración <xref:System.Data.DataRowVersion>\) y procesar los cambios según corresponda.  
  
> [!NOTE]
>  Las versiones diferentes de una fila sólo existen después de que ésta haya sido revisada y antes de haber llamado al método `AcceptChanges`.  Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.  
  
 Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna \(o el nombre de la columna como cadena\), se devuelve el valor de la versión de fila concreta de esa columna.  La columna modificada se identifica durante los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged>, por lo que es un buen momento para examinar las versiones de fila que difieran con fines de validación.  Sin embargo, si ha suspendido las restricciones temporalmente, esos eventos no se provocarán y deberá identificar mediante programación qué columnas han cambiado.  Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.  
  
## Tener acceso a la versión original de un objeto DataRow  
  
#### Para obtener la versión original de un registro  
  
-   Obtenga acceso al valor de una columna que se pasa en <xref:System.Data.DataRowVersion> de la fila que desea devolver.  
  
     El ejemplo siguiente muestra cómo puede utilizar un valor <xref:System.Data.DataRowVersion> para obtener el valor original de un campo `CompanyName` en un objeto <xref:System.Data.DataRow>:  
  
     [!code-cs[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/how-to-get-specific-versions-of-a-datarow_1.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/how-to-get-specific-versions-of-a-datarow_1.vb)]  
  
## Tener acceso a la versión actual de un objeto DataRow  
  
#### Para obtener la versión actual de un registro  
  
-   Obtenga acceso al valor de una columna y agregue un parámetro al índice donde se indique qué versión de una fila desea que se devuelva.  
  
     El ejemplo siguiente muestra cómo puede utilizar un valor <xref:System.Data.DataRowVersion> para obtener el valor actual de un campo `CompanyName` en un objeto <xref:System.Data.DataRow>:  
  
     [!code-cs[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/how-to-get-specific-versions-of-a-datarow_2.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/how-to-get-specific-versions-of-a-datarow_2.vb)]  
  
## Vea también  
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)