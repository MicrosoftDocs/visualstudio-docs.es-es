---
title: 'Tutorial: actualizar los controles de una cinta de opciones en tiempo de ejecución'
description: Obtenga información sobre cómo puede usar el modelo de objetos de la cinta de opciones para actualizar los controles de una cinta de opciones después de cargar la cinta de opciones en la aplicación de Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 181fafeb55720b5a97a635a4c2322cf7343643d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937191"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Tutorial: actualizar los controles de una cinta de opciones en tiempo de ejecución

En este tutorial se muestra cómo usar el modelo de objetos de la cinta de opciones para actualizar los controles de una cinta de opciones después de que la cinta de opciones se cargue en la aplicación de Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

En el ejemplo, se extraen los datos de la base de datos de ejemplo Northwind para rellenar un cuadro combinado y un menú en Microsoft Office Outlook. Los elementos que seleccione en estos controles rellenan automáticamente los campos como **para** y el **asunto** en un mensaje de correo electrónico.

En este tutorial se muestran las tareas siguientes:

- Cree un nuevo proyecto de complemento de VSTO de Outlook.

- Diseñar un grupo personalizado de la cinta de opciones.

- Agregue el grupo personalizado a una pestaña integrada.

- Actualizar los controles de la cinta de opciones en tiempo de ejecución.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Crear un nuevo proyecto de complemento de VSTO de Outlook

En primer lugar, cree un proyecto de complemento de VSTO de Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de complemento de VSTO de Outlook con el nombre **Ribbon_Update_At_Runtime**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en el directorio de proyecto predeterminado.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Diseñar un grupo de cinta personalizado

La cinta de opciones de este ejemplo aparecerá cuando un usuario crea un nuevo mensaje de correo. Para crear un grupo personalizado para la cinta de opciones, primero agregue un elemento de la cinta de opciones al proyecto y, a continuación, diseñe el grupo en el diseñador de la cinta de opciones. Este grupo personalizado le ayudará a generar mensajes de correo electrónico de seguimiento a los clientes mediante la extracción de nombres y el historial de pedidos de una base de datos.

### <a name="to-design-a-custom-group"></a>Para diseñar un grupo personalizado

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.

3. Cambie el nombre de la nueva cinta de opciones a **CustomerRibbon** y, a continuación, haga clic en **Agregar**.

     El archivo *CustomerRibbon.CS* o *CustomerRibbon. VB* se abre en el diseñador de la cinta de opciones y muestra una pestaña y un grupo predeterminados.

4. Haga clic en el Diseñador de la cinta de opciones para seleccionarlo.

5. En la ventana **propiedades** , haga clic en la flecha desplegable situada junto a la propiedad **RibbonType** y, a continuación, haga clic en **Microsoft. Outlook. mail. Compose**.

     Esto permite que la cinta de opciones aparezca cuando el usuario crea un nuevo mensaje de correo en Outlook.

6. En el diseñador de la cinta de opciones, haga clic en **Grupo1** para seleccionarlo.

7. En la ventana **propiedades** , establezca **etiqueta** en **compras de cliente**.

8. En la pestaña **controles** de la cinta de opciones de Office del **cuadro de herramientas**, arrastre un **control ComboBox** hasta el grupo de **compras del cliente** .

9. Haga clic en **ComboBox1** para seleccionarlo.

10. En la ventana **propiedades** , establezca **etiqueta** en **Customers**.

11. En la pestaña controles de la cinta de opciones de **Office** del **cuadro de herramientas**, arrastre un **menú** hasta el grupo compras de **cliente** .

12. En la ventana **propiedades** , establezca **etiqueta** en **producto comprado**.

13. Establezca **Dynamic** en **true**.

     Esto le permite agregar y quitar controles en el menú en tiempo de ejecución después de cargar la cinta de opciones en la aplicación de Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Agregar el grupo personalizado a una pestaña integrada

Una pestaña integrada es una pestaña que ya está en la cinta de opciones de un inspector o explorador de Outlook. En este procedimiento agregará el grupo personalizado a una pestaña integrada y especificará la posición del grupo personalizado en la pestaña.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Para agregar el grupo personalizado a una pestaña integrada

