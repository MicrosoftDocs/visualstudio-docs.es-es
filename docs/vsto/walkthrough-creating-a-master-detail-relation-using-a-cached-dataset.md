---
title: Creación de una relación de detalle maestra mediante el conjunto de datos almacenado en caché
description: Obtenga información sobre cómo crear una relación de maestro y detalle en una hoja de cálculo y almacenar en caché los datos para que la solución se pueda usar sin conexión.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 177b21e2278153693601adf7b7dc18b751cf184e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824853"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Tutorial: Creación de una relación de detalles maestra mediante un conjunto de datos almacenado en caché
  En este tutorial se muestra cómo crear una relación de maestro y detalle en una hoja de cálculo y almacenar en caché los datos para que la solución se pueda usar sin conexión.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar controles a una hoja de cálculo.

- Configure un conjunto de datos para almacenarlo en caché en una hoja de cálculo.

- Agregue código para habilitar el desplazamiento por los registros.

- Pruebe el proyecto.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a la base de datos de ejemplo SQL Server Northwind. La base de datos puede estar en el equipo de desarrollo o en un servidor.

- Permisos para leer y escribir en la base de datos SQL Server datos.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 En este paso, creará un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **My Master-Detail**( Mis detalles maestros) mediante Visual Basic o C#. Asegúrese de que **está seleccionada la opción Crear** un nuevo documento. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio abre el nuevo libro de Excel en el diseñador y agrega **el proyecto My Master-Detail** a **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Creación del origen de datos
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente.**

4. Seleccione una conexión de datos al ejemplo Northwind SQL Server base de datos o agregue una nueva conexión mediante el **botón Nueva** conexión.

5. Después de seleccionar o crear una conexión, haga clic **en Siguiente.**

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic **en Siguiente.**

7. Expanda el nodo **Tablas** en la ventana **Objetos de base de** datos .

8. Seleccione la **tabla Orders** (Pedidos) y la tabla Order **Details (Detalles del** pedido).

9. Haga clic en **Finalizar**

   El asistente agrega las dos tablas a la **ventana Orígenes de** datos. También agrega un conjunto de datos con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 En este paso, agregará un intervalo con nombre, un objeto de lista y dos botones a la primera hoja de cálculo. En primer lugar, agregue el intervalo con nombre y el objeto de lista desde la ventana **Orígenes** de datos para que se enlazan automáticamente al origen de datos. A continuación, agregue los botones del cuadro **de herramientas**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Para agregar un intervalo con nombre y un objeto de lista

1. Compruebe que el **libro My Master-Detail.xlsx** está abierto en el diseñador Visual Studio, con **Sheet1** mostrado.

2. Abra la **ventana Orígenes de** datos y expanda el **nodo** Pedidos.

3. Seleccione la **columna OrderID** y, a continuación, haga clic en la flecha desplegable que aparece.

