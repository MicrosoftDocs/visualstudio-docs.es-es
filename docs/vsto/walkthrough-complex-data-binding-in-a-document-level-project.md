---
title: 'Tutorial: enlace de datos complejo en un proyecto de nivel de documento'
description: Obtenga información sobre cómo puede enlazar varias celdas de una hoja de cálculo de Microsoft Excel a los campos de la base de datos de SQL Server Northwind.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 988394595e8aa4710a22e1fedf22a921481c7396
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527120"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Tutorial: enlace de datos complejo en un proyecto de nivel de documento
  En este tutorial se muestran los conceptos básicos del enlace de datos complejo en un proyecto de nivel de documento. Puede enlazar varias celdas de una Microsoft Office hoja de cálculo de Excel a los campos de la base de datos Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar un origen de datos al proyecto del libro.

- Agregar controles enlazados a datos a una hoja de cálculo.

- Guardar de nuevo los cambios de datos en la base de datos.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-a-new-project"></a>Creación de un proyecto
 El primer paso es crear un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi enlace de datos complejo**. En el asistente, seleccione **crear un nuevo documento**.

     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **My Complex Data Binding** a **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos a la base de datos de ejemplo Northwind SQL Server o agregue una nueva conexión mediante el botón **nueva conexión** .

5. Después de seleccionar o crear una conexión, haga clic en **siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el nodo **tablas** en la ventana **objetos de base de datos** .

8. Active la casilla situada junto a la tabla **Employees** .

9. Haga clic en **Finalizar**

   El asistente agrega la tabla **Employees** a la ventana **orígenes de datos** . También agrega un conjunto de un objeto con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Una hoja de cálculo mostrará la tabla **empleados** cuando se abra el libro. Los usuarios podrán realizar cambios en los datos y, a continuación, guardarlos de nuevo en la base de datos haciendo clic en un botón.

 Para enlazar la hoja de cálculo a la tabla automáticamente, puede Agregar un <xref:Microsoft.Office.Tools.Excel.ListObject> control a la hoja de cálculo desde la ventana **orígenes de datos** . Para proporcionar al usuario la opción de guardar los cambios, agregue un <xref:System.Windows.Forms.Button> control desde el **cuadro de herramientas**.

#### <a name="to-add-a-list-object"></a>Para agregar un objeto de lista

1. Compruebe que el libro **mis datos complejos Binding.xlsx** está abierto en el diseñador de Visual Studio, donde se muestra **Sheet1** .

2. Abra la ventana **orígenes de datos** y seleccione el nodo **empleados** .

3. Haga clic en la flecha desplegable que aparece.

4. Seleccione **ListObject** en la lista desplegable.

5. Arrastre la tabla **Employees** hasta la celda **A6**.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Se crea un control denominado `EmployeesListObject` en la celda **A6**. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` <xref:System.Data.DataSet> se agregan al proyecto un denominado, un adaptador de tabla y una instancia de. El control está enlazado a <xref:System.Windows.Forms.BindingSource> , que a su vez se enlaza a la <xref:System.Data.DataSet> instancia de.

### <a name="to-add-a-button"></a>Para agregar un botón

1. En la pestaña **controles comunes** del **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **a4** de la hoja de cálculo.

   El siguiente paso consiste en agregar texto al botón cuando se abra la hoja de cálculo.

## <a name="initialize-the-control"></a>Inicializar el control
 Agregue texto al botón en el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> controlador de eventos.

### <a name="to-initialize-the-control"></a>Para inicializar el control

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1. VB** o **Sheet1.CS** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto para la b `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Solo para C#, agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento al `Sheet1_Startup` método.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Ahora, agregue el código para controlar el <xref:System.Windows.Forms.Control.Click> evento del botón.

## <a name="save-changes-to-the-database"></a>Guardar cambios en la base de datos
 Cualquier cambio realizado en los datos solo existe en el conjunto de datos local hasta que se guardan explícitamente de nuevo en la base de datos.

### <a name="to-save-changes-to-the-database"></a>Para guardar los cambios en la base de datos

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento de `button` y agregue el código siguiente para confirmar todos los cambios que se han realizado en el conjunto de datos de nuevo en la base de datos.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para comprobar que los datos aparecen de la manera esperada y que puede manipular los datos del objeto de lista.

### <a name="to-test-the-data-binding"></a>Para probar el enlace de datos

- Presione **F5**.

     Compruebe que, cuando se abre el libro, el objeto de lista se rellena con datos de la tabla **Employees** .

### <a name="to-modify-data"></a>Para modificar datos

1. Haga clic en la celda **B7**, que debe contener el nombre **Davolio**.

2. Escriba el nombre **Anderson** y, a continuación, presione **entrar**.

### <a name="to-modify-a-column-header"></a>Para modificar un encabezado de columna

1. Haga clic en la celda que contiene el encabezado de columna **LastName**.

2. Escriba **Last Name**, incluido un espacio entre las dos palabras y, a continuación, presione **entrar**.

### <a name="to-save-data"></a>Para guardar datos

1. Haga clic en **Guardar** en la hoja de cálculo.

2. Salga de Excel. Haga clic en **no** cuando se le pida que guarde los cambios realizados.

3. Presione **F5** para volver a ejecutar el proyecto.

     El objeto de lista se rellena con datos de la tabla **Employees** .

4. Observe que el nombre de la celda **B7** sigue siendo **Anderson**, que es el cambio de datos que ha realizado y guardado en la base de datos. El encabezado de columna **LastName** ha cambiado a su forma original sin espacio, ya que el encabezado de columna no está enlazado a la base de datos y no ha guardado los cambios realizados en la hoja de cálculo.

### <a name="to-add-new-rows"></a>Para agregar nuevas filas

1. Seleccione una celda dentro del objeto de lista.

    Aparece una nueva fila en la parte inferior de la lista, con un asterisco (* *\** _) en la primera celda de la nueva fila.

2. Agregue la siguiente información en la fila vacía.

   |EmployeeID|Apellidos|Nombre|Title|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Jefe de ventas|

### <a name="to-delete-rows"></a>Eliminación de filas

- Haga clic con el botón secundario en el número 16 (fila 16) en el extremo izquierdo de la hoja de cálculo y, a continuación, haga clic en _ * eliminar * *.

### <a name="to-sort-the-rows-in-the-list"></a>Para ordenar las filas de la lista

1. Seleccione una celda de la lista.

     Los botones de flecha aparecen en cada encabezado de columna.

2. Haga clic en el botón de flecha del encabezado de columna **Last Name** .

3. Haga clic en **orden ascendente**.

     Las filas se ordenan alfabéticamente por apellidos.

### <a name="to-filter-information"></a>Para filtrar la información

1. Seleccione una celda de la lista.

2. Haga clic en el botón de flecha del encabezado de columna **título** .

3. Haga clic en **representante de ventas**.

     La lista solo muestra las filas que tienen el **representante de ventas** en la columna **título** .

4. Haga clic de nuevo en el botón de flecha del encabezado de columna **título** .

5. Haga clic en **(todos)**.

     Se quita el filtrado y aparecen todas las filas.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos del enlace de una tabla de una base de datos a un objeto de lista. A continuación, podría realizar las siguientes tareas:

- Almacene en caché los datos para que se puedan usar sin conexión. Para obtener más información, consulte [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Implementar la solución. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

- Cree una relación principal-detalle entre un campo y una tabla. Para obtener más información, vea [Tutorial: crear una relación maestra de detalles mediante un conjunto de datos almacenado en memoria caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Tutorial: enlace de datos simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