1. Haga clic en la pestaña **TabAddins (integrado)** para seleccionarla.

2. En la ventana **propiedades** , expanda la propiedad **ControlID** y, a continuación, establezca **OfficeId** en **TabNewMailMessage**.

     Esto agrega el grupo **compras de cliente** a la pestaña **mensajes** de la cinta de opciones que aparece en un nuevo mensaje de correo.

3. Haga clic en el grupo **compras de cliente** para seleccionarlo.

4. En la ventana **propiedades** , expanda la propiedad **posición** , haga clic en la flecha desplegable situada junto a la propiedad **PositionType** y, a continuación, haga clic en **BeforeOfficeId**.

5. Establezca la propiedad **OfficeId** en **GroupClipboard**.

     Esto coloca el grupo **compras del cliente** antes del grupo **portapapeles** de la pestaña **mensajes** .

## <a name="create-the-data-source"></a>Crear el origen de datos

Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     Esto inicia el **Asistente para la configuración de orígenes de datos**.

2. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

3. Seleccione **DataSet** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos a la base de datos de ejemplo Northwind Microsoft SQL Server Compact 4,0, o bien agregue una nueva conexión mediante el botón **nueva conexión** .

5. Después de seleccionar o crear una conexión, haga clic en **siguiente**.

6. Haga clic en **siguiente** para guardar la cadena de conexión.

7. En la página **Elija los objetos de base de datos** , expanda **tablas**.

8. Active la casilla situada al lado de cada una de las siguientes tablas:

    1. **Compradores**

    2. **Detalles de pedido**

    3. **Orders (Pedidos)**

    4. **Productos**

9. Haga clic en **Finalizar**

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Actualizar los controles del grupo personalizado en tiempo de ejecución

Use el modelo de objetos de la cinta de opciones para llevar a cabo las siguientes tareas:

- Agregue los nombres de cliente al cuadro combinado **clientes** .

- Agregue controles de menú y botón al menú **productos comprados** que representan los pedidos de ventas y productos vendidos.

- Rellene los campos para, asunto y cuerpo de los nuevos mensajes de correo utilizando los datos del cuadro combinado **clientes** y el menú **productos comprados** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Para actualizar los controles del grupo personalizado mediante el modelo de objetos de la cinta de opciones

1. En el menú **Proyecto**, haga clic en **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia** , haga clic en la pestaña **.net** , seleccione el ensamblado **System. Data. Linq** y, a continuación, haga clic en **Aceptar**.

    Este ensamblado contiene las clases para usar Language-Integrated Queries (LINQ). Va a usar LINQ para rellenar los controles del grupo personalizado con datos de la base de datos Northwind.

3. En **Explorador de soluciones**, haga clic en **CustomerRibbon.CS** o **CustomerRibbon. VB** para seleccionarlo.

4. En el menú **Ver** , haga clic en **Código**.

    Se abre el archivo de código de la cinta de opciones en el editor de código.

5. Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta. Estas instrucciones proporcionan acceso fácil a los espacios de nombres LINQ y al espacio de nombres del ensamblado de interoperabilidad primario (PIA) de Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Agregue el código siguiente dentro de la `CustomerRibbon` clase. Este código declara los adaptadores de tabla y tabla de datos que usará para almacenar la información de las tablas de clientes, pedidos, detalles de pedidos y productos de la base de datos Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Agregue el siguiente bloque de código a la clase `CustomerRibbon`. Este código agrega tres métodos auxiliares que crean controles para la cinta de opciones en tiempo de ejecución.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Reemplace el método del controlador de eventos `CustomerRibbon_Load` por el siguiente código. Este código usa una consulta LINQ para efectuar las siguientes tareas:

   - Rellene el cuadro combinado **clientes** usando el identificador y el nombre de 20 clientes en la base de datos Northwind.

   - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el menú **productoscomprados** con los números de pedido de ventas que pertenecen al cliente seleccionado actualmente.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Agregue el siguiente código a la clase `CustomerRibbon` . Este código usa consultas LINQ para efectuar las siguientes tareas:

   - Agrega un submenú al menú **productoscomprados** para cada pedido de ventas relacionado con el cliente seleccionado.

   - Agregar botones a cada submenú para los productos relacionados con el pedido.

   - Agregar controladores de eventos a cada botón.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. En **Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.

     Se abre el Diseñador de la cinta de opciones.

