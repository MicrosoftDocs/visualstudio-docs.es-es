---
title: "Trabajar con conjuntos de datos en aplicaciones de n capas | Microsoft Docs"
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
  - "datos [Visual Basic], aplicaciones con n capas"
  - "proyectos DataSet [frente a aplicaciones de datos con n capas]"
  - "conjuntos de datos [Visual Basic], aplicaciones con n capas"
  - "aplicaciones distribuidas [frente a aplicaciones de datos con n capas]"
  - "aplicaciones de varias capas"
  - "aplicaciones de base de datos de varias capas"
  - "aplicaciones con n capas"
  - "TableAdapters, aplicaciones con n capas"
  - "capas, aplicaciones con n capas"
  - "conjuntos de datos con tipo, aplicaciones con n capas"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trabajar con conjuntos de datos en aplicaciones de n capas
Las *aplicaciones de datos con n niveles* son aplicaciones centradas en datos que están separadas en varias capas lógicas \(o *niveles*\).  Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto.  Para obtener más información, vea [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md).  
  
 Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos.  Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.  
  
 La compatibilidad con n niveles en conjuntos de datos con tipo permite el desarrollo iterativo de la arquitectura de la aplicación en un diseño con n niveles, al tiempo que acaba con la necesidad de separar el código en más de un proyecto manualmente.  Empiece a diseñar la capa de datos mediante el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  Cuando esté listo para llevar la arquitectura de la aplicación a un diseño con n niveles, establezca la propiedad **DataSet Project** de un conjunto de datos de forma que la clase del conjunto de datos se genere en un proyecto por separado.  
  
## En esta sección  
 [Cómo: Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Se explica cómo sacar la clase de conjunto de datos generada del proyecto que contiene las clases TableAdapter generadas y colocarla en un nuevo proyecto.  
  
 [Cómo: Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Se explica cómo generar una clase parcial en la que se puede agregar código relativo a un TableAdapter con n niveles.  
  
 [Cómo: Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Se explica cómo generar una clase parcial en la que se puede agregar código relativo a un conjunto de datos con n niveles.  
  
 [Cómo: Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Se indica dónde agregar código con el que validar datos que cambian.  
  
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Contiene instrucciones paso a paso para crear un conjunto de datos con tipo y separar el código de TableAdapter y del conjunto de datos en varios proyectos.  
  
 [Tutorial: Agregar validación a una aplicación de datos con n niveles](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 Contiene instrucciones paso a paso para agregar validación a una aplicación creada en la aplicación de datos de n niveles.  
  
## Referencia  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## Secciones relacionadas  
 [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)  
  
 [Actualización jerárquica](../data-tools/hierarchical-update.md)  
  
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [Aplicaciones remotas y de n niveles con LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)