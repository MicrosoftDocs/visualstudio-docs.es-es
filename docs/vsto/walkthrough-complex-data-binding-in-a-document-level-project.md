---
title: 'Tutorial: Enlace de datos complejo en un proyecto de nivel de documento'
description: Obtenga información sobre cómo puede enlazar varias celdas de una hoja de cálculo de Microsoft Excel a los campos de la base de datos northwind SQL Server datos.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a85f46cf9c234ad662966372a8d014ae0f98be84
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826374"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Tutorial: Enlace de datos complejo en un proyecto de nivel de documento
  En este tutorial se muestran los conceptos básicos del enlace de datos complejo en un proyecto de nivel de documento. Puede enlazar varias celdas de una hoja Microsoft Office excel a los campos de la base de datos northwind SQL Server datos.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar un origen de datos al proyecto de libro.

- Agregar controles enlazados a datos a una hoja de cálculo.

- Guardar los cambios de datos en la base de datos.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server ejemplo.

- Permisos para leer y escribir en la base de datos SQL Server datos.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 El primer paso es crear un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **My Complex Data Binding**. En el asistente, seleccione **Crear un nuevo documento.**

     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega **el proyecto Mi enlace** de datos complejo a **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Creación del origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente.**

4. Seleccione una conexión de datos al ejemplo Northwind SQL Server base de datos o agregue una nueva conexión mediante el **botón Nueva** conexión.

5. Después de seleccionar o crear una conexión, haga clic en **Siguiente.**

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic **en Siguiente.**

7. Expanda el nodo **Tablas** en la ventana **Objetos de base de** datos .

8. Active la casilla situada junto a la **tabla Empleados.**

9. Haga clic en **Finalizar**

   El asistente agrega la **tabla Employees** a la ventana **Orígenes de** datos. También agrega un conjunto de datos con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Una hoja de cálculo mostrará la **tabla Employees** cuando se abra el libro. Los usuarios podrán realizar cambios en los datos y, a continuación, guardar esos cambios en la base de datos haciendo clic en un botón.

 Para enlazar la hoja de cálculo a la tabla automáticamente, puede agregar un control a la hoja de cálculo <xref:Microsoft.Office.Tools.Excel.ListObject> desde la ventana Orígenes **de** datos. Para dar al usuario la opción de guardar los cambios, agregue <xref:System.Windows.Forms.Button> un control desde el cuadro de **herramientas**.

#### <a name="to-add-a-list-object"></a>Para agregar un objeto de lista

1. Compruebe que el **libro My Complex Data Binding.xlsx** está abierto en el diseñador Visual Studio, con **Sheet1** mostrado.

2. Abra la **ventana Orígenes de** datos y seleccione el nodo **Empleados.**

3. Haga clic en la flecha desplegable que aparece.

4. Seleccione **ListObject** en la lista desplegable.

