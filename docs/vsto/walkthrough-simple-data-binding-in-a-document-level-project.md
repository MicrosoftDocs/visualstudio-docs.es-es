---
title: 'Tutorial: Enlace de datos Simple en un proyecto de nivel de documento'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25173e5c4d4aeb02045cf858ae1e093b7a04d2bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824385"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Tutorial: Enlace de datos Simple en un proyecto de nivel de documento
  Este tutorial muestra los aspectos básicos del enlace de datos en un proyecto de nivel de documento. Un único campo de datos en una base de datos de SQL Server está enlazado a un rango con nombre en Microsoft Office Excel. El tutorial también muestra cómo agregar controles que permiten desplazarse por todos los registros de la tabla.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Creación de un origen de datos para un proyecto de Excel.  
  
- Agregar controles a una hoja de cálculo.  
  
- Desplazarse por los registros de base de datos.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos para leer y escribir en la base de datos de SQL Server.  
  
## <a name="create-a-new-project"></a>Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1. Cree un proyecto de libro de Excel con el nombre **Mi enlace de datos Simple**, mediante Visual Basic o C#. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi enlace de datos Simple** proyecto a **el Explorador de soluciones**.  
  
## <a name="create-the-data-source"></a>Crear el origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1. Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.  
  
2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.  
  
4. Seleccione una conexión de datos para la base de datos de SQL Server de ejemplo Northwind, o agregue una nueva conexión mediante el **nueva conexión** botón.  
  
5. Después de haberse seleccionada o creada una conexión, haga clic en **siguiente**.  
  
6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7. Expanda el **tablas** nodo en el **objetos de base de datos** ventana.  
  
8. Active la casilla situada junto a la **clientes** tabla.  
  
9. Haga clic en **Finalizar**.  
  
   El asistente agrega los **clientes** la tabla a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.  
  
## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 En este tutorial, necesita dos rangos con nombre y cuatro botones en la primera hoja de cálculo. En primer lugar, agregue los dos rangos con nombre desde el **orígenes de datos** ventana para que se enlazan automáticamente al origen de datos. A continuación, agregue los botones de la **cuadro de herramientas**.  
  
### <a name="to-add-two-named-ranges"></a>Para agregar dos rangos con nombre  
  
1.  Compruebe que la *Binding.xlsx de datos Simple mi* libro está abierto en el Diseñador de Visual Studio, con **Sheet1** muestra.  
  
2.  Abra el **orígenes de datos** ventana y expanda el **clientes** nodo.  
  
3.  Seleccione el **CompanyName** columna y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
4.  Seleccione **NamedRange** en la lista desplegable y, a continuación, arrastre el **CompanyName** columna a la celda **A1**.  
  
     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `companyNameNamedRange` se crea en la celda **A1**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `customersBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> instancia se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.  
  
5.  Seleccione el **CustomerID** columna en el **orígenes de datos** ventana y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
6.  Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre el **CustomerID** columna a la celda **B1**.  
  
7.  Otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `customerIDNamedRange` se crea en la celda **B1**y se enlaza a la <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Para agregar cuatro botones  
  
1. Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **A3** de la hoja de cálculo.  
  
    Este botón se llamaba `Button1`.  
  
2. Agregue tres botones más a las celdas siguientes en este orden, para que los nombres son como se muestra:  
  
   |celda|(Nombre)|  
   |----------|--------------|  
   |B3|Button2|  
   |C3|Button3|  
   |D3|Button4|  
  
   El siguiente paso es agregar texto a los botones y en C#, agregue los controladores de eventos.  
  
## <a name="initialize-the-controls"></a>Inicializar los controles  
 Establezca el texto del botón y agregue los controladores de eventos durante la <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eventos.  
  
### <a name="to-initialize-the-controls"></a>Para inicializar los controles  
  
1. En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2. Agregue el código siguiente a la `Sheet1_Startup` método para establecer el texto para cada botón.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. Solo en C#, agregue controladores de eventos para el botón, haga clic en eventos para el `Sheet1_Startup` método.  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   Ahora, agregue código para controlar la <xref:System.Windows.Forms.Control.Click> eventos de los botones para que el usuario puede examinar los registros.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregue código para habilitar el desplazamiento por los registros  
 Agregue código a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de cada botón para desplazarse por los registros.  
  
### <a name="to-move-to-the-first-record"></a>Para desplazarse al primer registro  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la `Button1` botón y agregue el código siguiente para desplazarse al primer registro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Mover al registro anterior  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la `Button2` botón y agregue el código siguiente para devolver la posición uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Para desplazarse al siguiente registro  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la `Button3` botón y agregue el código siguiente para hacer avanzar la posición uno:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Para mover al último registro  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de la `Button4` botón y agregue el siguiente código para mover al último registro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar su libro para asegurarse de que puede examinar los registros de la base de datos.  
  
### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Confirme que el primer registro aparece en las celdas **A1** y **B1**.  
  
3.  Haga clic en el **>** (`Button3`) botón y confirme que el registro siguiente aparece en la celda **A1** y **B1**.  
  
4.  Haga clic en los otros botones de desplazamiento para confirmar que el registro cambia según lo previsto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del enlace de un rango con nombre a un campo en una base de datos. A continuación, podría realizar las siguientes tareas:  
  
-   Almacenar en caché los datos para que se puede usar sin conexión. Para obtener más información, consulte [Cómo: almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Enlazar celdas a varias columnas en una tabla, en lugar de a un campo. Para obtener más información, consulte [Tutorial: enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Use un <xref:System.Windows.Forms.BindingNavigator> control para desplazarse por los registros. Para obtener más información, consulte [Cómo: desplazarse por datos con el control BindingNavigator de Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Tutorial: Enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  