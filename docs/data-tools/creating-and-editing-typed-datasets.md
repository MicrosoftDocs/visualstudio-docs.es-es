---
title: "Crear y editar conjuntos de datos con tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], Diseñador de DataSet"
  - "Diseñador de DataSet"
  - "conjuntos de datos [Visual Basic], diseñador visual"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Crear y editar conjuntos de datos con tipo
El **Diseñador de DataSet** es un conjunto de herramientas visuales que se pueden utilizar para crear y editar conjuntos de datos con tipo y los elementos individuales que contienen.  
  
 El **Diseñador de DataSet** proporciona las representaciones visuales de los objetos contenidos en conjuntos de datos con tipo.  Con el **Diseñador de DataSet** puede crear y modificar [TableAdapters](../data-tools/tableadapter-overview.md), [consultas de TableAdapters](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s y <xref:System.Data.DataRelation>s.  
  
 Para abrir el **Diseñador de DataSet**, haga doble clic en un conjunto de datos en el **Explorador de soluciones**, o bien, haga clic con el botón secundario del mouse en el conjunto de datos en la ventana **Orígenes de datos** y haga clic en **Editar DataSet con el Diseñador**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  Al agregar un nuevo elemento <xref:System.Data.DataSet> con el cuadro de diálogo **Agregar nuevo elemento**, se abrirá el **Diseñador de DataSet** con un conjunto de datos vacío listo para editar.  
  
> [!NOTE]
>  El **Diseñador de DataSet** se puede utilizar para extender la funcionalidad de un conjunto de datos.  Haga doble clic en la superficie de diseño o haga clic con el botón secundario del mouse y elija **Ver código** para crear un archivo de clase parcial en el que puede agregar código al conjunto de datos que no modificará ni eliminará el diseñador.  Para obtener información sobre cómo extender la funcionalidad de un objeto TableAdapter, vea [Cómo: Extender la funcionalidad de un TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 La tabla siguiente muestra las tareas comunes que puede realizar con el **Diseñador de DataSet**.  
  
|Para|Vea|  
|----------|---------|  
|Crear un TableAdapter|[Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Editar un TableAdapter|[Cómo: Editar TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|Crear una consulta de TableAdapter|[Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Editar una consulta de TableAdapter|[Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Cree un control <xref:System.Data.DataTable>|[Cómo: Crear tablas de datos](../data-tools/how-to-create-data-tables.md)|  
|Editar un control <xref:System.Data.DataTable>|[Diseñar DataTables](../data-tools/designing-datatables.md)|  
|Cree un control <xref:System.Data.DataColumn>|[Cómo: Agregar columnas a un DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|Crear una relación entre dos controles <xref:System.Data.DataTable>|[Cómo: Crear DataRelations con el Diseñador de Dataset](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|Extender la funcionalidad del conjunto de datos|[Cómo: Extender la funcionalidad de un conjunto de datos](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|Agregar la validación al evento <xref:System.Data.DataTable.ColumnChanging> de una tabla de datos|[Cómo: Validar datos mientras se modifica una columna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|Agregar la validación al evento <xref:System.Data.DataTable.RowChanging> de una tabla de datos|[Cómo: Validar datos mientras se modifica la fila](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## Crear objetos en la superficie de diseño  
 Puede crear los conjuntos de datos agregando y editando los objetos individuales que constituyen un conjunto de datos.  La tabla siguiente proporciona una explicación de los distintos objetos de la ficha **DataSet** del **Cuadro de herramientas** que se pueden arrastrar hasta la superficie de diseño:  
  
|Objeto|Descripción|  
|------------|-----------------|  
|TableAdapter|Contiene una colección de comandos de datos y una conexión de datos que se utilizan para comunicar con la base de datos subyacente y rellenar una tabla de datos.  Para obtener más información, vea [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md) y [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Consulta|Las consultas de TableAdapter son métodos fuertemente tipados que ejecutan instrucciones SQL y procedimientos almacenados.  Al ejecutar una consulta de TableAdapter se rellenan una tabla de datos con datos o se llevan a cabo otras tareas de base de datos.  Para obtener más información, vea [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  Al arrastrar una columna hasta una tabla se agrega la columna a esa tabla, mientras que, arrastrando una consulta hasta un área vacía del **Diseñador de Dataset**, se crea una consulta global.  Para obtener más información, vea [Cómo: Agregar consultas globales a un conjunto de datos](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Representa una colección en memoria de las filas devueltas de una base de datos.|  
|Relación \(<xref:System.Data.DataRelation>\)|Representa una relación primaria\-\-secundaria entre dos objetos <xref:System.Data.DataTable>.  Para obtener más información, vea [Introducción a los objetos DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md) y [Tutorial: Crear una relación entre tablas de datos](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md).|  
  
> [!NOTE]
>  El **Diseñador de DataSet** se conecta a una base de datos subyacente únicamente cuando se crea un conjunto de datos; el diseñador no detecta automáticamente los cambios posteriores en la base de datos.  Para actualizar un archivo .xsd existente, vuelva a ejecutar el **Asistente para configuración**.  Si las relaciones de tabla han cambiado, quite y vuelva a agregar las tablas correspondientes a los .xsd.  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] habilita [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sobre los datos en un objeto <xref:System.Data.DataSet>.  Para obtener más información, vea [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Vea también  
 [Tutorial: Crear un conjunto de datos con el Diseñador de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Tutorial: Crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Tutorial: Crear un DataTable en el Diseñador de Dataset](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Tutorial: Crear una relación entre tablas de datos](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)