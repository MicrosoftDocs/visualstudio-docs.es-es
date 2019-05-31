---
title: 'Tutorial: Crear a una relación de maestro/detalle con un conjunto de datos en caché'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3380b9c5302ed6e8a1bf6965f5fb1f259e3a6682
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438548"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Tutorial: Crear a una relación de maestro/detalle con un conjunto de datos en caché
  Este tutorial muestra la creación de una relación principal-detalle en una hoja de cálculo y almacenamiento en caché los datos para que la solución se puede usar sin conexión.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar controles a una hoja de cálculo.

- Configurar un conjunto de datos que se almacenen en una hoja de cálculo.

- Agregue código para habilitar el desplazamiento por los registros.

- Pruebe el proyecto.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a la base de datos de ejemplo Northwind de SQL Server. La base de datos puede estar en el equipo de desarrollo o en un servidor.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En este paso, creará un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi pantalla principal-detallada**, mediante Visual Basic o C#. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **mi pantalla principal-detallada** proyecto a **el Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos para la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.

5. Después de seleccionar o crear una conexión, haga clic en **siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el **tablas** nodo en el **objetos de base de datos** ventana.

8. Seleccione el **pedidos** tabla y el **Order Details** tabla.

9. Haga clic en **Finalizar**.

   El asistente agrega las dos tablas a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 En este paso, agregará un rango con nombre, un objeto de lista y dos botones a la primera hoja de cálculo. En primer lugar, agregue el rango con nombre y el objeto de lista de los **orígenes de datos** ventana para que se enlazan automáticamente al origen de datos. A continuación, agregue los botones de la **cuadro de herramientas**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Para agregar un rango con nombre y un objeto de lista

1. Compruebe que la **mi Master-Detail.xlsx** libro está abierto en el Diseñador de Visual Studio, con **Sheet1** muestra.

2. Abra el **orígenes de datos** ventana y expanda el **pedidos** nodo.

3. Seleccione el **OrderID** columna y, a continuación, haga clic en la flecha de lista desplegable que aparece.

4. Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre el **OrderID** columna a la celda **A2**.

     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `OrderIDNamedRange` se crea en la celda **A2**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `OrdersBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> instancia se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.

5. Desplácese más allá de las columnas que están bajo el **pedidos** tabla. En la parte inferior de la lista es la **Order Details** tabla; está aquí porque es un elemento secundario de la **pedidos** tabla. Seleccione esta opción **Order Details** de tabla, no lo que es el mismo nivel que el **pedidos** de tabla y, a continuación, haga clic en la flecha de lista desplegable que aparece.

6. Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre el **OrderDetails** tabla a la celda **A6**.

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado **Order_DetailsListObject** se crea en la celda **A6**y se enlaza a la <xref:System.Windows.Forms.BindingSource>.

### <a name="to-add-two-buttons"></a>Para agregar dos botones

1. Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **A3** de la hoja de cálculo.

    Este botón se llamaba `Button1`.

2. Agregue otro <xref:System.Windows.Forms.Button> control a la celda **B3** de la hoja de cálculo.

    Este botón se llamaba `Button2`.

   A continuación, marque el conjunto de datos en la memoria caché en el documento.

## <a name="cache-the-dataset"></a>Almacenar en caché el conjunto de datos
 Marque el conjunto de datos se almacene en caché en el documento haciendo que el conjunto de datos públicos y estableciendo el **CacheInDocument** propiedad.

### <a name="to-cache-the-dataset"></a>Para almacenar en caché el conjunto de datos

1. Seleccione **NorthwindDataSet** en la Bandeja de componentes.

2. En el **propiedades** ventana, cambie el **modificadores** propiedad **pública**.

    Los conjuntos de datos deben ser públicos antes de que está habilitada la caché.

3. Cambiar el **CacheInDocument** propiedad **True**.

   El siguiente paso es agregar texto a los botones y en C#, agregue código para enlazar los controladores de eventos.

## <a name="initialize-the-controls"></a>Inicializar los controles
 Establezca el texto del botón y agregue los controladores de eventos durante la <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> eventos.

### <a name="to-initialize-the-data-and-the-controls"></a>Para inicializar los datos y los controles

1. En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **ver código** en el menú contextual.

2. Agregue el código siguiente a la `Sheet1_Startup` método para establecer el texto de los botones.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Solo en C#, agregue controladores de eventos para el botón, haga clic en eventos para el `Sheet1_Startup` método.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregue código para habilitar el desplazamiento por los registros
 Agregue código a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de cada botón para desplazarse por los registros.

### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros

1. Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> událostí `Button1`y agregue el siguiente código para desplazarse hacia atrás por los registros:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> událostí `Button2`y agregue el código siguiente para avanzar por los registros:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Probar la aplicación
 Ahora puede probar su libro para asegurarse de que los datos aparecen como se esperaba y que puede usar la solución sin conexión.

### <a name="to-test-the-data-caching"></a>Para probar el almacenamiento en caché de datos

1. Presione **F5**.

2. Compruebe que el rango con nombre y el objeto de lista se rellenan con datos procedentes del origen de datos.

3. Desplácese por algunos de los registros, haga clic en los botones.

4. Guarde el libro y, a continuación, cierre el libro y Visual Studio.

5. Deshabilitar la conexión a la base de datos. Desconecte el cable de red del equipo si se encuentra la base de datos en un servidor, o detener el servicio de SQL Server si la base de datos se encuentra en el equipo de desarrollo.

6. Abra Excel y, a continuación, abra **mi Master-Detail.xlsx** desde el *\bin* directorio ( *\My Master-Detail\bin* en Visual Basic o *\My Master-Detail\bin\ depurar* en C#).

7. Desplácese por algunos de los registros para ver que la hoja de cálculo funciona normalmente cuando se desconecta.

8. Volver a conectarse a la base de datos. Conectar el equipo a la red de nuevo si la base de datos se encuentra en un servidor o iniciar el servicio de SQL Server si la base de datos se encuentra en el equipo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes
 Este tutorial muestra los conceptos básicos de creación de una relación de datos principal-detalle en una hoja de cálculo y almacenamiento en caché un conjunto de datos. A continuación, podría realizar las siguientes tareas:

- Implementar la solución. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Vea también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Almacenar datos en caché](../vsto/caching-data.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