5. Arrastre la tabla **Employees** a la **celda A6.**

     Se <xref:Microsoft.Office.Tools.Excel.ListObject> crea un control denominado en la celda `EmployeesListObject` **A6.** Al mismo tiempo, se agregan al proyecto un denominado , un adaptador de tabla y una <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` instancia de <xref:System.Data.DataSet> . El control está enlazado a , que a su <xref:System.Windows.Forms.BindingSource> vez está enlazado a la instancia de <xref:System.Data.DataSet> .

### <a name="to-add-a-button"></a>Para agregar un botón

1. En la **pestaña Controles comunes** del Cuadro de **herramientas**, agregue un control a la <xref:System.Windows.Forms.Button> celda **A4** de la hoja de cálculo.

   El siguiente paso consiste en agregar texto al botón cuando se abra la hoja de cálculo.

## <a name="initialize-the-control"></a>Inicialización del control
 Agregue texto al botón en el controlador <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de eventos.

### <a name="to-initialize-the-control"></a>Para inicializar el control

1. En **Explorador de soluciones**, haga clic con el botón derecho **en Sheet1.vb** o **Sheet1.cs** y, a continuación, haga **clic** en Ver código en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto de b `utton` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet8":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet8":::

3. Solo para C#, agregue un controlador de eventos para <xref:System.Windows.Forms.Control.Click> el evento al método `Sheet1_Startup` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet9":::

   Ahora agregue código para controlar <xref:System.Windows.Forms.Control.Click> el evento del botón.

## <a name="save-changes-to-the-database"></a>Guardar cambios en la base de datos
 Los cambios realizados en los datos solo existen en el conjunto de datos local hasta que se guardan explícitamente en la base de datos.

### <a name="to-save-changes-to-the-database"></a>Para guardar los cambios en la base de datos

1. Agregue un controlador de eventos para el evento de y agregue el código siguiente para confirmar todos los cambios realizados en el conjunto de datos en la base <xref:System.Windows.Forms.Control.Click> `button` de datos.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet10":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para comprobar que los datos aparecen según lo previsto y que puede manipular los datos en el objeto de lista.

### <a name="to-test-the-data-binding"></a>Para probar el enlace de datos

- Presione **F5**.

     Compruebe que cuando se abre el libro, el objeto de lista se rellena con datos de la **tabla Employees.**

### <a name="to-modify-data"></a>Para modificar datos

1. Haga clic en **la celda B7**, que debe contener el nombre **Damio**.

2. Escriba el nombre **Anderson** y presione **Entrar.**

### <a name="to-modify-a-column-header"></a>Para modificar un encabezado de columna

1. Haga clic en la celda que contiene el encabezado de columna **LastName**.

2. Escriba **Apellidos,** incluido un espacio entre las dos palabras y, a continuación, presione **Entrar.**

### <a name="to-save-data"></a>Para guardar datos

1. Haga clic **en Guardar** en la hoja de cálculo.

2. Salga de Excel. Haga **clic en No** cuando se le pida que guarde los cambios realizados.

3. Presione **F5** para volver a ejecutar el proyecto.

     El objeto de lista se rellena con datos de la **tabla Employees.**

4. Observe que el nombre de la **celda B7** sigue siendo **Anderson,** que es el cambio de datos que ha realizado y guardado en la base de datos. El encabezado de columna **LastName** ha cambiado a su forma original sin espacio, porque el encabezado de columna no está enlazado a la base de datos y no ha guardado los cambios realizados en la hoja de cálculo.

### <a name="to-add-new-rows"></a>Para agregar nuevas filas

1. Seleccione una celda dentro del objeto de lista.

    Aparece una nueva fila en la parte inferior de la lista, con un asterisco ( **\*** ) en la primera celda de la nueva fila.

2. Agregue la siguiente información en la fila vacía.

   |EmployeeID (Id. de empleado)|Apellidos|Nombre|Título|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Jefe de ventas|

### <a name="to-delete-rows"></a>Eliminación de filas

- Haga clic con el botón derecho en el número 16 (fila 16) en el lado izquierdo de la hoja de cálculo y, a continuación, haga clic **en Eliminar**.

### <a name="to-sort-the-rows-in-the-list"></a>Para ordenar las filas de la lista

1. Seleccione una celda dentro de la lista.

     Los botones de flecha aparecen en cada encabezado de columna.

2. Haga clic en el botón de flecha del **encabezado de columna** Apellidos.

3. Haga clic **en Ordenar ascendente.**

     Las filas se ordenan alfabéticamente por apellidos.

### <a name="to-filter-information"></a>Para filtrar información

1. Seleccione una celda dentro de la lista.

2. Haga clic en el botón de flecha del **encabezado de** columna Título.

3. Haga clic **en Representante de ventas.**

     En la lista solo se muestran las filas que tienen **El representante de ventas** en la **columna** Título.

4. Haga clic de nuevo en el botón de flecha **del encabezado de** columna Título.

5. Haga **clic en (Todos)**.

     Se quita el filtrado y aparecen todas las filas.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos de enlazar una tabla de una base de datos a un objeto de lista. A continuación, podría realizar las siguientes tareas:

- Almacenar en caché los datos para que se puedan usar sin conexión. Para obtener más información, [vea Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Implementar la solución. Para obtener más información, vea [Implementar una solución de Office.](../vsto/deploying-an-office-solution.md)

- Cree una relación de maestro y detalle entre un campo y una tabla. Para obtener más información, vea [Tutorial: Crear una relación de detalles maestra mediante un conjunto de datos almacenado en caché.](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)

## <a name="see-also"></a>Consulte también
- [Enlace de datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Tutorial: Enlace de datos simple en un proyecto de nivel de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
