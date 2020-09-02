---
title: 'Tutorial: enlace de datos simple en un proyecto de nivel de documento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b573842aee5f00f161213cf3e01dfcc4c8ba93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62981067"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Tutorial: enlace de datos simple en un proyecto de nivel de documento
  En este tutorial se muestran los aspectos básicos del enlace de datos en un proyecto de nivel de documento. Un único campo de datos en una base de datos de SQL Server se enlaza a un rango con nombre en Microsoft Office Excel. En el tutorial también se muestra cómo agregar controles que le permiten desplazarse por todos los registros de la tabla.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un origen de datos para un proyecto de Excel.

- Agregar controles a una hoja de cálculo.

- Desplazarse por los registros de base de datos.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto
 En este paso, creará un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi enlace de datos simple**, mediante Visual Basic o C#. Asegúrese de que **la opción crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **My simple Data Binding** a **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos**de Windows.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos a la base de datos de ejemplo Northwind SQL Server o agregue una nueva conexión mediante el botón **nueva conexión** .

5. Después de seleccionar o crear una conexión, haga clic en **siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el nodo **tablas** en la ventana **objetos de base de datos** .

8. Active la casilla situada junto a la tabla **Customers** .

9. Haga clic en **Finalizar**

   El asistente agrega la tabla **Customers** a la ventana **orígenes de datos** . También agrega un conjunto de un objeto con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Para este tutorial, necesita dos rangos con nombre y cuatro botones en la primera hoja de cálculo. En primer lugar, agregue los dos rangos con nombre desde la ventana **orígenes de datos** para que se enlacen automáticamente al origen de datos. A continuación, agregue los botones del **cuadro de herramientas**.

### <a name="to-add-two-named-ranges"></a>Para agregar dos rangos con nombre

1. Compruebe que el libro *My simple Data Binding.xlsx* está abierto en el diseñador de Visual Studio, donde se muestra **Sheet1** .

2. Abra la ventana **orígenes de datos** y expanda el nodo **clientes** .

3. Seleccione la columna **CompanyName** y, a continuación, haga clic en la flecha desplegable que aparece.

4. Seleccione **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **CompanyName** hasta la celda **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Se crea un control denominado `companyNameNamedRange` en la celda **a1**. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `customersBindingSource` <xref:System.Data.DataSet> se agregan al proyecto un denominado, un adaptador de tabla y una instancia de. El control está enlazado a <xref:System.Windows.Forms.BindingSource> , que a su vez se enlaza a la <xref:System.Data.DataSet> instancia de.

5. Seleccione la columna **CustomerID** en la ventana **orígenes de datos** y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **CustomerID** hasta la celda **B1**.

7. Otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `customerIDNamedRange` se crea en la celda **B1**y se enlaza a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Para agregar cuatro botones

1. En la pestaña **controles comunes** del **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **a3** de la hoja de cálculo.

    Este botón se denomina `Button1` .

2. Agregue tres botones más a las celdas siguientes en este orden, de modo que los nombres sean como se muestra a continuación:

   |Cell|(Nombre)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   El siguiente paso consiste en agregar texto a los botones y en C# agregar controladores de eventos.

## <a name="initialize-the-controls"></a>Inicializar los controles
 Establezca el texto del botón y agregue los controladores de eventos durante el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento.

### <a name="to-initialize-the-controls"></a>Para inicializar los controles

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1. VB** o **Sheet1.CS**y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto para cada botón.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Solo para C#, agregue controladores de eventos para los eventos de clic de botón al `Sheet1_Startup` método.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Ahora, agregue el código para controlar los <xref:System.Windows.Forms.Control.Click> eventos de los botones de modo que el usuario pueda desplazarse por los registros.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregue código para habilitar el desplazamiento por los registros
 Agregue código al <xref:System.Windows.Forms.Control.Click> controlador de eventos de cada botón para desplazarse por los registros.

### <a name="to-move-to-the-first-record"></a>Para ir al primer registro

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento del `Button1` botón y agregue el código siguiente para pasar al primer registro:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Para desplace al registro anterior

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento del `Button2` botón y agregue el código siguiente para devolver la posición en uno:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Para ir al siguiente registro

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento del `Button3` botón y agregue el código siguiente para avanzar la posición en uno:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Para ir al último registro

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento del `Button4` botón y agregue el código siguiente para pasar al último registro:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que puede examinar los registros de la base de datos.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el primer registro aparece en las celdas **a1** y **B1**.

3. Haga clic en el **>** `Button3` botón () y confirme que el siguiente registro aparece en las celdas **a1** y **B1**.

4. Haga clic en los botones de desplazamiento para confirmar que el registro cambia según lo previsto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos del enlace de un rango con nombre a un campo de una base de datos. A continuación, podría realizar las siguientes tareas:

- Almacene en caché los datos para que se puedan usar sin conexión. Para obtener más información, consulte [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Enlazar celdas a varias columnas de una tabla, en lugar de a un campo. Para obtener más información, vea [Tutorial: enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Use un <xref:System.Windows.Forms.BindingNavigator> control para desplazarse por los registros. Para obtener más información, vea [Cómo: navegar por los datos con el control BindingNavigator de Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Tutorial: enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
