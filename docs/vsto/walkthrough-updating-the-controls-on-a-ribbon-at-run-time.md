---
title: "Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecuci&#243;n"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controles [desarrollo de Office en Visual Studio], cinta de opciones"
  - "menús dinámicos [desarrollo de Office en Visual Studio]"
  - "Cinta [desarrollo de Office en Visual Studio], controles"
  - "Cinta [desarrollo de Office en Visual Studio], menú dinámico"
  - "Cinta [desarrollo de Office en Visual Studio], actualizar"
  - "actualizar controles de la cinta de opciones"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecuci&#243;n
  En este tutorial se muestra cómo usar el modelo de objetos de la cinta de opciones para actualizar los controles en una cinta después de cargarla en la aplicación de Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 En el ejemplo, se extraen los datos de la base de datos de ejemplo Northwind para rellenar un cuadro combinado y un menú en Microsoft Office Outlook.  Los elementos que se seleccionan en estos controles rellenan automáticamente campos como **Para** y **Asunto** en un mensaje de correo electrónico.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO de Outlook  
  
-   Diseñar un grupo personalizado de la cinta de opciones  
  
-   Agregar el grupo personalizado a una pestaña integrada  
  
-   Actualizar los controles de la cinta de opciones en tiempo de ejecución  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Crear un proyecto de complemento de VSTO de Outlook  
 En primer lugar, cree un proyecto de complemento de VSTO de Outlook.  
  
#### Para crear un proyecto de complemento de VSTO de Outlook  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento de VSTO de Outlook con el nombre Ribbon\_Update\_At\_Runtime.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, seleccione **Crear directorio para la solución**.  
  
3.  Guarde el proyecto en el directorio de proyecto predeterminado.  
  
     Para obtener más información, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Diseñar un grupo personalizado de la cinta de opciones  
 La cinta de opciones de este ejemplo aparecerá cuando un usuario cree un nuevo mensaje de correo electrónico.  Para crear un grupo personalizado en la cinta de opciones, primero agregue un elemento de la cinta de opciones al proyecto y, después, diseñe el grupo en el Diseñador de la cinta de opciones.  Este grupo personalizado ayudará a generar mensajes de correo electrónico de seguimiento para los clientes extrayendo los nombres e historiales de pedidos de una base de datos.  
  
#### Para diseñar un grupo personalizado  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Cinta \(diseñador visual\)**.  
  
3.  Cambie el nombre de la nueva cinta de opciones por **CustomerRibbon** y, después, haga clic en **Agregar**.  
  
     El archivo **CustomerRibbon.cs** o **CustomerRibbon.vb** se abre en el Diseñador de la cinta de opciones y muestra una pestaña y un grupo predeterminados.  
  
4.  Haga clic en el Diseñador de la cinta de opciones para seleccionarlo.  
  
5.  En la ventana **Propiedades**, haga clic en la flecha desplegable situada junto a la propiedad **RibbonType** y, después, haga clic en **Microsoft.Outlook.Mail.Compose**.  
  
     De este modo, la cinta de opciones aparecerá cuando el usuario redacte un nuevo mensaje de correo en Outlook.  
  
6.  En el Diseñador de la cinta de opciones, haga clic en **Grupo1** para seleccionarlo.  
  
7.  En la ventana **Propiedades** , establezca **Etiqueta** en Compras de cliente.  
  
8.  En la pestaña **Controles de la cinta de opciones de Office**  del **Cuadro de herramientas**, arrastre un **ComboBox** hasta el grupo **Compras de cliente**.  
  
9. Haga clic en **ComboBox1** para seleccionarlo.  
  
10. En la ventana **Propiedades**, establezca **Etiqueta** en Clientes.  
  
11. En la pestaña **Controles de la cinta de opciones de Office**  del **Cuadro de herramientas**, arrastre un **Menú** hasta el grupo **Compras de cliente**.  
  
12. En la ventana **Propiedades**, establezca **Etiqueta** en Producto comprado.  
  
13. Establezca **Dinámico** en **true**.  
  
     De este modo, puede agregar y quitar controles del menú en tiempo de ejecución después de que se haya cargado la cinta de opciones en la aplicación de Office.  
  
## Agregar el grupo personalizado a una pestaña integrada  
 Una pestaña integrada es una pestaña que ya está en la cinta de opciones de un inspector o explorador de Outlook.  En este procedimiento agregará el grupo personalizado a una pestaña integrada y especificará la posición del grupo personalizado en la pestaña.  
  
