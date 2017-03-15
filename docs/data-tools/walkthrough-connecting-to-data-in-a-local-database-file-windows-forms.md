---
title: "Tutorial: Conectar con los datos de un archivo de base de datos local (Windows Forms) | Microsoft Docs"
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
  - "datos [Visual Studio], conectar con SQL Express"
  - "datos [Visual Studio], locales"
  - "bases de datos, conectar"
  - "datos locales, SQL Express"
  - "SQL Express, conectar"
  - "SQL Express, tutoriales"
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Conectar con los datos de un archivo de base de datos local (Windows Forms)
Puede mostrar rápida y fácilmente los datos de un archivo de base de datos local en la aplicación creando un conjunto de datos y agregando controles enlazados a datos a la aplicación.  En este tutorial, mostrará datos del archivo de base de datos local que creó siguiendo las instrucciones de [Tutorial: Crear un archivo de base de datos local en Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md).  Después de crear un proyecto de Windows Forms, se conectará a dicha base de datos para indicar que desea que los datos de la tabla Clientes aparezcan en una cuadrícula de datos en el formulario para la aplicación.  
  
 Al crear una base de datos en Visual Studio 2013, el motor de SQL Server Express LocalDB se utiliza para tener acceso a un archivo de base de datos \(.mdf\) en SQL Server 2012.  En versiones anteriores de Visual Studio, el motor de SQL Server Express se utiliza para tener acceso a un archivo de base de datos \(.mdf\).  Vea [Información general de datos locales](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
 En este tutorial se incluyen las tareas siguientes:  
  
-   [Crear y configurar un conjunto de datos](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Agregar controles enlazados a datos](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## Requisitos previos  
 Para realizar este tutorial, necesitará acceso a la base de datos SampleDatabase.mdf que puede crear siguiendo las instrucciones de [Tutorial: Crear un archivo de base de datos local en Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Crear y configurar un conjunto de datos  
  
#### Para crear y configurar un conjunto de datos  
  
1.  Cree un proyecto de Windows Forms y denomínelo ConnectLocalData.  
  
     Vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
2.  Si la ventana **Orígenes de datos** no aparece, elija las teclas Mayús\-Alt\-D o, en la barra de menús, elija **Ver**, **Otras ventanas**, **Mostrar orígenes de datos**.  
  
3.  En la ventana **Orígenes de datos**, elija el vínculo **Agregar nuevo origen de datos**.  
  
     En el **Asistente para configuración de orígenes de datos**, elija el botón **Siguiente** dos veces para aceptar la configuración predeterminada.  
  
4.  En la página **Elegir la conexión de datos**, elija el botón **Nueva conexión**.  
  
     Aparecerá el cuadro de diálogo **Elegir origen de datos**.  
  
5.  En la lista **Origen de datos**, elija **Archivo de base de datos de Microsoft SQL Server** y, después, elija el botón **Continuar**.  
  
     Aparecerá el cuadro de diálogo **Agregar conexión**.  
  
6.  En el cuadro **Nombre del archivo de la base de datos**, especifique el archivo que creó siguiendo los pasos del [Tutorial: Crear un archivo de base de datos local en Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md), o elija el botón **Examinar** y, después, busque el archivo.  
  
     De forma predeterminada, el archivo se encuentra en Usuarios\\*SuCuenta*\\Documentos\\Visual Studio *Versión*\\Projects\\SampleDatabaseWalkthrough\\SampleDatabaseWalkthrough.  
  
7.  En **Conexión con el servidor**, acepte los valores predeterminados, elija el botón **Aceptar** y, a continuación, el botón **Siguiente**.  
  
    > [!NOTE]
    >  Al conectar con un archivo de bases de datos local, puede crear una copia de la base de datos en su proyecto, o puede conectar con el archivo de base de datos existente en su ubicación actual.  Vea [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  En el cuadro de diálogo que aparece, elija **Sí** para copiar el archivo de base de datos en el proyecto.  
  
9. En la página **Guardar cadena de conexión en el archivo de config. de la aplicación**, elija el botón **Siguiente**.  
  
10. En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas**, active la casillas **Customers** y **Orders** y, a continuación elija el botón **Finalizar**.  
  
     Se agrega **SampleDatabaseDataSet** al proyecto y aparecen las tablas **Customers** y **Orders** en la ventana **Orígenes de datos**.  
  
##  <a name="BKMK_AddCtrls"></a> Agregar controles enlazados a datos  
  
#### Para agregar controles enlazados a datos  
  
1.  Mueva el nodo **Customers** principal de la ventana **Orígenes de datos** a **Form1**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
2.  Para ejecutar la aplicación y mostrar los datos que agregó en el tutorial anterior, elija la tecla F5.  
  
3.  Elija el icono amarillo de suma \(![Botón Agregar en Windows Forms](../data-tools/media/addrecord.png "AddRecord")\), agregue un registro de cliente y seleccione el icono de disco \(![Botón Guardar en Windows Forms](../data-tools/media/saveinwf.png "SaveInWF")\) para guardar los cambios.  
  
4.  Elimine el registro que acaba de crear. Para ello, elíjalo y seleccione el icono de eliminación de color rojo \(![Botón Eliminar en Windows Forms](../data-tools/media/deleterecord.png "DeleteRecord")\).  
  
## Pasos siguientes  
 Si quiere crear o modificar objetos en el conjunto de datos, abra el origen de datos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  También puede agregar lógica de validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos.  Vea [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## Vea también  
 [Información general de datos locales](../data-tools/local-data-overview.md)   
 [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)