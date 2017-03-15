---
title: "Tutorial: Crear un conjunto de datos con el Dise&#241;ador de Dataset | Microsoft Docs"
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
  - "datos [Visual Studio], Diseñador de DataSet"
  - "Diseñador de DataSet, tutoriales"
  - "conjuntos de datos [Visual Basic], crear"
  - "conjuntos de datos [Visual Basic], tutoriales"
  - "esquemas XML, crear conjuntos de datos"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Crear un conjunto de datos con el Dise&#241;ador de Dataset
En este tutorial creará un conjunto de datos mediante el **Diseñador de DataSet**.  Éste lo guiará a través del proceso de crear un proyecto nuevo y agregar un nuevo elemento **DataSet** a él.  Obtendrá información sobre cómo crear tablas de acuerdo con una base de datos sin utilizar un asistente.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto de **Aplicación para Windows**.  
  
-   Agregar un elemento de **Conjunto de datos** vacío al proyecto.  
  
-   Crear y configurar un origen de datos de la aplicación para generar conjuntos de datos con el **Diseñador de DataSet**.  
  
-   Crear una conexión a la base de datos Northwind en el **Explorador de servidores**.  
  
-   Crear tablas con TableAdapters del conjunto de datos basadas en tablas de la base de datos.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind \(versión de SQL Server o Access\).  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear un nuevo proyecto de aplicación para Windows  
  
#### Para crear un proyecto de aplicación para Windows nuevo  
  
1.  Desde el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Elija un lenguaje de programación en el panel **Tipos de proyecto**.  
  
3.  Haga clic en **Aplicación para Windows** en el panel **Plantillas**.  
  
4.  Denomine el proyecto `DatasetDesignerWalkthrough` y, a continuación, haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agregará el proyecto al **Explorador de soluciones** y mostrará un nuevo formulario en el diseñador.  
  
## Agregar un nuevo conjunto de datos a la aplicación  
  
#### Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.  
  
2.  En el cuadro **Plantillas** del cuadro de diálogo **Agregar nuevo elemento**, haga clic en **DataSet**.  
  
3.  Asigne al conjunto de datos el nombre `NorthwindDataset` y, a continuación, haga clic en **Agregar**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agregará un archivo denominado **NorthwindDataset.xsd** al proyecto y lo abrirá en el **Diseñador de DataSet**.  
  
## Crear una conexión de datos en el Explorador de servidores  
  
#### Para crear una conexión a la base de datos Northwind  
  
1.  En el menú **Ver**, haga clic en el **Explorador de servidores**.  
  
2.  En el **Explorador de servidores**, haga clic en el botón **Conectar con base de datos**.  
  
3.  Crear una conexión a la base de datos de ejemplo Northwind.  
  
    > [!NOTE]
    >  Puede conectar a la versión SQL Server o Access de Northwind para este tutorial.  
  
## Crear las tablas del conjunto de datos  
 En esta sección se explicará cómo agregar tablas al conjunto de datos.  
  
#### Para crear la tabla Customers  
  
1.  Expanda la conexión de datos que creó en el **Explorador de servidores** y, a continuación, expanda el nodo **Tablas**.  
  
2.  Arrastre la tabla **Customers** desde el **Explorador de servidores** al **Diseñador de DataSet**.  
  
     Se agregan una tabla de datos **Customers** y **CustomersTableAdapter** al conjunto de datos.  
  
#### Para crear la tabla Orders  
  
-   Arrastre la tabla **Orders** desde el **Explorador de servidores** al **Diseñador de DataSet**.  
  
     Una tabla de datos **Orders**, **OrdersTableAdapter** y una relación de datos entre las tablas **Customers** y **Orders** se agregan al conjunto de datos.  
  
#### Para crear la tabla OrderDetails  
  
-   Arrastre la tabla **Order Details** desde el **Explorador de servidores** hasta el **Diseñador de DataSet**.  
  
     Se agregan un tabla de datos **Order Details**, un **Order DetailsTableAdapter** y una relación de datos entre las tablas **Orders** y **Order Details** al conjunto de datos.  
  
## Pasos siguientes  
  
### Para agregar funcionalidad a la aplicación  
  
-   Guarde el conjunto de datos.  
  
-   Seleccione elementos en la ventana **Orígenes de datos** y arrástrelos a un formulario.  Para obtener más información, vea [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Agregar más consultas a los TableAdapters.  Para obtener más información, vea [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Agregar lógica de la validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos.  Para obtener más información, vea [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)