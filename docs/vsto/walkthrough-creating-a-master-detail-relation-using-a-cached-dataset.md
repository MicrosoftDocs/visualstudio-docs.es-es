---
title: "Tutorial: Crear una relación de detalles principal mediante un conjunto de datos almacenado en caché | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 124f4ca6450b5fe19bc707627dfed03e46307cff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Tutorial: Crear a una relación de detalles principal mediante un conjunto de datos almacenados en caché
  Este tutorial muestra cómo crear a una relación principal-detalle en una hoja de cálculo y almacenamiento en caché los datos para que la solución se puede usar sin conexión.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Configurar un conjunto de datos en la memoria caché en una hoja de cálculo.  
  
-   Agregue código para habilitar el desplazamiento por los registros.  
  
-   El proyecto de prueba.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a la base de datos de ejemplo Northwind de SQL Server. La base de datos puede estar en el equipo de desarrollo o en un servidor.  
  
-   Permisos para leer y escribir en la base de datos de SQL Server.  
  
## <a name="creating-a-new-project"></a>Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi principal-detalle**, mediante Visual Basic o C#. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi principal-detalle** proyecto al **el Explorador de soluciones**.  
  
## <a name="creating-the-data-source"></a>Crear el origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.  
  
5.  Después de seleccionar o crear una conexión, haga clic en **siguiente**.  
  
6.  Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7.  Expanda el **tablas** nodo en el **objetos de base de datos** ventana.  
  
8.  Seleccione el **pedidos** tabla y la **Order Details** tabla.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega las dos tablas a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 En este paso, agregará un rango con nombre, un objeto de lista y dos botones a la primera hoja de cálculo. En primer lugar, agregue el rango con nombre y el objeto de lista de la **orígenes de datos** ventana para que se enlazan automáticamente al origen de datos. A continuación, agregue los botones de la **cuadro de herramientas**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>Para agregar un rango con nombre y un objeto de lista  
  
1.  Compruebe que la **mi Master-Detail.xlsx** libro está abierto en el Diseñador de Visual Studio, con **Sheet1** muestra.  
  
2.  Abra la **orígenes de datos** ventana y expanda el **pedidos** nodo.  
  
3.  Seleccione el **OrderID** columna y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
4.  Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre el **OrderID** columna a la celda **A2**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `OrderIDNamedRange` se crea en la celda **A2**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `OrdersBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> instancia se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.  
  
5.  Desplácese hacia abajo más allá de las columnas que se encuentran bajo el **pedidos** tabla. En la parte inferior de la lista es el **Order Details** tabla; está aquí porque es un elemento secundario de la **pedidos** tabla. Seleccione esta opción **Order Details** de tabla, no lo que es el mismo nivel que el **pedidos** de tabla y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
6.  Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre el **OrderDetails** tabla a la celda **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado **Order_DetailsListObject** se crea en la celda **A6**y se enlaza a la <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>Para agregar dos botones  
  
1.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **A3** de la hoja de cálculo.  
  
     Este botón se llamaba `Button1`.  
  
2.  Agregue otro <xref:System.Windows.Forms.Button> control a la celda **B3** de la hoja de cálculo.  
  
     Este botón se llamaba `Button2`.  
  
 A continuación, marque el conjunto de datos en la memoria caché en el documento.  
  
## <a name="caching-the-dataset"></a>Almacenamiento en caché el conjunto de datos  
 Marcar el conjunto de datos en la memoria caché en el documento al hacer que el conjunto de datos públicos y establecer la **CacheInDocument** propiedad.  
  
#### <a name="to-cache-the-dataset"></a>Para almacenar en caché el conjunto de datos  
  
1.  Seleccione **NorthwindDataSet** en la Bandeja de componentes.  
  
2.  En el **propiedades** ventana, cambiar la **modificadores** propiedad **público**.  
  
     Conjuntos de datos deben ser públicos antes de habilita el almacenamiento en caché.  
  
3.  Cambiar el **CacheInDocument** propiedad **True**.  
  
 El siguiente paso es agregar texto a los botones y en C#, agregue código para enlazar los controladores de eventos.  
  
## <a name="initializing-the-controls"></a>Inicializar los controles  
 Establecer el texto del botón y agregue controladores de eventos durante la <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> eventos.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>Para inicializar los datos y los controles  
  
1.  En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el código siguiente a la `Sheet1_Startup` método para establecer el texto de los botones.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Para C# únicamente, agregar controladores de eventos para el botón click (eventos) a la `Sheet1_Startup` método.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Agregar código para habilitar el desplazamiento por los registros  
 Agregue código a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de cada botón para desplazarse por los registros.  
  
#### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros  
  
1.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de `Button1`y agregue el código siguiente para moverse hacia atrás por los registros:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Agregar un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos de `Button2`y agregue el código siguiente para avanzar por los registros:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que los datos aparecen como se esperaba y que puede usar la solución sin conexión.  
  
#### <a name="to-test-the-data-caching"></a>Para probar el almacenamiento en caché de datos  
  
1.  Presione **F5**.  
  
2.  Compruebe que el rango con nombre y el objeto de lista se rellenan con datos del origen de datos.  
  
3.  Desplácese por algunos de los registros, haga clic en los botones.  
  
4.  Guarde el libro y, a continuación, cierre el libro y Visual Studio.  
  
5.  Deshabilitar la conexión a la base de datos. Desconecte el cable de red del equipo si la base de datos se encuentra en un servidor o detener el servicio de SQL Server si la base de datos se encuentra en el equipo de desarrollo.  
  
6.  Abra Excel y, a continuación, abra **mi Master-Detail.xlsx** desde el directorio \bin (\My Master-Detail\bin en Visual Basic o \My Master-Detail\bin\debug en C#).  
  
7.  Desplácese por algunos de los registros para comprobar que la hoja de cálculo funciona normalmente cuando se desconecta.  
  
8.  Volver a conectarse a la base de datos. Conectar el equipo a la red de nuevo si la base de datos se encuentra en un servidor, o iniciar el servicio de SQL Server si la base de datos se encuentra en el equipo de desarrollo.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos de crear una relación de datos principal-detalle en una hoja de cálculo y almacenamiento en caché un conjunto de datos. A continuación, podría realizar las siguientes tareas:  
  
-   Implementar la solución. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  