4. Haga **clic en NamedRange** en la lista desplegable y arrastre la **columna OrderID** a la **celda A2.**

     Se <xref:Microsoft.Office.Tools.Excel.NamedRange> crea un control denominado en la celda `OrderIDNamedRange` **A2.** Al mismo tiempo, se agregan al proyecto un denominado , un adaptador de tabla y una <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` instancia de <xref:System.Data.DataSet> . El control está enlazado a , que a su <xref:System.Windows.Forms.BindingSource> vez está enlazado a la instancia de <xref:System.Data.DataSet> .

5. Desplácese hacia abajo más allá de las columnas que se encuentran en la **tabla Orders.** En la parte inferior de la lista se encuentra la **tabla Detalles del** pedido; está aquí porque es un elemento secundario de la **tabla Orders.** Seleccione esta **tabla Detalles del** pedido, no la que está en el mismo nivel que la tabla **Orders** y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga **clic en ListObject** en la lista desplegable y arrastre la **tabla OrderDetails** a la **celda A6.**

7. Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado **Order_DetailsListObject** se crea en la **celda A6** y se enlaza a <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Para agregar dos botones

1. En la **pestaña Controles comunes** del Cuadro de **herramientas**, agregue un control a la <xref:System.Windows.Forms.Button> celda **A3** de la hoja de cálculo.

    Este botón se denomina `Button1` .

2. Agregue otro <xref:System.Windows.Forms.Button> control a la celda **B3** de la hoja de cálculo.

    Este botón se denomina `Button2` .

   A continuación, marque el conjunto de datos que se almacenará en caché en el documento.

## <a name="cache-the-dataset"></a>Almacenar en caché el conjunto de datos
 Marque el conjunto de datos que se va a almacenar en caché en el documento haciendo que el conjunto de datos sea público y estableciendo la **propiedad CacheInDocument.**

### <a name="to-cache-the-dataset"></a>Para almacenar en caché el conjunto de datos

1. Seleccione **NorthwindDataSet en** la bandeja de componentes.

2. En la **ventana** Propiedades, cambie la **propiedad Modificadores** a **Público.**

    Los conjuntos de datos deben ser públicos antes de habilitar el almacenamiento en caché.

3. Cambie la **propiedad CacheInDocument** a **True.**

   El siguiente paso consiste en agregar texto a los botones y, en C#, agregar código para enlazar los controladores de eventos.

## <a name="initialize-the-controls"></a>Inicialización de los controles
 Establezca el texto del botón y agregue controladores de eventos durante el <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> evento.

### <a name="to-initialize-the-data-and-the-controls"></a>Para inicializar los datos y los controles

1. En **Explorador de soluciones**, haga clic con el botón derecho **en Sheet1.vb** o **Sheet1.cs** y, a continuación, haga **clic** en Ver código en el menú contextual.

2. Agregue el código siguiente al `Sheet1_Startup` método para establecer el texto de los botones.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet15":::

3. Solo para C#, agregue controladores de eventos para los eventos de clic de botón al `Sheet1_Startup` método .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet16":::

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Agregar código para habilitar el desplazamiento por los registros
 Agregue código al controlador <xref:System.Windows.Forms.Control.Click> de eventos de cada botón para desplazarse por los registros.

### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros

1. Agregue un controlador de eventos para el evento de y agregue el código siguiente para retroceder <xref:System.Windows.Forms.Control.Click> `Button1` por los registros:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet17":::

2. Agregue un controlador de eventos para <xref:System.Windows.Forms.Control.Click> el evento de y agregue el código siguiente para avanzar por los `Button2` registros:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet18":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que los datos aparecen según lo previsto y de que puede usar la solución sin conexión.

### <a name="to-test-the-data-caching"></a>Para probar el almacenamiento en caché de datos

1. Presione **F5**.

2. Compruebe que el intervalo con nombre y el objeto de lista se rellenan con datos del origen de datos.

3. Desplácese por algunos de los registros haciendo clic en los botones.

4. Guarde el libro y, a continuación, cierre el libro y Visual Studio.

5. Deshabilite la conexión a la base de datos. Desconecte el cable de red del equipo si la base de datos se encuentra en un servidor o detenga el servicio SQL Server si la base de datos está en el equipo de desarrollo.

6. Abra Excel y, **a continuación,** abra My Master-Detail.xlsxdesde el *directorio \bin* (*\My Master-Detail\bin* en Visual Basic o *\My Master-Detail\bin\debug* en C#).

7. Desplácese por algunos de los registros para ver que la hoja de cálculo funciona con normalidad cuando está desconectada.

8. Vuelva a conectarse a la base de datos. Conecte de nuevo el equipo a la red si la base de datos se encuentra en un servidor o inicie el servicio SQL Server si la base de datos está en el equipo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos de la creación de una relación de datos maestro/detalle en una hoja de cálculo y el almacenamiento en caché de un conjunto de datos. A continuación, podría realizar las siguientes tareas:

- Implementar la solución. Para más información, consulte [Implementación de una solución de Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Consulte también
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Datos de caché](../vsto/caching-data.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
