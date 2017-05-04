---
title: "Informaci&#243;n general sobre la cinta de opciones | Microsoft Docs"
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
  - "Cinta de opciones personalizada, varias cintas de opciones"
  - "personalizar la cinta de opciones, varias cintas de opciones"
  - "Cinta [desarrollo de Office en Visual Studio]"
  - "Cinta [desarrollo de Office en Visual Studio], acerca de la cinta de opciones"
  - "Cinta [desarrollo de Office en Visual Studio], varias cintas de opciones"
  - "barras de herramientas [desarrollo de Office en Visual Studio]"
  - "barras de herramientas [desarrollo de Office en Visual Studio], cinta de opciones"
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Informaci&#243;n general sobre la cinta de opciones
  La cinta es una manera de organizar comandos relacionados para que sean fáciles de encontrar.  Los comandos aparecen como controles en la cinta.  Los controles se organizan en *grupos* a lo largo de una franja horizontal en el borde superior de la ventana de una aplicación.  Los grupos relacionados se organizan en pestañas.  
  
 Ahora se puede acceder mediante la cinta a la mayoría de las características a las que se accedía mediante menús y barras de herramientas en versiones anteriores de Microsoft Office System.  Para obtener más información, vea el artículo técnico [Introducción para desarrolladores a la interfaz de usuario de 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Personalizar la cinta de Microsoft Office  
 Para personalizar la cinta, agregue uno de los siguientes elementos de cinta al proyecto de Office:  
  
-   **Cinta \(diseñador visual\)**  
  
-   **Cinta \(XML\)**  
  
 Por ejemplo, para personalizar la cinta de Excel, agregue un elemento de cinta a un proyecto de complemento de Excel de VSTO.  
  
### Elemento de cinta \(diseñador visual\)  
 El elemento **Cinta \(diseñador visual\)** proporciona herramientas avanzadas que facilitan el diseño y desarrollo de una cinta personalizada.  Use el elemento **Cinta \(diseñador visual\)** para personalizar la cinta de las siguientes maneras:  
  
-   Agregue pestañas personalizadas o integradas a una cinta.  
  
-   Agregue grupos personalizados a una pestaña personalizada o integrada.  
  
    > [!NOTE]  
    >  Una pestaña o grupo integrado es uno que ya existe en la cinta de una aplicación de Microsoft Office.  Por ejemplo, la pestaña **Datos** es una pestaña integrada en Excel.  El grupo **Conexiones** es un grupo integrado en la pestaña **Datos**.  
  
-   Agregue controles personalizados a un grupo personalizado.  
  
-   Agregue controles personalizados a la vista Backstage.  
  
 Para obtener más información acerca de cómo personalizar una cinta mediante el elemento **Cinta \(diseñador visual\)**, vea [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md).  
  
### Elemento Cinta \(XML\)  
 Use el elemento **Cinta \(XML\)** si desea personalizar la cinta de opciones de un modo que el elemento **Cinta \(diseñador visual\)** no admite.  Use el elemento **Cinta \(XML\)** para personalizar la cinta de las siguientes maneras:  
  
-   Agregue grupos *integrados* a una pestaña personalizada o integrada.  
  
-   Agregue controles integrados a un grupo personalizado.  
  
-   Agregue código personalizado para invalidar los controladores de eventos de los controles integrados.  
  
-   Personalice la barra de herramientas de acceso rápido.  
  
-   Comparta una personalización de cinta entre el complemento de VSTO usando un identificador calificado.  
  
 Para obtener más información acerca de cómo personalizar la cinta mediante el elemento **Cinta \(XML\)**, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
## Exportar una cinta del diseñador de la cinta al XML de la Cinta  
 Si crea una cinta mediante el diseñador de la cinta y, a continuación, decide que desea personalizar la cinta de maneras que no admite el elemento **Cinta \(diseñador visual\)**, puede exportar la cinta a XML.  
  
 Visual Studio crea automáticamente un elemento **Cinta \(XML\)** y rellena el archivo XML de la cinta con elementos y atributos para cada control de la cinta.  
  
 No todas las propiedades que se encuentran en la ventana **Propiedades** del diseñador de la cinta se transfieren al archivo XML de la cinta.  Por ejemplo, Visual Studio no exporta el valor de la propiedad **Imagen** o **Texto**.  Eso es porque debe crear un método de devolución de llamada en el archivo de código de la cinta del proyecto exportado para asignar una imagen o establecer el texto de un control.  Visual Studio no genera automáticamente métodos de devolución de llamada como parte del proceso de exportación.  
  
 Además, los valores de propiedad predeterminados sin modificar no aparecen en el archivo XML de la cinta resultante.  
  
 Para obtener más información acerca de cómo exportar la cinta a XML, vea [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### Actualizar el código  
 Se agrega un nuevo archivo de código de cinta al **Explorador de soluciones**.  Este archivo contiene la clase XML de la cinta.  Debe crear métodos de devolución de llamada en la región `Ribbon Callbacks` de esta clase para controlar las acciones del usuario, como es el hacer clic en un botón.  Mueva el código de los controladores de eventos a estos métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta \(RibbonX\).  Para obtener más información, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
 También debe agregar código a la clase `ThisAddIn`, `ThisWorkbook` o `ThisDocument` que invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML de la cinta a la aplicación de Office.  
  
 Para obtener más información, consulte [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
## Agregar varios elementos de cinta a un proyecto  
 Puede agregar más de un elemento de cinta a un mismo proyecto.  Esto resulta útil si desea realizar alguna de las dos tareas indicadas a continuación:  
  
-   Crear cintas para los *Inspectores* de Outlook.   Para obtener más información, vea [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un Inspector es una ventana que se abre cuando los usuarios realizan ciertas tareas, como crear un mensaje de correo electrónico.  
  
-   Seleccione qué cinta se mostrará en tiempo de ejecución.  
  
### Seleccionar qué cintas se mostrarán en tiempo de ejecución.  
 Dado que un proyecto puede contener más de una cinta, puede seleccionar qué cinta se mostrará en tiempo de ejecución.  
  
 Para seleccionar una cinta para que se muestre en tiempo de ejecución, invalide el método CreateRibbonExtensibilityObject en la clase `ThisAddin`, `ThisWorkbook` o `ThisDocument` de su proyecto y devuelva la cinta que desee mostrar.  En el ejemplo siguiente se comprueba el valor de un campo denominado `myCondition` y se devuelve la cinta adecuada.  
  
> [!NOTE]  
>  La sintaxis usada en este ejemplo devuelve una cinta que se creó mediante el elemento **Cinta \(diseñador visual\)**.  La sintaxis para devolver una cinta creada mediante un elemento **Cinta \(XML\)** es ligeramente diferente.  Para obtener más información sobre cómo devolver un elemento **Cinta \(XML\)**, consulte [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
 Agregue el código siguiente:  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
### Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)|Muestra cómo personalizar la cinta de una aplicación de Microsoft Office, agregar un elemento **Cinta \(diseñador visual\)** o **Cinta \(XML\)** a un proyecto de Office.|  
|[Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)|Describe cómo puede usar el Diseñador de la cinta para agregar pestañas, grupos y controles personalizados a la cinta de una aplicación de Microsoft Office.|  
|[Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta mediante el diseñador de la cinta.  Puede usar el diseñador de la cinta para agregar y colocar controles en la pestaña personalizada.|  
|[Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md)|Proporciona información general sobre el modelo de objetos de diferentes tipos que puede usar para obtener y establecer las propiedades de controles de la cinta en tiempo de ejecución.|  
|[Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Muestra cómo usar el modelo de objetos de la cinta para actualizar los controles de una cinta después de cargarla en la aplicación de Office.|  
|[Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Proporciona instrucciones para personalizar la cinta en Microsoft Office Outlook.|  
|[Personalizar una Cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Proporciona instrucciones para personalizar la cinta en Microsoft Office InfoPath.|  
|[Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)|Indica cómo mostrar, ocultar y modificar la cinta y permitir a los usuarios ejecutar el código desde los controles de un panel de tareas personalizado, un panel de acciones o un área del formulario de Outlook.|  
|[Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Indica cómo cambiar el orden de las pestañas de una cinta.|  
|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|Muestra cómo agregar grupos y controles a una pestaña integrada.|  
|[Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Muestra cómo agregar controles al menú que se abre al hacer clic en el **Archivo**.|  
|[Cómo: Agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Muestra cómo agregar un selector de cuadro de diálogo a cualquier grupo de una cinta.|  
|[Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Muestra cómo personalizar la cinta de maneras avanzadas exportando la cinta del diseñador al XML de la cinta.|  
|[XML de la cinta de opciones](../vsto/ribbon-xml.md)|Explica cómo personalizar una cinta mediante el XML de la cinta.|  
|[Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta mediante el elemento **Cinta \(XML\)**.|  
  
  