#### Para agregar el grupo personalizado a una pestaña integrada  
  
1.  Haga clic en la pestaña **TabAddins \(Integrado\)** para seleccionarla.  
  
2.  En la ventana **Propiedades**, expanda la propiedad **ControlId** y, después, establezca **OfficeId** en TabNewMailMessage.  
  
     De este modo, se agrega el grupo **Compras del cliente** a la pestaña **Mensajes** de la cinta de opciones que aparece en un nuevo mensaje de correo.  
  
3.  Haga clic en el grupo **Compras del cliente** para seleccionarlo.  
  
4.  En la ventana **Propiedades**, expanda la propiedad **Position**, haga clic en la flecha desplegable situada junto a la propiedad **PositionType** y, después, haga clic en **BeforeOfficeId**.  
  
5.  Establezca la propiedad **OfficeId** en GroupClipboard.  
  
     De este modo, se coloca el grupo **Compras del cliente** delante del grupo **Portapapeles** de la pestaña **Mensajes**.  
  
## Crear el origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Agregar nuevo elemento**.  
  
     Se inicia el **Asistente para la configuración de orígenes de datos**.  
  
2.  Seleccione **Base de datos** y haga clic en **Siguiente**.  
  
3.  Seleccione **Conjunto de datos** y haga clic en **Siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de ejemplo Northwind de Microsoft SQL Server Compact 4.0 o agregue una nueva conexión mediante el botón **Nueva conexión**.  
  
5.  Cuando haya seleccionado o creado una conexión, haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** para guardar la cadena de conexión.  
  
7.  En la página **Elija los objetos de base de datos**, expanda **Tablas**.  
  
8.  Active la casilla situada al lado de cada una de las siguientes tablas:  
  
    1.  **Customers**  
  
    2.  **Detalles del pedido**  
  
    3.  **Pedidos**  
  
    4.  **Productos**  
  
9. Haga clic en **Finalizar**.  
  
## Actualizar los controles del grupo personalizado en tiempo de ejecución  
 Use el modelo de objetos de la cinta de opciones para llevar a cabo las siguientes tareas:  
  
-   Agregar nombres de cliente al cuadro combinado **Clientes**.  
  
-   Agregar controles de menú y de botón al menú **Productos comprados** que representen los pedidos y los productos vendidos.  
  
-   Rellenar los campos To, Subject y Body de los nuevos mensajes de correo usando los datos del cuadro combinado **Clientes** y del menú **Productos comprados**.  
  
#### Para actualizar los controles del grupo personalizado mediante el modelo de objetos de la cinta de opciones  
  
1.  En el menú **Proyecto**, haga clic en **Agregar referencia**.  
  
2.  En el cuadro de diálogo **Agregar referencia**, haga clic en la pestaña **.NET**, seleccione el ensamblado  **System.Data.Linq** y, después, haga clic en **Aceptar**.  
  
     Este ensamblado contiene las clases para usar Language\-Integrated Queries \(LINQ\).  Va a usar LINQ para rellenar los controles del grupo personalizado con datos de la base de datos Northwind.  
  
3.  En el **Explorador de soluciones**, haga clic en el archivo **CustomerRibbon.cs** o **CustomerRibbon.vb** para seleccionarlo.  
  
4.  En el menú **Ver**, haga clic en **Código**.  
  
     Se abre el archivo de código de la cinta de opciones en el editor de código.  
  
5.  Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta de opciones.  Estas instrucciones proporcionan acceso fácil a los espacios de nombres LINQ y al espacio de nombres del ensamblado de interoperabilidad primario \(PIA\) de Outlook.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  Agregue el siguiente código dentro de la clase CustomerRibbon.  Este código declara los adaptadores de tabla y tabla de datos que usará para almacenar la información de las tablas de clientes, pedidos, detalles de pedidos y productos de la base de datos Northwind.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  Agregue el siguiente bloque de código a la clase `CustomerRibbon`.  Este código agrega tres métodos auxiliares que crean los controles para la cinta de opciones en tiempo de ejecución.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  Reemplace el método del controlador de eventos `CustomerRibbon_Load` por el siguiente código.  Este código usa una consulta LINQ para efectuar las siguientes tareas:  
  
    -   Rellenar el cuadro combinado **Clientes** con el identificador y el nombre de 20 clientes de la base de datos Northwind.  
  
    -   Llama al método auxiliar `PopulateSalesOrderInfo`.  Este método actualiza el menú **Productos comprados** con los números de pedido correspondientes al cliente actualmente seleccionado.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. Agregue el código siguiente a la clase `CustomerRibbon`.  Este código usa consultas LINQ para efectuar las siguientes tareas:  
  
    -   Agregar un submenú al menú **Productos comprados** por cada pedido relacionado con el cliente seleccionado.  
  
    -   Agregar botones a cada submenú para los productos relacionados con el pedido.  
  
    -   Agregar controladores de eventos a cada botón.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. En el **Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.  
  
     Se abre el Diseñador de la cinta de opciones.  
  
