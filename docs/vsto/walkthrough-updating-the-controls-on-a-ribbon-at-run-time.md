---
title: 'Tutorial: Actualizar los controles de una cinta en tiempo de ejecución'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e293a0136e6ae2d8b6a6747201e484fdea43f91e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981119"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Tutorial: Actualizar los controles de una cinta en tiempo de ejecución

Este tutorial muestra cómo utilizar el modelo de objetos de la cinta de opciones para actualizar los controles de una cinta después de carga la cinta de opciones en la aplicación de Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

En el ejemplo, se extraen los datos de la base de datos de ejemplo Northwind para rellenar un cuadro combinado y un menú en Microsoft Office Outlook. Los elementos que se seleccionan en estos controles automáticamente rellenan los campos como **a** y **asunto** en un mensaje de correo electrónico.

En este tutorial se muestran las tareas siguientes:

- Cree un nuevo proyecto de complemento VSTO de Outlook.

- Diseñar un grupo personalizado de la cinta de opciones.

- Agregue el grupo personalizado a una pestaña integrada.

- Actualizar los controles en la cinta de opciones en tiempo de ejecución.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Cree un nuevo proyecto de complemento VSTO de Outlook

En primer lugar, cree un proyecto de complemento de VSTO de Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO de Outlook

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento VSTO de Outlook con el nombre **Ribbon_Update_At_Runtime**.

2. En el cuadro de diálogo **Nuevo proyecto** , seleccione **Crear directorio para la solución**.

3. Guarde el proyecto en el directorio de proyecto predeterminado.

     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Diseñar un grupo personalizado de la cinta de opciones

La cinta de opciones para este ejemplo aparecerá cuando un usuario cree un nuevo mensaje de correo electrónico. Para crear un grupo personalizado de la cinta de opciones, primero agregue un elemento de la cinta de opciones al proyecto y, a continuación, diseñe el grupo en el Diseñador de cinta. Este grupo personalizado ayudará a generar mensajes de correo electrónico de seguimiento a los clientes extrayendo los nombres e historiales de pedidos de una base de datos.

### <a name="to-design-a-custom-group"></a>Para diseñar un grupo personalizado

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.

3. Cambiar el nombre de la nueva cinta de opciones para **CustomerRibbon**y, a continuación, haga clic en **agregar**.

     El *CustomerRibbon.cs* o *CustomerRibbon.vb* archivo se abre en el Diseñador de cinta de opciones y muestra una ficha predeterminada y un grupo.

4. Haga clic en el Diseñador de la cinta de opciones para seleccionarlo.

5. En el **propiedades** ventana, haga clic en la flecha desplegable situada junto a la **RibbonType** propiedad y, a continuación, haga clic en **Microsoft.Outlook.Mail.Compose**.

     Esto permite que la cinta de opciones que aparecen cuando el usuario redacte un nuevo mensaje de correo electrónico en Outlook.

6. En el Diseñador de cinta de opciones, haga clic en **Group1** para seleccionarlo.

7. En el **propiedades** ventana, establezca **etiqueta** a **compras del cliente**.

8. Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre un **ComboBox** hasta la **compras del cliente** grupo.

9. Haga clic en **ComboBox1** para seleccionarlo.

10. En el **propiedades** ventana, establezca **etiqueta** a **clientes**.

11. Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre un **menú** hasta la **compras del cliente** grupo.

12. En el **propiedades** ventana, establezca **etiqueta** a **producto comprado**.

13. Establecer **dinámica** a **true**.

     Esto le permite agregar y quitar controles del menú en tiempo de ejecución después de carga la cinta de opciones en la aplicación de Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Agregar el grupo personalizado a una pestaña integrada

Una pestaña integrada es una ficha que ya está en la cinta de opciones de un Inspector o explorador de Outlook. En este procedimiento agregará el grupo personalizado a una pestaña integrada y especificará la posición del grupo personalizado en la pestaña.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Para agregar el grupo personalizado a una pestaña integrada

1. Haga clic en el **TabAddins (integrado)** tab para seleccionarla.

