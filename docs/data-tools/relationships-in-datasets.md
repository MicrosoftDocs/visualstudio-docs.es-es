---
title: "Relaciones en conjuntos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conjuntos de datos [Visual Basic], relaciones"
  - "relaciones, acera de relaciones"
  - "relaciones, conjuntos de datos"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relaciones en conjuntos de datos
Un conjunto de datos puede contener tablas relacionadas como una base de datos relacional.  El objeto que facilita una relación entre las tablas de datos es un objeto **DataRelation**.  Los temas siguientes proporcionan información sobre los objetos **DataRelation** de ADO.NET, cómo se crean y cómo se utilizan para trabajar con datos en tablas relacionadas.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## En esta sección  
 [Introducción a los objetos DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 Proporciona información general sobre el modo en que los conjuntos de datos permiten especificar relaciones entre tablas y cómo se pueden aprovechar estas relaciones.  
  
 [Cómo: Crear DataRelations con el Diseñador de Dataset](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 Explica cómo se utiliza el **Diseñador de Dataset** para agregar un objeto <xref:System.Data.DataRelation> a un conjunto de datos.  
  
 [Cómo: Obtener acceso a registros en tablas de datos relacionadas](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 Explica cómo devolver mediante programación los registros relacionados de un conjunto de datos con tipo con tablas en una relación uno a varios.  
  
 [Tutorial: Crear una relación entre tablas de datos](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 Proporciona instrucciones paso a paso para crear dos tablas de datos con el **Diseñador de Dataset** y agregar una relación entre ellas.  
  
## Referencia  
 <xref:System.Data.DataRelation>  
 Representa una relación primaria\/secundaria entre dos objetos T:System.Data.DataTable.  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 Obtiene las filas secundarias de un objeto T:System.Data.DataRow.  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 Obtiene las filas primarias de un objeto T:System.Data.DataRow.  
  
 <xref:System.Data.Rule>  
 Indica la acción que se produce cuando se fuerza <xref:System.Data.ForeignKeyConstraint>.  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 Obtiene o establece un valor que indica si los valores de cada fila de la columna deben ser únicos.  
  
 <xref:System.Data.Constraint>  
 Representa una restricción que se puede forzar en uno o más objetos <xref:System.Data.DataColumn>.  
  
## Secciones relacionadas  
 [Agregar DataRelations](../Topic/Adding%20DataRelations.md)  
 Describe cómo se crean relaciones entre tablas en un <xref:System.Data.DataSet>.  
  
 [Navegar por DataRelations](../Topic/Navigating%20DataRelations.md)  
 Describe cómo se utilizan las relaciones entre tablas en un <xref:System.Data.DataSet> para devolver las filas secundarias o primarias de una relación primaria\-secundaria.  
  
 [Anidar DataRelations](../Topic/Nesting%20DataRelations.md)  
 Explica la importancia de los objetos <xref:System.Data.DataRelation> anidados al representar el contenido de un <xref:System.Data.DataSet> como datos XML y describe cómo crearlos.