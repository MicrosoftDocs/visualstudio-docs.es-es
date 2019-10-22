---
title: 'Tutorial: Enlace de datos complejo en un proyecto de nivel de documento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 026dc77573bbedce7882f9b3cceab049ef1066e4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692343"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Tutorial: Enlace de datos complejo en un proyecto de nivel de documento
  Este tutorial muestra los aspectos básicos del enlace de datos complejo en un proyecto de nivel de documento. Puede enlazar varias celdas en una hoja de cálculo de Microsoft Office Excel a los campos de la base de datos Northwind de SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar un origen de datos a su proyecto de libro.

- Agregar controles enlazados a datos a una hoja de cálculo.

- Guardar los cambios de datos en la base de datos.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 El primer paso es crear un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **Mi enlace de datos complejo**. En el asistente, seleccione **crear un nuevo documento**.

     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi enlace de datos complejo** proyecto a **el Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos para la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.

5. Después de haberse seleccionada o creada una conexión, haga clic en **siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el **tablas** nodo en el **objetos de base de datos** ventana.

8. Active la casilla situada junto a la **empleados** tabla.

9. Haga clic en **Finalizar**.

   El asistente agrega los **empleados** la tabla a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Se mostrará una hoja de cálculo el **empleados** tabla cuando se abre el libro. Los usuarios podrán realizar cambios en los datos y, a continuación, guardar los cambios en la base de datos, haga clic en un botón.

 Para enlazar automáticamente la hoja de cálculo a la tabla, puede agregar un <xref:Microsoft.Office.Tools.Excel.ListObject> control a la hoja de cálculo desde el **orígenes de datos** ventana. Para conceder al usuario la opción para guardar los cambios, agregue un <xref:System.Windows.Forms.Button> controlar desde la **cuadro de herramientas**.

#### <a name="to-add-a-list-object"></a>Para agregar un objeto de lista

1. Compruebe que la **mi Binding.xlsx datos complejos** libro está abierto en el Diseñador de Visual Studio, con **Sheet1** muestra.

2. Abra el **orígenes de datos** ventana y seleccione el **empleados** nodo.

3. Haga clic en la flecha de lista desplegable que aparece.

4. Seleccione **ListObject** en la lista desplegable.

5. Arrastre el **empleados** tabla a la celda **A6**.

     Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado `EmployeesListObject` se crea en la celda **A6**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `EmployeesBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> instancia se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.

### <a name="to-add-a-button"></a>Para agregar un botón

1. Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **A4** de la hoja de cálculo.

   El siguiente paso es agregar texto al botón cuando se abre la hoja de cálculo.

## <a name="initialize-the-control"></a>Inicializar el control
 Agregar texto al botón en el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> controlador de eventos.

### <a name="to-initialize-the-control"></a>Para inicializar el control

1. En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **ver código** en el menú contextual.

2. Agregue el código siguiente a la `Sheet1_Startup` método para establecer el texto de la b`utton`.

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Solo en C#, agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos para el `Sheet1_Startup` método.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Ahora, agregue código para controlar la <xref:System.Windows.Forms.Control.Click> eventos del botón.

## <a name="save-changes-to-the-database"></a>Guardar los cambios en la base de datos
 Se han realizado cambios a los datos solo existen en el conjunto de datos local hasta que explícitamente se guardan en la base de datos.

### <a name="to-save-changes-to-the-database"></a>Para guardar los cambios en la base de datos

1. Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la `button`y agregue el código siguiente para confirmar todos los cambios que se han realizado en el conjunto de datos a la base de datos.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Probar la aplicación
 Ahora puede probar el libro para comprobar que los datos aparecen como se esperaba y que puede manipular los datos del objeto de lista.

### <a name="to-test-the-data-binding"></a>Para probar el enlace de datos

- Presione **F5**.

     Compruebe que, cuando se abre el libro, el objeto de lista se rellena con datos de la **empleados** tabla.

### <a name="to-modify-data"></a>Para modificar los datos

1. Haga clic en la celda **B7**, que debe contener el nombre **Davolio**.

2. Escriba el nombre **Anderson**y, a continuación, presione **ENTRAR**.

### <a name="to-modify-a-column-header"></a>Para modificar un encabezado de columna

1. Haga clic en la celda que contiene el encabezado de columna **LastName**.

2. Tipo **apellido**, incluido un espacio entre las dos palabras y, a continuación, presione **ENTRAR**.

### <a name="to-save-data"></a>Para guardar los datos

1. Haga clic en **guardar** en la hoja de cálculo.

2. Salga de Excel. Haga clic en **No** cuando se le pida que guarde los cambios realizados.

3. Presione **F5** volver a ejecutar el proyecto.

     El objeto de lista se rellena con datos de la **empleados** tabla.

4. Tenga en cuenta que el nombre de la celda **B7** sigue siendo **Anderson**, que son los datos los cambios realizados y vuelve a guardar en la base de datos. El encabezado de columna **LastName** ha cambiado a su forma original sin espacio, porque el encabezado de columna no está enlazado a la base de datos y no ha guardado los cambios realizados en la hoja de cálculo.

### <a name="to-add-new-rows"></a>Para agregar nuevas filas

1. Seleccione una celda dentro del objeto de lista.

    Aparece una nueva fila en la parte inferior de la lista, con un asterisco ( **\*** ) en la primera celda de la nueva fila.

2. Agregue la siguiente información en la fila vacía.

   |EmployeeID|LastName|Nombre|Título|
   |----------------|--------------|---------------|-----------|
   |10|Gil|Enrique|Director de ventas|

### <a name="to-delete-rows"></a>Para eliminar filas

- Haga clic en el número 16 (fila 16) en la esquina izquierda de la hoja de cálculo y, a continuación, haga clic en **eliminar**.

### <a name="to-sort-the-rows-in-the-list"></a>Para ordenar las filas en la lista

1. Seleccione una celda dentro de la lista.

     Botones de flecha aparecen en cada encabezado de columna.

2. Haga clic en el botón de flecha en el **apellido** encabezado de columna.

3. Haga clic en **ordena en orden ascendente**.

     Las filas se ordenan alfabéticamente por apellido.

### <a name="to-filter-information"></a>Para filtrar la información

1. Seleccione una celda dentro de la lista.

2. Haga clic en el botón de flecha en el **título** encabezado de columna.

3. Haga clic en **representante de ventas**.

     La lista muestra solo las filas que tienen **representante de ventas** en el **título** columna.

4. Haga clic en el botón de flecha en el **título** nuevo encabezado de columna.

5. Haga clic en **(All)** .

     El filtrado se quita y se mostrarán todas las filas.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestra los aspectos básicos del enlace de una tabla en una base de datos a un objeto de lista. A continuación, podría realizar las siguientes tareas:

- Almacenar en caché los datos para que se puede usar sin conexión. Para obtener más información, vea [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Implementar la solución. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

- Crear a una relación principal-detalle entre un campo y una tabla. Para obtener más información, vea [Tutorial: Crear una relación de maestro/detalle con un conjunto de datos en caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Vea también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Tutorial: Enlace de datos simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
