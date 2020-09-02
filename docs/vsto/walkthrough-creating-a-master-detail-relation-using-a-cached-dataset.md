---
title: Crear relación de maestro de detalles mediante el conjunto de información en caché
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
ms.openlocfilehash: 0acf84dd983a8c10f2af526ae0bb904eaa90a360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328363"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Tutorial: crear una relación maestra-detalle mediante un conjunto de información almacenado en caché
  En este tutorial se muestra cómo crear una relación principal-detalle en una hoja de cálculo y cómo almacenar en caché los datos para que la solución se pueda usar sin conexión.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar controles a una hoja de cálculo.

- Configure un conjunto de DataSet para que se almacene en caché en una hoja de cálculo.

- Agregue código para habilitar el desplazamiento por los registros.

- Pruebe el proyecto.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a la base de datos de ejemplo Northwind SQL Server. La base de datos puede estar en el equipo de desarrollo o en un servidor.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto
 En este paso, creará un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi maestro-detalle**, mediante Visual Basic o C#. Asegúrese de que **la opción crear un nuevo documento** está seleccionada. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **mi principal-detalle** a **Explorador de soluciones**.

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

8. Seleccione la tabla **pedidos** y la tabla Order **Details** .

9. Haga clic en **Finalizar**

   El asistente agrega las dos tablas a la ventana **orígenes de datos** . También agrega un conjunto de un objeto con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 En este paso, agregará un rango con nombre, un objeto de lista y dos botones a la primera hoja de cálculo. En primer lugar, agregue el rango con nombre y el objeto de lista de la ventana **orígenes de datos** para que se enlacen automáticamente al origen de datos. A continuación, agregue los botones del **cuadro de herramientas**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Para agregar un rango con nombre y un objeto de lista

1. Compruebe que el libro **My Master-Detail.xlsx** está abierto en el diseñador de Visual Studio, donde se muestra **Sheet1** .

2. Abra la ventana **orígenes de datos** y expanda el nodo **pedidos** .

3. Seleccione la columna **OrderID** y, a continuación, haga clic en la flecha desplegable que aparece.

4. Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **OrderID** hasta la celda **a2**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Se crea un control denominado `OrderIDNamedRange` en la celda **a2**. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` <xref:System.Data.DataSet> se agregan al proyecto un denominado, un adaptador de tabla y una instancia de. El control está enlazado a <xref:System.Windows.Forms.BindingSource> , que a su vez se enlaza a la <xref:System.Data.DataSet> instancia de.

5. Desplácese hacia abajo más allá de las columnas que se encuentran debajo de la tabla **Orders** . En la parte inferior de la lista se encuentra la tabla **Order Details** ; está aquí porque es un elemento secundario de la tabla **Orders** . Seleccione esta tabla Order **Details** , no la que se encuentra en el mismo nivel que la tabla **Orders** y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre la tabla **OrderDetails** a la celda **A6**.

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado **Order_DetailsListObject** se crea en la celda **A6**y se enlaza a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Para agregar dos botones

1. En la pestaña **controles comunes** del **cuadro de herramientas**, agregue un <xref:System.Windows.Forms.Button> control a la celda **a3** de la hoja de cálculo.

    Este botón se denomina `Button1` .

2. Agregue otro <xref:System.Windows.Forms.Button> control a la celda **B3** de la hoja de cálculo.

    Este botón se denomina `Button2` .

   A continuación, marque el conjunto de documentos que se va a almacenar en caché en el documento.

## <a name="cache-the-dataset"></a>Almacenar en caché el conjunto de
 Marque el conjunto de documentos que se va a almacenar en caché en el documento; para ello, convierta el conjunto de valores en público y establezca la propiedad **CacheInDocument** .

### <a name="to-cache-the-dataset"></a>Para almacenar en caché el conjunto de

1. Seleccione **NorthwindDataSet** en la bandeja de componentes.

2. En la ventana **propiedades** , cambie la propiedad **Modifiers** a **Public**.

    Los conjuntos de valores deben ser públicos antes de habilitar el almacenamiento en caché.

3. Cambie la propiedad **CacheInDocument** a **true**.

   El siguiente paso consiste en agregar texto a los botones y en C# agregar código para enlazar los controladores de eventos.

## <a name="initialize-the-controls"></a>Inicializar los controles
 Establezca el texto del botón y agregue los controladores de eventos durante el <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento.

### <a name="to-initialize-the-data-and-the-controls"></a>Para inicializar los datos y los controles

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1. VB** o **Sheet1.CS**y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto de los botones.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Solo para C#, agregue controladores de eventos para los eventos de clic de botón al `Sheet1_Startup` método.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregue código para habilitar el desplazamiento por los registros
 Agregue código al <xref:System.Windows.Forms.Control.Click> controlador de eventos de cada botón para desplazarse por los registros.

### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros

1. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento de `Button1` y agregue el código siguiente para desplazarse hacia atrás por los registros:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Agregue un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento de `Button2` y agregue el código siguiente para avanzar por los registros:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que los datos aparecen de la manera esperada y de que puede usar la solución sin conexión.

### <a name="to-test-the-data-caching"></a>Para probar el almacenamiento en caché de datos

1. Presione **F5**.

2. Compruebe que el rango con nombre y el objeto de lista se rellenan con datos del origen de datos.

3. Desplácese por algunos de los registros haciendo clic en los botones.

4. Guarde el libro y, a continuación, cierre el libro y Visual Studio.

5. Deshabilite la conexión a la base de datos. Desconecte el cable de red del equipo si la base de datos se encuentra en un servidor o detenga el servicio de SQL Server si la base de datos está en el equipo de desarrollo.

6. Abra Excel y, a continuación, Abra **My Master-Detail.xlsx** desde el directorio *\Bin* (*\Mis Master-Detail\bin* en Visual Basic o *\Mis Master-Detail\bin\debug* en C#).

7. Desplácese por algunos de los registros para ver que la hoja de cálculo funciona normalmente cuando está desconectada.

8. Vuelva a conectarse a la base de datos. Vuelva a conectar el equipo a la red si la base de datos se encuentra en un servidor o inicie el servicio SQL Server si la base de datos está en el equipo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos de la creación de una relación de datos principal-detalle en una hoja de cálculo y el almacenamiento en caché de un conjunto de datos. A continuación, podría realizar las siguientes tareas:

- Implementar la solución. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md) .

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Datos de caché](../vsto/caching-data.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