11. En el diseñador de la cinta de opciones, haga doble clic en el cuadro combinado **clientes** .

     El archivo de código de la cinta de opciones se abre en el editor de código y aparece el controlador de eventos `ComboBox1_TextChanged`.

12. Reemplace el controlador de eventos `ComboBox1_TextChanged` por el siguiente código: Este código realiza las tareas siguientes:

    - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el menú **productos comprados** con pedidos de ventas relacionados con el cliente seleccionado.

    - Llama al método del asistente `PopulateMailItem` y pasa el texto actual, que es el nombre del cliente seleccionado. Este método rellena los campos para, asunto y cuerpo de los nuevos mensajes de correo.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Agregue el siguiente controlador de eventos `Click` a la clase `CustomerRibbon` . Este código agrega el nombre de los productos seleccionados al campo de cuerpo de los nuevos mensajes de correo.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Agregue el siguiente código a la clase `CustomerRibbon` . Este código realiza las tareas siguientes:

    - Rellena la línea para de los mensajes de correo nuevos mediante la dirección de correo electrónico del cliente actualmente seleccionado.

    - Agrega texto a los campos asunto y cuerpo de los nuevos mensajes de correo.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Probar los controles del grupo personalizado

Al abrir un nuevo formulario de correo en Outlook, aparece un grupo personalizado denominado **compras de clientes** en la pestaña **mensajes** de la cinta de opciones.

Para crear un mensaje de correo electrónico de seguimiento de cliente, seleccione un cliente y, a continuación, seleccione los productos comprados por el cliente. Los controles del grupo **compras del cliente** se actualizan en tiempo de ejecución con los datos de la base de datos Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Para probar los controles en el grupo personalizado

1. Presione **F5** para ejecutar el proyecto.

     Se inicia Outlook.

2. En Outlook, en el menú **archivo** , seleccione **nuevo** y, a continuación, haga clic en **mensaje de correo**.

     Se producirán las acciones siguientes:

    - Aparece una nueva ventana del inspector de mensajes de correo.

    - En la pestaña **mensaje** de la cinta de opciones, el grupo **compras de cliente** aparece antes del grupo **portapapeles** .

    - El cuadro combinado **clientes** del grupo se actualiza con los nombres de los clientes de la base de datos Northwind.

3. En la pestaña **mensaje** de la cinta de opciones, en el grupo **compras del cliente** , seleccione un cliente en el cuadro combinado **clientes** .

     Se producirán las acciones siguientes:

    - El menú **productos comprados** se actualiza para mostrar cada pedido de venta del cliente seleccionado.

    - Cada submenú del pedido se actualiza para mostrar los productos comprados en ese pedido.

    - La dirección de correo electrónico del cliente seleccionada se agrega a la línea **para** del mensaje de correo, y el asunto y el cuerpo del mensaje de correo se rellenan con texto.

4. Haga clic en el menú **productos compras** , seleccione cualquier pedido de ventas y, a continuación, haga clic en un producto del pedido de venta.

     El nombre del producto se agrega al cuerpo del mensaje de correo.

## <a name="next-steps"></a>Pasos siguientes

Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento. Para obtener más información, vea [información general del panel de acciones](../vsto/actions-pane-overview.md).

- Extender un formulario estándar o personalizado de Microsoft Office Outlook. Para obtener más información, vea [Tutorial: diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Agregar un panel de tareas personalizado a Outlook. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vea también

- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Información general del modelo de objetos de la cinta](../vsto/ribbon-object-model-overview.md)
- [Personalización de una cinta para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Mostrar errores de la interfaz de usuario de complementos](../vsto/how-to-show-add-in-user-interface-errors.md)