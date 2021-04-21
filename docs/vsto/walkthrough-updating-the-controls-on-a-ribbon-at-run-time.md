---
title: 'Tutorial: Actualización de los controles de una cinta de opciones en tiempo de ejecución'
description: Obtenga información sobre cómo puede usar el modelo de objetos de la cinta de opciones para actualizar los controles de una cinta de opciones después de cargar la cinta en la aplicación de Office.
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
ms.openlocfilehash: 7cf9bbe73bd43fa01aec8e7d0dec42fd8301ff30
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827531"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Tutorial: Actualización de los controles de una cinta de opciones en tiempo de ejecución

En este tutorial se muestra cómo usar el modelo de objetos de la cinta de opciones para actualizar los controles de una cinta de opciones después de cargar la cinta en la aplicación de Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

En el ejemplo, se extraen los datos de la base de datos de ejemplo Northwind para rellenar un cuadro combinado y un menú en Microsoft Office Outlook. Los elementos seleccionados en estos controles rellenan automáticamente campos como **A** y **Asunto** en un mensaje de correo electrónico.

En este tutorial se muestran las tareas siguientes:

- Cree un nuevo proyecto de complemento de VSTO de Outlook.

- Diseñe un grupo de cinta de opciones personalizado.

- Agregue el grupo personalizado a una pestaña integrada.

- Actualice los controles de la cinta en tiempo de ejecución.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creación de un nuevo proyecto de complemento de VSTO de Outlook

En primer lugar, cree un proyecto de complemento de VSTO de Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de complemento de VSTO de Outlook con el nombre **Ribbon_Update_At_Runtime**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en el directorio de proyecto predeterminado.

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Diseño de un grupo de cinta de opciones personalizado

La cinta de opciones de este ejemplo aparecerá cuando un usuario cree un nuevo mensaje de correo. Para crear un grupo personalizado para la cinta de opciones, agregue primero un elemento de cinta de opciones al proyecto y, a continuación, diseñe el grupo en el Diseñador de la cinta de opciones. Este grupo personalizado le ayudará a generar mensajes de correo electrónico de seguimiento a los clientes mediante la extracción de nombres e historiales de pedidos de una base de datos.

### <a name="to-design-a-custom-group"></a>Para diseñar un grupo personalizado

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.

3. Cambie el nombre de la nueva cinta de opciones a **CustomerRibbon** y, a continuación, haga clic **en Agregar**.

     El *archivo CustomerRibbon.cs* o *CustomerRibbon.vb* se abre en el Diseñador de cinta de opciones y muestra una pestaña y un grupo predeterminados.

4. Haga clic en el Diseñador de la cinta de opciones para seleccionarlo.

5. En la **ventana Propiedades,** haga clic en la flecha desplegable situada junto a la propiedad **RibbonType** y, a continuación, haga clic en **Microsoft.Outlook.Mail.Compose**.

     Esto permite que la cinta de opciones aparezca cuando el usuario crea un nuevo mensaje de correo en Outlook.

6. En el Diseñador de la cinta de opciones, **haga clic en Grupo1** para seleccionarlo.

7. En la **ventana Propiedades,** establezca **Etiqueta en** Compras **del cliente.**

8. En la **pestaña Controles de la cinta de** opciones de Office del Cuadro **de** herramientas, arrastre un **ComboBox** al **grupo Compras del** cliente.

9. Haga **clic en ComboBox1** para seleccionarlo.

10. En la **ventana** Propiedades, establezca **Etiqueta** en **Clientes.**

11. En la **pestaña Controles de la cinta de** opciones de Office **del** Cuadro de herramientas, arrastre un **menú** al grupo **Compras del** cliente.

12. En la **ventana** Propiedades, establezca **Etiqueta** en **Producto comprado.**

13. Establezca **Dinámica en** **true.**

     Esto le permite agregar y quitar controles en el menú en tiempo de ejecución después de cargar la cinta de opciones en la aplicación de Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Agregar el grupo personalizado a una pestaña integrada

Una pestaña integrada es una pestaña que ya está en la cinta de opciones de un Explorador o Inspector de Outlook. En este procedimiento agregará el grupo personalizado a una pestaña integrada y especificará la posición del grupo personalizado en la pestaña.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Para agregar el grupo personalizado a una pestaña integrada

