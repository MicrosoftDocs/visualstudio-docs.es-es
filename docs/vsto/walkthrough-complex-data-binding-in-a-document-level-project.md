---
title: 'Tutorial: Enlace de datos complejo en un proyecto de nivel de documento | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a46a0f30fe3ab0cfc44a4cdb9121c4f39f3c417f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento
  Este tutorial muestran los aspectos básicos del enlace de datos complejo en un proyecto de nivel de documento. Puede enlazar varias celdas de una hoja de cálculo de Microsoft Office Excel a los campos de la base de datos Northwind de SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un origen de datos a un proyecto de libro.  
  
-   Agregar controles enlazados a datos a una hoja de cálculo.  
  
-   Guardar los cambios de datos en la base de datos.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos para leer y escribir en la base de datos de SQL Server.  
  
## <a name="creating-a-new-project"></a>Crear un proyecto nuevo  
 El primer paso es crear un proyecto de libro de Excel.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi enlace de datos complejo**. En el asistente, seleccione **crear un nuevo documento**.  
  
     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi enlace de datos complejo** proyecto al **el Explorador de soluciones**.  
  
## <a name="creating-the-data-source"></a>Crear el origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.  
  
5.  Después de que se ha seleccionado o creado una conexión, haga clic en **siguiente**.  
  
6.  Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7.  Expanda el **tablas** nodo en el **objetos de base de datos** ventana.  
  
8.  Active la casilla situada junto a la **empleados** tabla.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega la **empleados** la tabla a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 Se mostrará una hoja de cálculo el **empleados** tabla cuando se abre el libro. Los usuarios podrán realizar cambios en los datos y, a continuación, guardar los cambios a la base de datos haciendo clic en un botón.  
  
 Para enlazar automáticamente la hoja de cálculo a la tabla, puede agregar un <xref:Microsoft.Office.Tools.Excel.ListObject> control a la hoja de cálculo desde el **orígenes de datos** ventana. Para dar al usuario la opción para guardar los cambios, agregue un <xref:System.Windows.Forms.Button> controlar desde la **cuadro de herramientas**.  
  
#### <a name="to-add-a-list-object"></a>Para agregar un objeto de lista  
  
1.  Compruebe que la **Binding.xlsx de datos complejos mi** libro está abierto en el Diseñador de Visual Studio, con **Sheet1** muestra.  
  
2.  Abra la **orígenes de datos** ventana y seleccione el **empleados** nodo.  
  
3.  Haga clic en la flecha de lista desplegable que aparece.  
  
4.  Seleccione **ListObject** en la lista desplegable.  
  