2. En el **propiedades** ventana, expanda el **ControlId** propiedad y, después, establezca **OfficeId** a **TabNewMailMessage**.

     Esto agrega el **compras del cliente** grupo la **mensajes** pestaña de la cinta de opciones que aparece en un mensaje de correo.

3. Haga clic en el **compras del cliente** grupo para seleccionarlo.

4. En el **propiedades** ventana, expanda el **posición** propiedad, haga clic en la flecha desplegable situada junto a la **PositionType** propiedad y, a continuación, haga clic en  **BeforeOfficeId**.

5. Establecer el **OfficeId** propiedad **GroupClipboard**.

     Esto coloca el **compras del cliente** grupo antes de la **Portapapeles** grupo de la **mensajes** ficha.

## <a name="create-the-data-source"></a>Crear el origen de datos

Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

     Esto inicia el **Asistente para configuración de origen de datos**.

2. Seleccione **base de datos**y, a continuación, haga clic en **siguiente**.

3. Seleccione **Dataset**y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos para la base de datos de Microsoft SQL Server Compact 4.0 de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.

5. Después de haberse seleccionada o creada una conexión, haga clic en **siguiente**.

6. Haga clic en **siguiente** para guardar la cadena de conexión.

7. En el **elija los objetos de base de datos** , expanda **tablas**.

8. Active la casilla situada al lado de cada una de las siguientes tablas:

    1. **Clientes**

    2. **Detalles del pedido**

    3. **Pedidos**

    4. **Productos**

9. Haga clic en **Finalizar**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Actualizar los controles del grupo personalizado en tiempo de ejecución

Use el modelo de objetos de la cinta de opciones para llevar a cabo las siguientes tareas:

- Agregar nombres de los clientes a la **clientes** cuadro combinado.

- Agregar controles de menú y el botón a la **productos comprados** menú que representen los pedidos y productos vendidos.

- Rellenar el para, asunto y cuerpo de los campos de nuevos mensajes de correo mediante el uso de datos de la **clientes** cuadro combinado y **productos comprados** menú.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Para actualizar los controles del grupo personalizado mediante el modelo de objetos de la cinta de opciones

1. En el menú **Proyecto**, haga clic en **Agregar referencia**.

2. En el **Agregar referencia** cuadro de diálogo, haga clic en el **.NET** ficha, seleccione el **System.Data.Linq** ensamblado y, a continuación, haga clic en **Aceptar**.

    Este ensamblado contiene las clases para usar Language-Integrated Queries (LINQ). Va a usar LINQ para rellenar los controles del grupo personalizado con datos de la base de datos Northwind.

3. En **el Explorador de soluciones**, haga clic en **CustomerRibbon.cs** o **CustomerRibbon.vb** para seleccionarlo.

4. En el **vista** menú, haga clic en **código**.

    Se abre el archivo de código de la cinta de opciones en el editor de código.

5. Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta. Estas instrucciones proporcionan acceso fácil a los espacios de nombres LINQ y al espacio de nombres del ensamblado de interoperabilidad primario (PIA) de Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Agregue el código siguiente dentro de la `CustomerRibbon` clase. Este código declara los adaptadores de tabla y tabla de datos que usará para almacenar la información de las tablas de clientes, pedidos, detalles de pedidos y productos de la base de datos Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Agregue el siguiente bloque de código a la clase `CustomerRibbon`. Este código agrega tres métodos auxiliares que crean los controles de la cinta de opciones en tiempo de ejecución.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Reemplace el método del controlador de eventos `CustomerRibbon_Load` por el siguiente código. Este código usa una consulta LINQ para efectuar las siguientes tareas:

   - Rellenar el **clientes** cuadro combinado mediante el identificador y nombre de 20 clientes en la base de datos Northwind.

   - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el **Productoscomprados** menú con los números de pedido de ventas que pertenecen al cliente actualmente seleccionado.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Agregue el código siguiente a la clase `CustomerRibbon` . Este código usa consultas LINQ para efectuar las siguientes tareas:

   - Agregar un submenú a la **Productoscomprados** menú para cada pedido de ventas relacionada con el cliente seleccionado.

   - Agregar botones a cada submenú para los productos relacionados con el pedido.

   - Agregar controladores de eventos a cada botón.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. En **el Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.

     Se abre el Diseñador de la cinta de opciones.

