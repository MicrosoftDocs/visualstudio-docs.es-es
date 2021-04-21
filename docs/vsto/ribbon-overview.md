---
title: Información general sobre la cinta de opciones
description: Obtenga información sobre cómo la cinta de opciones es una manera de organizar los comandos relacionados para que sean más fáciles de encontrar y cómo aparecen los comandos como controles en la cinta de opciones.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8920c8a402b4566cf95bb74626171cca833d32de
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825555"
---
# <a name="ribbon-overview"></a>Información general sobre la cinta de opciones
  La cinta de opciones es una manera de organizar los comandos relacionados para que sean más fáciles de encontrar. Los comandos aparecen como controles en la cinta de opciones. Los controles se organizan en *grupos* a lo largo de una franja horizontal en el borde superior de una ventana de aplicación. Los grupos relacionados se organizan en pestañas.

 Ahora se puede acceder a la mayoría de las características a las que se ha accedido mediante menús y barras de herramientas en versiones anteriores del sistema Microsoft Office mediante la cinta de opciones. Para obtener más información, vea el artículo técnico Información general para desarrolladores de la interfaz de usuario para el sistema [de Microsoft Office 2007.](/previous-versions/office/developer/office-2007/aa338198(v=office.12))

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personalización de la Microsoft Office cinta de opciones
 Para personalizar la cinta de opciones, agregue uno de los siguientes elementos de la cinta de opciones al proyecto de Office:

- **Cinta (diseñador visual)**

- **Cinta de opciones (XML)**

  Por ejemplo, para personalizar la cinta de Excel, agregue un elemento de cinta a un proyecto de complemento de Excel de VSTO.

### <a name="ribbon-visual-designer-item"></a>Elemento ribbon (Visual Designer)
 El **elemento Cinta de opciones (Diseñador visual)** proporciona herramientas avanzadas que facilitan el diseño y el desarrollo de una cinta de opciones personalizada. Use el **elemento Ribbon (Visual Designer)** para personalizar la cinta de opciones de las maneras siguientes:

- Agregar pestañas personalizadas o integradas a una cinta de opciones.

- Agregue grupos personalizados a una pestaña personalizada o integrada.

  > [!NOTE]
  > Una pestaña o un grupo integrados es aquel que ya existe en la cinta de opciones de una Microsoft Office aplicación. Por ejemplo, la **pestaña** Datos es una pestaña integrada en Excel. El **grupo Conexiones** es un grupo integrado en la **pestaña** Datos.

- Agregue controles personalizados a un grupo personalizado.

