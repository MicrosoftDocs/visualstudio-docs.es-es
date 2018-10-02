---
title: 'Tutorial: Conectarse a datos en un archivo de base de datos Local (formularios Windows Forms) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9b2d17c5ed86e37d3c674ef9238702cd8557a90f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580524"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Tutorial: Conectar con los datos de un archivo de base de datos local (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede mostrar rápida y fácilmente los datos de un archivo de base de datos local en la aplicación creando un conjunto de datos y agregando controles enlazados a datos a la aplicación. En este tutorial, mostrará los datos del archivo de base de datos local que creó siguiendo los pasos descritos en [crear una base de datos SQL mediante un diseñador](../data-tools/create-a-sql-database-by-using-a-designer.md). Después de crear un proyecto de Windows Forms, se conectará a dicha base de datos para indicar que desea que los datos de la tabla Clientes aparezcan en una cuadrícula de datos en el formulario para la aplicación.  
  
 Al crear una base de datos en Visual Studio 2013, el motor de SQL Server Express LocalDB se utiliza para tener acceso a un archivo de base de datos (.mdf) en SQL Server 2012. En versiones anteriores de Visual Studio, el motor de SQL Server Express se utiliza para tener acceso a un archivo de base de datos (.mdf). Consulte [Local Data Overview](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 En este tutorial se incluyen las tareas siguientes:  
  
-   [Crear y configurar un conjunto de datos](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Agregar controles enlazados a datos](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, necesitará acceso a la base de datos SampleDatabase.mdf creada siguiendo [crear una base de datos SQL mediante un diseñador](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Crear y configurar un conjunto de datos  
  
#### <a name="to-create-and-configure-a-dataset"></a>Para crear y configurar un conjunto de datos  
  
1.  Crear un proyecto de Windows Forms y asígnele el nombre **ConnectLocalData**.  
  
     Consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Si el **orígenes de datos** ventana no está visible, elija las teclas Mayús-Alt-D o, en la barra de menús, elija **vista**, **Other Windows**, **Mostrar orígenes de datos**.  
  
3.  En el **orígenes de datos** ventana, elija el **Agregar nuevo origen de datos** vínculo.  
  
     En el **Asistente para configuración de origen de datos**, elija el **siguiente** botón dos veces para aceptar la configuración predeterminada.  
  
4.  En el **elegir la conexión de datos** página, elija el **nueva conexión** botón.  
  
     El **Elegir origen de datos** aparece el cuadro de diálogo.  
  
5.  En el **origen de datos** elija **el archivo de base de datos de Microsoft SQL Server**y, a continuación, elija el **continuar** botón.  
  
     El **Agregar conexión** aparece el cuadro de diálogo.  
  
6.  En el **nombre de archivo de base de datos** , especifique el archivo que creó siguiendo los pasos [crear una base de datos SQL mediante un diseñador](../data-tools/create-a-sql-database-by-using-a-designer.md), o elija el **examinar** y, a continuación, busque ese archivo.  
  
     De forma predeterminada, el archivo está en los usuarios\\*suCuenta*\Documents\Visual Studio *versión*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  En **inicie sesión en el servidor**, acepte los valores predeterminados, elija el **Aceptar** botón y, a continuación, elija el **siguiente** botón.  
  
    > [!NOTE]
    >  Al conectar con un archivo de bases de datos local, puede crear una copia de la base de datos en su proyecto, o puede conectar con el archivo de base de datos existente en su ubicación actual. Consulte [Cómo: administrar archivos de datos locales en el proyecto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  En el cuadro de diálogo que aparece, elija **Sí** para copiar el archivo de base de datos al proyecto.  
  
9. En el **Guardar cadena de conexión en el archivo de configuración de aplicación** página, elija el **siguiente** botón.  
  
10. En el **elija los objetos de base de datos** , expanda el **tablas** nodo, seleccione el **clientes** y **pedidos** casillas de verificación y, a continuación, Elija la **finalizar** botón.  
  
     El **SampleDatabaseDataSet** se agrega al proyecto y el **clientes** y **pedidos** tablas aparecen en la **orígenes de datos** ventana.  
  
##  <a name="BKMK_AddCtrls"></a> Agregar controles enlazados a datos  
  
#### <a name="to-add-data-bound-controls"></a>Para agregar controles enlazados a datos  
  
1.  Mover el método main **clientes** nodo desde el **orígenes de datos** ventana hasta **Form1**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
2.  Para ejecutar la aplicación y mostrar los datos que agregó en el tutorial anterior, elija la tecla F5.  
  
3.  Elija el icono amarillo de suma (![botón Agregar en el formulario de Windows](../data-tools/media/addrecord.png "AddRecord")), agregue un registro de cliente y, a continuación, guarde los cambios eligiendo el icono de disco (![botón Guardar en el formulario de Windows](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Eliminar el registro que acaba de crear seleccionándola y, a continuación, elija el icono de eliminación de color rojo (![botón Eliminar en el formulario de Windows](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede crear o modificar objetos en el conjunto de datos si abre el origen de datos en el [crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md). También puede agregar lógica de validación a los eventos <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de datos locales](../data-tools/local-data-overview.md)   
 [Cómo: administrar archivos de datos locales en el proyecto](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)