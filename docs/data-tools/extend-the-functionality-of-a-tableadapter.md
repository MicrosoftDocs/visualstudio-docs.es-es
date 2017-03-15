---
title: "C&#243;mo: Extender la funcionalidad de un TableAdapter | Microsoft Docs"
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
  - "datos [Visual Studio], extender TableAdapters"
  - "datos [Visual Studio], TableAdapters"
  - "TableAdapters, agregar funcionalidad"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Extender la funcionalidad de un TableAdapter
Puede extender la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.  
  
 El código que define un objeto TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter \(en el **Diseñador de Dataset**\) o cuando se realizan cambios en la ejecución de cualquier asistente que modifiquen la configuración de un TableAdapter.  Para evitar que su código sea eliminado durante la regeneración de un objeto TableAdapter, agregue código al archivo de clase parcial del TableAdapter.  
  
 \(Las clases parciales permiten que el código para una clase concreta se divida entre varios archivos físicos.  Para obtener más información, vea [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial \(Tipos\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
## Buscar TableAdapters en el código  
 Aunque los objetos TableAdapter se diseñan con el **Diseñador de DataSet**, las clases TableAdapter generadas no se generan como clases anidadas de <xref:System.Data.DataSet>.  Los objetos TableAdapter se buscan en un espacio de nombres basado en el nombre del conjunto de datos asociado del TableAdapter.  Por ejemplo, si su aplicación contiene un conjunto de datos denominado `HRDataSet`, los TableAdapters se buscarían en el espacio de nombres `HRDataSetTableAdapters`.  \(La convención de nomenclatura sigue este patrón: *DatasetName* \+ `TableAdapters`\).  
  
 El ejemplo siguiente supone un TableAdapter denominado `CustomersTableAdapter` en un proyecto con `NorthwindDataSet`.  
  
#### Para crear una clase parcial para un TableAdapter  
  
1.  Agregue una clase nueva al proyecto eligiendo **Agregar clase** en el menú **Proyecto**.  
  
2.  Asigne a la clase el nombre `CustomersTableAdapterExtended`.  
  
3.  Haga clic en **Agregar**.  
  
4.  Reemplace el código con el espacio de nombres y el nombre de clase parcial correspondientes a su proyecto.  Por ejemplo:  
  
     [!code-cs[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: Extender la funcionalidad de un conjunto de datos](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
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