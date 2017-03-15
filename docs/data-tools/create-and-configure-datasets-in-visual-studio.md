---
title: "C&#243;mo: Crear un conjunto de datos con tipo | Microsoft Docs"
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
  - "conjuntos de datos [Visual Basic], crear"
  - "conjuntos de datos con tipo, crear"
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 36
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear un conjunto de datos con tipo
Se crea un <xref:System.Data.DataSet> con tipo mediante el **Asistente para la configuración de orígenes de datos** o el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
> [!NOTE]
>  Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [Crear un DataSet](../Topic/Creating%20a%20DataSet.md).  
  
## Para crear conjuntos de datos con tipo con el Asistente para configuración de orígenes de datos o con el Diseñador de DataSet  
  
#### Para crear un conjunto de datos con el Asistente para la configuración de orígenes de datos  
  
1.  En el menú **Datos**, haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para la configuración de orígenes de datos**.  
  
2.  Seleccione **Base de datos** en la página **Elegir un tipo de origen de datos**.  
  
3.  Finalice el asistente y se agrega un conjunto de datos con tipo al proyecto.  Para obtener más información, vea [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
#### Para crear un conjunto de datos con el Diseñador de Dataset  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  Seleccione **DataSet** en el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  Escriba un nombre para el conjunto de datos.  
  
4.  Haga clic en **Agregar**.  
  
     El conjunto de datos se agrega al proyecto y se abre en el **Diseñador de DataSet**.  
  
5.  Arrastre los elementos desde la ficha **DataSet** del **Cuadro de herramientas** al diseñador.  Para obtener más información, vea [Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
     O bien  
  
     Arrastre elementos desde una conexión activa del **Explorador de servidores** o **Explorador de bases de datos** hasta el **Diseñador de DataSet**.  
  
## Vea también  
 [Tutorial: Conectar a los datos en una base de datos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)   
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)