---
title: "C&#243;mo: Crear consultas de TableAdapter | Microsoft Docs"
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
  - "datos [Visual Studio], consultas TableAdapter"
  - "consultas [Visual Studio], crear"
  - "consultas [Visual Studio], TableAdapters"
  - "TableAdapters, crear consultas"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Crear consultas de TableAdapter
Las consultas del TableAdapter son instrucciones SQL o procedimientos almacenados que puede ejecutar su aplicación en una base de datos.  
  
 Agregue tantas consultas a un TableAdapter como sea necesario para su aplicación.  Las consultas de TableAdapter aparecen como métodos en un TableAdapter.  Cuando crea que una consulta llamada `FillByCity` que toma un parámetro que representa el valor de ciudad, la consulta se agrega al TableAdapter.  Se agrega como método de tipo y toma como argumento el tipo correcto de parámetro, en este caso una cadena que representa el valor de ciudad.  A la consulta de TableAdapter se la llama exactamente igual que a cualquier método u objeto.  Por ejemplo, el código siguiente ejecuta la consulta `FillByCity` y rellena la tabla `Customers` con todos los clientes con un valor de ciudad de `Seattle`:  
  
 [!code-vb[VbRaddataTableAdapters#1](../data-tools/codesnippet/VisualBasic/how-to-create-tableadapter-queries_1.vb)]
 [!code-cs[VbRaddataTableAdapters#1](../data-tools/codesnippet/CSharp/how-to-create-tableadapter-queries_1.cs)]  
  
 Las consultas de TableAdapter pueden rellenar una tabla de datos \(consultas `Fill` y `FillBy`\) o devolver nuevas tablas de datos rellenadas con los datos devueltos por la consulta \(consultas `GetData` y `GetDataBy`\).  
  
 Puede agregar consultas a TableAdapters existente ejecutando [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md).  \(Haga clic con el botón secundario del mouse en cualquier TableAdapter y elija **Agregar consulta**.\)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Crear una consulta en el Diseñador de DataSet  
  
#### Para agregar una consulta a un TableAdapter en el Diseñador de DataSet  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Haga clic con el botón secundario del mouse en el TableAdapter deseado y seleccione **Agregar consulta**.  
  
     O bien  
  
3.  Arrastre una **Consulta** desde la ficha **DataSet** del **Cuadro de herramientas** hasta una tabla del diseñador.  
  
     El **Asistente para la configuración de consultas de TableAdapter** se abre.  
  
4.  Finalice el asistente; la consulta se agrega al TableAdapter.  
  
## Crear una consulta directamente en un formulario de su aplicación para Windows  
 Si tiene una instancia de un TableAdapter en su formulario, puede agregar una consulta mediante el [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md), que agregue al formulario un control <xref:System.Windows.Forms.ToolStrip> que acepte cualquier parámetro de entrada requerido por la consulta, así como un botón para ejecutar la consulta.  
  
#### Para agregar una consulta a un TableAdapter utilizando el cuadro de diálogo Criterios de búsqueda  
  
1.  Seleccione un TableAdapter en la bandeja de componentes.  
  
2.  Haga clic en la etiqueta inteligente del TableAdapter y elija **Agregar consulta**.  
  
3.  Finalice el cuadro de diálogo y la consulta se agregará al TableAdapter.  Para obtener más información, vea [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Cómo: Explorar datos con el control BindingNavigator de formularios Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Tutorial: Crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)