1. Haga clic **en la pestaña Agregar (integrada)** para seleccionarla.

2. En la **ventana** Propiedades, expanda la **propiedad ControlId** y, a continuación, establezca **OfficeId** en **TabNewMailMessage**.

     Esto agrega el **grupo Compras de** clientes a la pestaña **Mensajes** de la cinta de opciones que aparece en un nuevo mensaje de correo.

3. Haga clic en **el grupo Compras de** clientes para seleccionarlo.

4. En la **ventana Propiedades,** expanda la propiedad **Posición,** haga clic en la flecha desplegable situada junto a la **propiedad PositionType** y, a continuación, haga clic **en BeforeOfficeId**.

5. Establezca la **propiedad OfficeId** en **GroupClipboard.**

     Esto coloca el grupo **Compras de clientes** delante del grupo **Portapapeles** de la **pestaña** Mensajes.

## <a name="create-the-data-source"></a>Creación del origen de datos

Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     Esto inicia el Asistente **para configuración del origen de datos**.

2. Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente.**

3. Seleccione **Conjunto de datos** y, a continuación, haga clic en **Siguiente.**

4. Seleccione una conexión de datos al ejemplo Northwind Microsoft SQL Server Compact base de datos 4.0 o agregue una nueva conexión mediante el **botón Nueva** conexión.

5. Después de seleccionar o crear una conexión, haga clic en **Siguiente.**

6. Haga **clic en** Siguiente para guardar la cadena de conexión.

7. En la página **Elegir los objetos de base de** datos , expanda **Tablas**.

8. Active la casilla situada al lado de cada una de las siguientes tablas:

    1. **Clientes**

    2. **Detalles de pedido**

    3. **Órdenes**

    4. **Productos**

9. Haga clic en **Finalizar**

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Actualizar controles del grupo personalizado en tiempo de ejecución

Use el modelo de objetos de la cinta de opciones para llevar a cabo las siguientes tareas:

- Agregue nombres de cliente al **cuadro combinado** Clientes.

- Agregue controles de menú y botón al **menú Productos** comprados que representan pedidos de ventas y productos vendidos.

- Rellene los campos Para, Asunto y Cuerpo de los  nuevos mensajes de correo mediante los datos del cuadro combinado Clientes y **el menú Productos comprados.**

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Para actualizar los controles del grupo personalizado mediante el modelo de objetos de la cinta de opciones

1. En el menú **Proyecto**, haga clic en **Agregar referencia**.

2. En el **cuadro de diálogo** Agregar referencia , haga clic en la pestaña **.NET,** seleccione el ensamblado **System.Data.Linq** y, a continuación, haga clic en **Aceptar.**

    Este ensamblado contiene las clases para usar Language-Integrated Queries (LINQ). Va a usar LINQ para rellenar los controles del grupo personalizado con datos de la base de datos Northwind.

3. En **Explorador de soluciones**, haga **clic en CustomerRibbon.cs** o **CustomerRibbon.vb** para seleccionarlo.

4. En el menú **Ver** , haga clic en **Código**.

    Se abre el archivo de código de la cinta de opciones en el editor de código.

5. Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta. Estas instrucciones proporcionan acceso fácil a los espacios de nombres LINQ y al espacio de nombres del ensamblado de interoperabilidad primario (PIA) de Outlook.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet1":::

6. Agregue el código siguiente dentro de la `CustomerRibbon` clase . Este código declara los adaptadores de tabla y tabla de datos que usará para almacenar la información de las tablas de clientes, pedidos, detalles de pedidos y productos de la base de datos Northwind.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet2":::

7. Agregue el siguiente bloque de código a la clase `CustomerRibbon`. Este código agrega tres métodos auxiliares que crean controles para la cinta de opciones en tiempo de ejecución.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet3":::

8. Reemplace el método del controlador de eventos `CustomerRibbon_Load` por el siguiente código. Este código usa una consulta LINQ para efectuar las siguientes tareas:

   - Rellene el **cuadro combinado** Clientes con el identificador y el nombre de 20 clientes de la base de datos Northwind.

   - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el **menú ProductsPurchased con** números de pedido de ventas que pertenecen al cliente seleccionado actualmente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet4":::