11. En el Diseñador de la cinta de opciones, haga doble clic en el cuadro combinado **Clientes**.  
  
     El archivo de código de la cinta de opciones se abre en el editor de código y aparece el controlador de eventos `ComboBox1_TextChanged`.  
  
12. Reemplace el controlador de eventos `ComboBox1_TextChanged` por el siguiente código.  Este código realiza las tareas siguientes:  
  
    -   Llama al método auxiliar `PopulateSalesOrderInfo`.  Este método actualiza el menú **Productos comprados** con los pedidos relacionados con el cliente seleccionado.  
  
    -   Llama al método auxiliar `PopulateMailItem` y pasa el texto actual, que es el nombre del cliente seleccionado.  Este método rellena los campos To, Subject y Body de los nuevos mensajes de correo.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. Agregue el siguiente controlador de eventos Click a la clase `CustomerRibbon`.  Este código agrega el nombre de los productos seleccionados al campo Body de los nuevos mensajes de correo.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. Agregue el código siguiente a la clase `CustomerRibbon`.  Este código realiza las tareas siguientes:  
  
    -   Rellena la línea To en los nuevos mensajes de correo con la dirección de correo electrónico del cliente actualmente seleccionado.  
  
    -   Agrega texto a los campos Subject y Body de los nuevos mensajes de correo.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## Probar los controles en el grupo personalizado  
 Cuando abra un nuevo formulario de correo en Outlook, aparecerá el grupo personalizado **Compras del cliente** en la pestaña **Mensajes** de la cinta de opciones.  
  
 Para crear un mensaje de correo electrónico de seguimiento de clientes, seleccione un cliente y, después, seleccione los productos comprados por ese cliente.  Los controles del grupo **Compras del cliente** se actualizan en tiempo de ejecución con los datos de la base de datos Northwind.  
  
#### Para probar los controles en el grupo personalizado  
  
1.  Presione F5 para ejecutar el proyecto.  
  
     Se inicia Outlook.  
  
2.  En Outlook, en el menú **Archivo**, elija **Nuevo** y haga clic en **Mensaje de correo**.  
  
     Se producen las siguientes acciones:  
  
    -   Aparece una nueva ventana del inspector de mensajes de correo.  
  
    -   En la pestaña **Mensaje** de la cinta de opciones, el grupo **Compras del cliente** aparece delante del grupo **Portapapeles**.  
  
    -   El cuadro combinado **Clientes** del grupo se actualiza con los nombres de los clientes en la base de datos Northwind.  
  
3.  En la pestaña **Mensaje** de la cinta de opciones, en el grupo **Compras del cliente**, seleccione un cliente en el cuadro combinado **Clientes**.  
  
     Se producen las siguientes acciones:  
  
    -   El menú **Productos comprados** se actualiza para mostrar cada pedido del cliente seleccionado.  
  
    -   Cada submenú del pedido se actualiza para mostrar los productos comprados en ese pedido.  
  
    -   La dirección de correo electrónico del cliente seleccionado se agrega a la línea **Para** del mensaje de correo, y el asunto y el cuerpo del mensaje de correo se rellenan con texto.  
  
4.  Haga clic en el menú **Productos comprados**, elija cualquier pedido y, después, haga clic en un producto del pedido.  
  
     El nombre del producto se agrega al cuerpo del mensaje de correo.  
  
## Pasos siguientes  
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:  
  
-   Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento.  Para obtener más información, consulte [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
-   Extender un formulario estándar o personalizado de Microsoft Office Outlook.  Para obtener más información, consulte [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Agregar un panel de tareas personalizado a Outlook.  Para obtener más información, consulte [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Language\-Integrated Query \(LINQ\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: Mostrar errores de la interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  