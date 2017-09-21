---
title: "Tutorial: Crear un DataTable en el Dise&#241;ador de Dataset | Microsoft Docs"
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
  - "datos [Visual Studio], Diseñador de DataSet"
  - "Diseñador de DataSet, crear tablas de datos"
  - "objetos DataTable, crear"
  - "tablas [Visual Studio], crear"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Crear un DataTable en el Dise&#241;ador de Dataset
Este tutorial explica cómo crear un control <xref:System.Data.DataTable> \(sin un TableAdapter\) mediante el **Diseñador de DataSet**.  Para obtener información sobre cómo crear tablas de datos que incluyen objetos TableAdapter, vea [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto de aplicación para Windows  
  
-   Agregar un nuevo conjunto de datos a la aplicación  
  
-   Agregar una nueva tabla de datos al conjunto de datos  
  
-   Agregar las columnas a la tabla de datos  
  
-   Establecer la clave principal de la tabla  
  
## Crear una nueva aplicación para Windows  
  
#### Para crear un proyecto de aplicación para Windows nuevo  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Elija un lenguaje de programación en el panel **Tipos de proyecto**.  
  
3.  Haga clic en **Aplicación para Windows** en el panel **Plantillas**.  
  
4.  Denomine al proyecto `DataTableWalkthrough` y, a continuación, haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto al **Explorador de soluciones** y muestra **Form1** en el diseñador.  
  
## Agregar un nuevo conjunto de datos a la aplicación  
  
#### Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
     Aparecerá el cuadro de diálogo Agregar nuevo elemento.  
  
2.  En el cuadro **Plantillas**, seleccione **DataSet**.  
  
3.  Haga clic en **Agregar**.  
  
     Visual Studio agregará un archivo denominado **DataSet1.xsd** al proyecto y lo abrirá en el **Diseñador de DataSet**.  
  
## Agregar una nueva DataTable al conjunto de datos  
  
#### Para agregar una nueva tabla de datos al conjunto de datos  
  
1.  Arrastre **DataTable** desde la ficha **DataSet** del **Cuadro de herramientas** al **Diseñador de DataSet**.  
  
     Una tabla denominada **DataTable1** se agrega al conjunto de datos.  
  
    > [!NOTE]
    >  Para crear una tabla de datos que incluya un TableAdapter, vea [Tutorial: Crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Haga clic en la barra de título de **DataTable1** y cámbiele el nombre a `Música`.  
  
## Agregar columnas a la tabla de datos  
  
#### Para agregar las columnas a la tabla de datos  
  
1.  Haga clic con el botón secundario del mouse en la tabla **Música**.  Señale **Agregar** y, a continuación, haga clic en **Columna**.  
  
2.  Denomine la columna `IdCanción`.  
  
3.  En la ventana **Propiedades**, establezca la propiedad <xref:System.Data.DataColumn.DataType%2A> en <xref:System.Int16?displayProperty=fullName>.  
  
4.  Repita este proceso y agregue las columnas siguientes:  
  
     `Título`: <xref:System.String?displayProperty=fullName>  
  
     `Intérprete`: <xref:System.String?displayProperty=fullName>  
  
     `Género`: <xref:System.String?displayProperty=fullName>  
  
## Establecer la clave principal de la tabla  
 Todas las tablas de datos deben tener una clave principal.  Una clave principal identifica de manera única un registro específico en una tabla de datos.  
  
#### Para establecer la clave principal de la tabla de datos  
  
-   Haga clic con el botón secundario en la columna **IdCanción** y, a continuación, haga clic en **Establecer clave principal**.  
  
     Aparece un icono de clave junto a la columna **IdCanción**.  
  
## Guardar el proyecto  
  
#### Para guardar el proyecto DataTableWalkthrough  
  
-   En el menú **Archivo**, haga clic en **Guardar todo**.  
  
## Pasos siguientes  
 Ahora que ha creado la tabla, puede realizar una las acciones siguientes:  
  
|Para|Vea|  
|----------|---------|  
|Crear un formulario para introducir datos|[Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Agregar datos a la tabla|[Agregar datos a DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|Ver datos en una tabla|[Ver datos en DataTable](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|Editar datos|[Editar DataTable](../Topic/DataTable%20Edits.md)|  
|Eliminar una fila de una tabla|[Eliminar DataRow](../Topic/DataRow%20Deletion.md)|  
  
## Vea también  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)