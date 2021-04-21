---
title: 'Tutorial: Enlace de datos simple en un proyecto de nivel de documento'
description: Conozca los conceptos básicos del enlace de datos en un proyecto de nivel de documento y que un único campo de datos de una base de datos SQL Server está enlazado a un intervalo con nombre en Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 36d4da65a6cd39c53f1f9d8edf4f9d9b1fe46284
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826855"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Tutorial: Enlace de datos simple en un proyecto de nivel de documento
  En este tutorial se muestran los conceptos básicos del enlace de datos en un proyecto de nivel de documento. Un único campo de datos de una base SQL Server de datos está enlazado a un intervalo con nombre en Microsoft Office Excel. El tutorial también muestra cómo agregar controles que permiten desplazarse por todos los registros de la tabla.

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

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server ejemplo.

- Permisos para leer y escribir en la base de datos SQL Server datos.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En este paso, creará un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **My Simple Data Binding (Mi enlace** de datos simple) mediante Visual Basic o C#. Asegúrese de que **está seleccionada la opción Crear** un nuevo documento. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **proyecto Mi enlace** de datos simple a **Explorador de soluciones**.

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

8. Active la casilla situada junto a la **tabla Clientes.**

9. Haga clic en **Finalizar**

   El asistente agrega la **tabla Customers** a la ventana **Orígenes de** datos. También agrega un conjunto de datos con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Para este tutorial, necesita dos intervalos con nombre y cuatro botones en la primera hoja de cálculo. En primer lugar, agregue los dos intervalos con nombre desde la **ventana Orígenes** de datos para que se enlazan automáticamente al origen de datos. A continuación, agregue los botones del cuadro **de herramientas**.

### <a name="to-add-two-named-ranges"></a>Para agregar dos intervalos con nombre

1. Compruebe que el *libro My Simple Data Binding.xlsx* está abierto en el diseñador Visual Studio datos, con **Sheet1** mostrado.

2. Abra la **ventana Orígenes de** datos y expanda el **nodo** Clientes.

3. Seleccione la **columna CompanyName** y, a continuación, haga clic en la flecha desplegable que aparece.

4. Seleccione **NamedRange** en la lista desplegable y arrastre la columna **CompanyName** a la **celda A1.**

     Se <xref:Microsoft.Office.Tools.Excel.NamedRange> crea un control denominado en la celda `companyNameNamedRange` **A1.** Al mismo tiempo, se agregan al proyecto un denominado , un adaptador de tabla y una <xref:System.Windows.Forms.BindingSource> `customersBindingSource` instancia de <xref:System.Data.DataSet> . El control está enlazado a , que a su <xref:System.Windows.Forms.BindingSource> vez está enlazado a la instancia de <xref:System.Data.DataSet> .

5. Seleccione la **columna CustomerID** en la **ventana Orígenes de** datos y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga **clic en NamedRange** en la lista desplegable y arrastre la **columna CustomerID** a la **celda B1.**

7. Otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado se crea en la celda `customerIDNamedRange` **B1** y se enlaza a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Para agregar cuatro botones

1. En la **pestaña Controles comunes** del Cuadro de **herramientas**, agregue un control a la <xref:System.Windows.Forms.Button> celda **A3** de la hoja de cálculo.

    Este botón se denomina `Button1` .

2. Agregue tres botones más a las celdas siguientes en este orden, para que los nombres sean como se muestra:

   |Cell|(Nombre)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   El siguiente paso consiste en agregar texto a los botones y, en C#, agregar controladores de eventos.

## <a name="initialize-the-controls"></a>Inicialización de los controles
 Establezca el texto del botón y agregue controladores de eventos durante el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento.

### <a name="to-initialize-the-controls"></a>Para inicializar los controles

1. En **Explorador de soluciones**, haga clic con el botón derecho **en Sheet1.vb** o **Sheet1.cs** y, a continuación, haga **clic** en Ver código en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto de cada botón.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet2":::

3. Solo para C#, agregue controladores de eventos para los eventos de clic de botón al `Sheet1_Startup` método .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet3":::

   Ahora agregue código para controlar los eventos de los botones para <xref:System.Windows.Forms.Control.Click> que el usuario pueda examinar los registros.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregar código para habilitar el desplazamiento por los registros
 Agregue código al controlador <xref:System.Windows.Forms.Control.Click> de eventos de cada botón para desplazarse por los registros.

### <a name="to-move-to-the-first-record"></a>Para pasar al primer registro

1. Agregue un controlador de eventos para el evento del botón y <xref:System.Windows.Forms.Control.Click> agregue el código siguiente para pasar al primer `Button1` registro:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet4":::

### <a name="to-move-to-the-previous-record"></a>Para pasar al registro anterior

1. Agregue un controlador de eventos para el evento del botón y agregue el código siguiente para volver a mover <xref:System.Windows.Forms.Control.Click> `Button2` la posición en uno:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet5":::

### <a name="to-move-to-the-next-record"></a>Para pasar al siguiente registro

1. Agregue un controlador de eventos para el evento del botón y <xref:System.Windows.Forms.Control.Click> agregue el código siguiente para avanzar la posición en `Button3` uno:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet6":::

### <a name="to-move-to-the-last-record"></a>Para pasar al último registro

1. Agregue un controlador de eventos para el evento del botón y <xref:System.Windows.Forms.Control.Click> agregue el código siguiente para pasar al último `Button4` registro:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que puede examinar los registros de la base de datos.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el primer registro aparece en las **celdas A1** y **B1.**

3. Haga clic **>** en el botón ( ) y confirme que el siguiente registro aparece en la celda `Button3` **A1** y **B1.**

4. Haga clic en los demás botones de desplazamiento para confirmar que el registro cambia según lo previsto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos de enlazar un intervalo con nombre a un campo de una base de datos. A continuación, podría realizar las siguientes tareas:

- Almacenar en caché los datos para que se puedan usar sin conexión. Para obtener más información, [vea Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Enlace celdas a varias columnas de una tabla, en lugar de a un campo. Para obtener más información, [vea Tutorial: Enlace de datos complejo en un proyecto de nivel de documento.](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)

- Use un <xref:System.Windows.Forms.BindingNavigator> control para desplazarse por los registros. Para obtener más información, [vea How to: Navigate data with the Windows Forms BindingNavigator control](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Tutorial: Enlace de datos complejo en un proyecto de nivel de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