11. En el Diseñador de cinta de opciones, haga doble clic en el **clientes** cuadro combinado.

     El archivo de código de la cinta de opciones se abre en el editor de código y aparece el controlador de eventos `ComboBox1_TextChanged`.

12. Reemplace el controlador de eventos `ComboBox1_TextChanged` por el siguiente código: Este código realiza las tareas siguientes:

    - Llama al método del asistente `PopulateSalesOrderInfo`. Este método actualiza el **productos comprados** menú con los pedidos relacionados con el cliente seleccionado.

    - Llama al método del asistente `PopulateMailItem` y pasa el texto actual, que es el nombre del cliente seleccionado. Este método rellena el para, asunto y cuerpo de los campos de nuevos mensajes de correo.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Agregue el siguiente controlador de eventos `Click` a la clase `CustomerRibbon` . Este código agrega el nombre de los productos seleccionados al campo de cuerpo de nuevos mensajes de correo.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Agregue el código siguiente a la clase `CustomerRibbon` . Este código realiza las tareas siguientes:

    - Rellena la línea para de nuevos mensajes de correo mediante el uso de la dirección de correo electrónico del cliente actualmente seleccionado.

    - Agrega texto a los campos Asunto y cuerpo de nuevos mensajes de correo.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Probar los controles del grupo personalizado

Cuando abre un nuevo formulario de correo electrónico en Outlook, un grupo personalizado denominado **compras del cliente** aparece en el **mensajes** pestaña de la cinta de opciones.

Para crear un mensaje de correo electrónico de seguimiento de cliente, seleccione a un cliente y, a continuación, seleccione los productos comprados por el cliente. Los controles en el **compras del cliente** grupo se actualizan en tiempo de ejecución con los datos de la base de datos Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Para probar los controles en el grupo personalizado

1. Presione **F5** para ejecutar el proyecto.

     Se inicia Outlook.

2. En Outlook, en el **archivo** menú, elija **New**y, a continuación, haga clic en **mensaje de correo electrónico**.

     Se producen las siguientes acciones:

    - Aparece una nueva ventana del inspector de mensajes de correo.

    - En el **mensaje** pestaña de la cinta de opciones, el **compras del cliente** grupo aparece antes de la **Portapapeles** grupo.

    - El **clientes** cuadro combinado en el grupo se actualiza con los nombres de los clientes en la base de datos Northwind.

3. En el **mensaje** pestaña de la cinta de opciones, en el **compras del cliente** grupo, seleccione un cliente en el **clientes** cuadro combinado.

     Se producen las siguientes acciones:

    - El **productos comprados** menú se actualiza para mostrar cada pedido de ventas para el cliente seleccionado.

    - Cada submenú del pedido se actualiza para mostrar los productos comprados en ese pedido.

    - Dirección de correo electrónico del cliente seleccionado se agrega a la **a** línea del mensaje de correo electrónico y el asunto y cuerpo del mensaje de correo se rellenan con texto.

4. Haga clic en el **Products Purchases** menú, elija cualquier pedido de ventas y, a continuación, haga clic en un producto del pedido de ventas.

     El nombre del producto se agrega al cuerpo del mensaje de correo.

## <a name="next-steps"></a>Pasos siguientes

Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento. Para obtener más información, consulte [información general sobre el panel de acciones](../vsto/actions-pane-overview.md).

- Extender un formulario estándar o personalizado de Microsoft Office Outlook. Para obtener más información, vea [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Agregar un panel de tareas personalizado a Outlook. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vea también

- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md)
- [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: Exportar una cinta desde el Diseñador de cinta al XML de cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Mostrar errores de interfaz de usuario del complemento](../vsto/how-to-show-add-in-user-interface-errors.md)