5.  Arrastre el **empleados** tabla a la celda **A6**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado `EmployeesListObject` se crea en la celda **A6**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `EmployeesBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> instancia se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.  
  
#### <a name="to-add-a-button"></a>Para agregar un botón  
  
1.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **A4** de la hoja de cálculo.  
  
 El siguiente paso es agregar texto al botón cuando se abre la hoja de cálculo.  
  
## <a name="initializing-the-control"></a>Inicializar el control  
 Agregar texto al botón en la <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> controlador de eventos.  
  
#### <a name="to-initialize-the-control"></a>Para inicializar el control  
  
1.  En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el código siguiente a la `Sheet1_Startup` método para establecer el texto de la b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Sólo para C#, agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos para el `Sheet1_Startup` método.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 Ahora, agregue código para controlar la <xref:System.Windows.Forms.Control.Click> eventos del botón.  
  
## <a name="saving-changes-to-the-database"></a>Guardando los cambios en la base de datos  
 Los cambios se realizaron en los datos solo existen en el conjunto de datos local hasta que se guardan explícitamente en la base de datos.  
  
#### <a name="to-save-changes-to-the-database"></a>Para guardar los cambios en la base de datos  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la herramienta b`utton`y agregue el código siguiente para confirmar todos los cambios realizados en el conjunto de datos a la base de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para comprobar que los datos aparecen como se esperaba y que se pueden manipular los datos en el objeto de lista.  
  
#### <a name="to-test-the-data-binding"></a>Para probar el enlace de datos  
  
-   Presione F5.  
  
     Compruebe que, cuando se abre el libro, el objeto de lista se rellena con datos de la **empleados** tabla.  
  
#### <a name="to-modify-data"></a>Para modificar datos  
  
1.  Haga clic en la celda **B7**, que debe contener el nombre **Davolio**.  
  
2.  Escriba el nombre **Anderson**, y, a continuación, presione ENTRAR.  
  
#### <a name="to-modify-a-column-header"></a>Para modificar un encabezado de columna  
  
1.  Haga clic en la celda que contiene el encabezado de columna **LastName**.  
  
2.  Tipo de **Last Name**, incluido un espacio entre las dos palabras y, a continuación, presione ENTRAR.  
  
#### <a name="to-save-data"></a>Para guardar los datos  
  
1.  Haga clic en **guardar** en la hoja de cálculo.  
  
2.  Salga de Excel. Haga clic en **n** cuando se le pida que guarde los cambios realizados.  
  
3.  Presione F5 para ejecutar el proyecto de nuevo.  
  
     El objeto de lista se rellena con datos de la **empleados** tabla.  
  
4.  Tenga en cuenta que el nombre de la celda **B7** sigue siendo **Anderson**, que son los datos de los cambios realizados y volver a guardar la base de datos. El encabezado de columna **LastName** ha cambiado a su forma original sin ningún espacio, porque el encabezado de columna no está enlazado a la base de datos y no ha guardado los cambios realizados en la hoja de cálculo.  
  
#### <a name="to-add-new-rows"></a>Para agregar nuevas filas  
  
1.  Seleccione una celda dentro del objeto de lista.  
  
     Aparecerá una nueva fila en la parte inferior de la lista, con un asterisco (**\***) en la primera celda de la nueva fila.  
  
2.  Agregue la siguiente información en la fila vacía.  
  
    |IdEmpleado|LastName|Nombre|Title|  
    |----------------|--------------|---------------|-----------|  
    |10|Gil|Enrique|Director de ventas|  
  
#### <a name="to-delete-rows"></a>Para eliminar filas  
  
-   Haga clic en el número 16 (fila 16) en el lado izquierdo de la hoja de cálculo y, a continuación, haga clic en **eliminar**.  
  
#### <a name="to-sort-the-rows-in-the-list"></a>Para ordenar las filas de la lista  
  
1.  Seleccione una celda dentro de la lista.  
  
     Botones de flecha aparecen en cada encabezado de columna.  
  
2.  Haga clic en el botón de flecha en el **Last Name** encabezado de columna.  
  
3.  Haga clic en **ordena en orden ascendente**.  
  
     Las filas se ordenan alfabéticamente por apellidos.  
  
#### <a name="to-filter-information"></a>Para filtrar la información  
  
1.  Seleccione una celda dentro de la lista.  
  
2.  Haga clic en el botón de flecha en el **título** encabezado de columna.  
  
3.  Haga clic en **representante de ventas**.  
  
     La lista muestra sólo aquellas filas que tienen **representante de ventas** en el **título** columna.  
  
4.  Haga clic en el botón de flecha en el **título** nuevo encabezado de columna.  
  
5.  Haga clic en **(All)**.  
  
     El filtrado se quita y se mostrarán todas las filas.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos de enlazar una tabla en una base de datos a un objeto de lista. A continuación, podría realizar las siguientes tareas:  
  
-   Almacenar en caché los datos para que se puede usar sin conexión. Para obtener más información, consulte [Cómo: datos de la caché para uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Implementar la solución. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Crear a una relación principal-detalle entre un campo y una tabla. Para obtener más información, consulte [Tutorial: crear una relación de detalle maestra utilizando un conjunto de datos almacenado en memoria caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Tutorial: Enlace de datos simple en un proyecto en el nivel del documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  