- Agregue controles personalizados a la vista Backstage.

  Para obtener más información sobre cómo personalizar una cinta de opciones mediante el elemento **Cinta de opciones (Diseñador visual),** vea [Diseñador de cinta de opciones](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Elemento de la cinta de opciones (XML)
 Use el **elemento Cinta de opciones (XML)** si desea personalizar la cinta de opciones de una manera que no sea compatible con el elemento Cinta de opciones **(Visual Designer).** Use el **elemento Ribbon (XML)** para personalizar la cinta de opciones de las maneras siguientes:

- Agregue *grupos integrados* a una pestaña personalizada o a una pestaña integrada.

- Agregue controles integrados a un grupo personalizado.

- Agregue código personalizado para invalidar los controladores de eventos de los controles integrados.

- Personalice la barra de herramientas de acceso rápido.

- Comparta una personalización de cinta entre el complemento de VSTO usando un identificador calificado.

  Para obtener más información sobre cómo personalizar la cinta de opciones mediante el elemento **Ribbon (XML),** vea RIBBON [XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportación de una cinta de opciones desde el Diseñador de la cinta de opciones a XML de la cinta
 Si crea una cinta de opciones mediante el Diseñador de la cinta de opciones y, a continuación, decide que quiere personalizar la cinta de opciones de maneras que el elemento Cinta **de opciones (Visual Designer)** no admite, puede exportar la cinta a XML.

 Visual Studio crea automáticamente un elemento de cinta **de opciones (XML)** y rellena el archivo XML de la cinta de opciones con elementos y atributos para cada control de la cinta.

 No todas las propiedades que se encuentran en la ventana **Propiedades** del Diseñador de la cinta de opciones se transfieren al archivo XML de la cinta de opciones.  Por ejemplo, Visual Studio no exporta el valor de la **propiedad Image** o **Text.** Eso es porque debe crear un método de devolución de llamada en el archivo de código de la cinta del proyecto exportado para asignar una imagen o establecer el texto de un control. Visual Studio no genera automáticamente métodos de devolución de llamada como parte del proceso de exportación.

 Además, los valores de propiedad predeterminados sin modificar no aparecen en el archivo XML de la cinta resultante.

 Para obtener más información sobre cómo exportar la cinta de opciones a XML, vea [How to: Export a ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Actualización del código
 Se agrega un nuevo archivo de código de la cinta de **opciones Explorador de soluciones**. Este archivo contiene la clase XML de la cinta. Debe crear métodos de devolución de llamada en la región `Ribbon Callbacks` de esta clase para controlar las acciones del usuario, como es el hacer clic en un botón. Mueva el código de los controladores de eventos a estos métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta (RibbonX). Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

 También debe agregar código a la clase `ThisAddIn`, `ThisWorkbook` o `ThisDocument` que invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML de la cinta a la aplicación de Office.

 Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Agregar varios elementos de la cinta de opciones a un proyecto
 Puede agregar más de un elemento de cinta a un mismo proyecto. Esto resulta útil si desea realizar alguna de las dos tareas indicadas a continuación:

- Cree cintas de opciones para *los inspectores de* Outlook. Para obtener más información, vea [Personalizar una cinta de opciones para Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

    > [!NOTE]
    > Un Inspector es una ventana que se abre cuando los usuarios realizan ciertas tareas, como crear un mensaje de correo electrónico.

- Seleccione la cinta de opciones que se va a mostrar en tiempo de ejecución.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Selección de las cintas de opciones que se mostrarán en tiempo de ejecución
 Dado que un proyecto puede contener más de una cinta de opciones, puede seleccionar la cinta que se va a mostrar en tiempo de ejecución.

 Para seleccionar una cinta de opciones para mostrar en tiempo de ejecución, invalide el método de la clase , o del proyecto y devuelva la cinta de `CreateRibbonExtensibilityObject` `ThisAddin` opciones que desea `ThisWorkbook` `ThisDocument` mostrar. En el ejemplo siguiente se comprueba el valor de un campo denominado `myCondition` y se devuelve la cinta de opciones adecuada.

> [!NOTE]
> La sintaxis usada en este ejemplo devuelve una cinta de opciones que se creó mediante el elemento **Ribbon (Visual Designer).** La sintaxis para devolver una cinta de opciones que se crea mediante un elemento **de cinta de opciones (XML)** es ligeramente diferente. Para obtener más información sobre cómo devolver **un elemento de la cinta de opciones (XML),** vea XML de la cinta de [opciones](../vsto/ribbon-xml.md).

 Agregue el siguiente código:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)|Muestra cómo personalizar la cinta de opciones de una aplicación Microsoft Office, agregar un elemento **Ribbon (Visual Designer)** o **Ribbon (XML)** a un proyecto de Office.|
|[Diseñador de cinta de opciones](../vsto/ribbon-designer.md)|Describe cómo puede usar el Diseñador de cinta de opciones para agregar pestañas, grupos y controles personalizados a la cinta de opciones de una Microsoft Office personalizada.|
|[Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta mediante el diseñador de la cinta. Puede usar el diseñador de la cinta para agregar y colocar controles en la pestaña personalizada.|
|[Información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md)|Proporciona información general sobre el modelo de objetos de diferentes tipos que puede usar para obtener y establecer las propiedades de controles de la cinta en tiempo de ejecución.|
|[Tutorial: Actualización de los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Muestra cómo usar el modelo de objetos de la cinta para actualizar los controles de una cinta después de cargarla en la aplicación de Office.|
|[Personalización de una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Proporciona instrucciones para personalizar la cinta de opciones Microsoft Office Outlook.|
|[Personalización de una cinta de opciones para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Proporciona instrucciones para personalizar la cinta de opciones Microsoft Office InfoPath.|
|[Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)|Muestra cómo mostrar, ocultar y modificar la cinta de opciones, y cómo permitir que los usuarios ejecuten el código desde controles de un panel de tareas personalizado, un panel de acciones o un área de formulario de Outlook.|
|[Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Muestra cómo cambiar el orden de las pestañas en una cinta de opciones.|
|[Personalización de una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|Muestra cómo agregar grupos y controles a una pestaña integrada.|
|[Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Muestra cómo agregar controles al menú que se abre al hacer clic en **archivo**.|
|[Cómo: Agregar un iniciador de cuadro de diálogo a un grupo de cinta de opciones](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Muestra cómo agregar un iniciador de cuadro de diálogo a cualquier grupo de una cinta de opciones.|
|[Cómo: Exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Muestra cómo personalizar la cinta de opciones de manera avanzada mediante la exportación de la cinta desde el diseñador al XML de la cinta de opciones.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Explica cómo puede personalizar una cinta de opciones mediante XML de cinta de opciones.|
|[Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el elemento **Cinta de opciones (XML).**|
