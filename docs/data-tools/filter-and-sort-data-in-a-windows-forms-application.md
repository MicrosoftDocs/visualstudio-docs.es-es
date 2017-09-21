---
title: "C&#243;mo: Filtrar y ordenar los datos en una aplicaci&#243;n Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "vistas de datos, filtrar"
  - "vistas de datos, ordenar"
  - "filtrado de conjuntos de datos, mediante vistas de datos"
  - "estados de fila"
  - "estados de fila, filtrar"
  - "versión de fila, filtrar"
  - "ordenar conjuntos de datos, mediante vistas de datos"
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Filtrar y ordenar los datos en una aplicaci&#243;n Windows Forms
Los datos se filtran estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en una expresión de cadena que devuelve los registros deseados.  
  
 Puede ordenar los datos estableciendo la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en el nombre de columna por la que desea ordenar; anexe `DESC` para realizar la ordenación en sentido descendente, o bien, `ASC` para hacerlo en sentido ascendente.  
  
> [!NOTE]
>  Si su aplicación no utiliza componentes <xref:System.Windows.Forms.BindingSource>, puede puede filtrar y ordenar los datos mediante objetos <xref:System.Data.DataView>.  Para obtener más información, vea [DataViews](../Topic/DataViews.md).  
  
### Para filtrar datos mediante un componente BindingSource  
  
-   Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Filter%2A> en la expresión que desea devolver.  Por ejemplo, el código siguiente devuelve los clientes cuyo valor de `CompanyName` empieza por "B":  
  
     [!code-cs[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
### Para ordenar los datos mediante un componente BindingSource  
  
-   Establezca la propiedad <xref:System.Windows.Forms.BindingSource.Sort%2A> en la columna por la que desea ordenar.  Por ejemplo, el código siguiente ordena los clientes por la columna `CompanyName` en orden descendente:  
  
     [!code-cs[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)