9. Agregue el siguiente código a la clase `CustomerRibbon` . Este código usa consultas LINQ para efectuar las siguientes tareas:

   - Agrega un submenú al **menú ProductsPurchased para** cada pedido de venta relacionado con el cliente seleccionado.

   - Agregar botones a cada submenú para los productos relacionados con el pedido.

   - Agregar controladores de eventos a cada botón.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet6":::

10. En **Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.

     Se abre el Diseñador de la cinta de opciones.

11. En el Diseñador de la cinta de opciones, haga doble clic en el **cuadro combinado** Clientes.

     El archivo de código de la cinta de opciones se abre en el editor de código y aparece el controlador de eventos `ComboBox1_TextChanged`.

12. Reemplace el controlador de eventos `ComboBox1_TextChanged` por el siguiente código: Este código realiza las tareas siguientes:

    - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el **menú Productos comprados** con pedidos de ventas relacionados con el cliente seleccionado.

    - Llama al método del asistente `PopulateMailItem` y pasa el texto actual, que es el nombre del cliente seleccionado. Este método rellena los campos To, Subject y Body de los nuevos mensajes de correo.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet5":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet5":::

13. Agregue el siguiente controlador de eventos `Click` a la clase `CustomerRibbon` . Este código agrega el nombre de los productos seleccionados al campo Cuerpo de los nuevos mensajes de correo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet8":::

14. Agregue el siguiente código a la clase `CustomerRibbon` . Este código realiza las tareas siguientes:

    - Rellena la línea Para de los nuevos mensajes de correo electrónico mediante la dirección de correo electrónico del cliente seleccionado actualmente.

    - Agrega texto a los campos Asunto y Cuerpo de los nuevos mensajes de correo.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet7":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet7":::

## <a name="test-the-controls-in-the-custom-group"></a>Prueba de los controles del grupo personalizado

Al abrir un nuevo formulario de correo en Outlook, aparece un grupo personalizado denominado **Compras de** clientes en la **pestaña** Mensajes de la cinta de opciones.

Para crear un mensaje de correo electrónico de seguimiento del cliente, seleccione un cliente y, a continuación, seleccione los productos adquiridos por el cliente. Los controles del grupo **Compras de** clientes se actualizan en tiempo de ejecución con datos de la base de datos Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Para probar los controles en el grupo personalizado

1. Presione **F5** para ejecutar el proyecto.

     Se inicia Outlook.

2. En Outlook, en el **menú Archivo** , seleccione **Nuevo** y, a continuación, haga clic en Mensaje **de correo**.

     Se producirán las acciones siguientes:

    - Aparece una nueva ventana del inspector de mensajes de correo.

    - En la **pestaña Mensaje** de la cinta de opciones, el grupo **Compras del** cliente aparece delante del grupo **Portapapeles.**

    - El **cuadro** combinado Clientes del grupo se actualiza con los nombres de los clientes de la base de datos Northwind.

3. En la **pestaña Mensaje** de la cinta de opciones, en el grupo **Compras de** clientes, seleccione un cliente en el **cuadro** combinado Clientes.

     Se producirán las acciones siguientes:

    - El **menú Productos comprados** se actualiza para mostrar cada pedido de ventas del cliente seleccionado.

    - Cada submenú del pedido se actualiza para mostrar los productos comprados en ese pedido.

    - La dirección de correo electrónico del cliente seleccionado se agrega a la línea **To** del mensaje de correo y el asunto y el cuerpo del mensaje de correo se rellenan con texto.

4. Haga clic en **el menú Compras de** productos, seleccione cualquier pedido de ventas y, a continuación, haga clic en un producto del pedido de ventas.

     El nombre del producto se agrega al cuerpo del mensaje de correo.

## <a name="next-steps"></a>Pasos siguientes

Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento. Para obtener más información, vea Información [general del panel Acciones.](../vsto/actions-pane-overview.md)

- Extender un formulario estándar o personalizado de Microsoft Office Outlook. Para obtener más información, vea [Tutorial: Diseño de un área de formulario de Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

- Agregar un panel de tareas personalizado a Outlook. Para obtener más información, vea [Paneles de tareas personalizados.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Consulte también

- [Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md)
- [Personalización de una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Personalización de una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: Exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Mostrar errores de la interfaz de usuario del complemento](../vsto/how-to-show-add-in-user-interface-errors.md)