---
title: Información general de la cinta de opciones
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8697a49c57840d358eeaa597fe984b6671958b09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446967"
---
# <a name="ribbon-overview"></a>Información general de la cinta de opciones
  La cinta de opciones es una manera de organizar comandos relacionados para que sean fáciles de encontrar. Los comandos aparecen como controles en la cinta de opciones. Los controles se organizan en *grupos* a lo largo de una franja horizontal en el borde superior de una ventana de aplicación. Los grupos relacionados se organizan en pestañas.

 Ahora se puede acceder la mayoría de las características que antes de que se accedía mediante menús y barras de herramientas en versiones anteriores de Microsoft Office system mediante el uso de la cinta de opciones. Para obtener más información, consulte el artículo técnico [Introducción para desarrolladores de la interfaz de usuario de 2007 Microsoft Office system](http://go.microsoft.com/fwlink/?LinkID=70860).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personalizar la cinta de opciones de Microsoft Office
 Para personalizar la cinta de opciones, agregue uno de los siguientes elementos de la cinta de opciones al proyecto de Office:

- **Cinta (diseñador Visual)**

- **Cinta (XML)**

  Por ejemplo, para personalizar la cinta de Excel, agregue un elemento de cinta a un proyecto de complemento de Excel de VSTO.

### <a name="ribbon-visual-designer-item"></a>Elemento cinta (diseñador Visual)
 El **cinta (diseñador Visual)** elemento proporciona herramientas avanzadas que facilitan el diseño y desarrollo de una cinta personalizada. Use la **cinta (diseñador Visual)** elemento para personalizar la cinta de opciones de las maneras siguientes:

- Agregar pestañas personalizadas o integradas a una cinta de opciones.

- Agregue grupos personalizados a una pestaña personalizada o integrada.

  > [!NOTE]
  > Una pestaña integrada o un grupo es uno que ya existe en la cinta de opciones de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel. El **conexiones** grupo es un grupo integrado en el **datos** ficha.

- Agregue controles personalizados a un grupo personalizado.

- Agregue controles personalizados a la vista Backstage.

  Para obtener más información acerca de cómo personalizar una cinta mediante el **cinta (diseñador Visual)** de elemento, vea [Diseñador de cinta](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Elemento cinta (XML)
 Use la **cinta (XML)** del elemento si desea personalizar la cinta de opciones de forma que no es compatible con la **cinta (diseñador Visual)** elemento. Use la **cinta (XML)** elemento para personalizar la cinta de opciones de las maneras siguientes:

- Agregar *integrada* grupos a una pestaña personalizada o integrada.

- Agregue controles integrados a un grupo personalizado.

- Agregue código personalizado para invalidar los controladores de eventos de los controles integrados.

- Personalice la barra de herramientas de acceso rápido.

- Comparta una personalización de cinta entre el complemento de VSTO usando un identificador calificado.

  Para obtener más información acerca de cómo personalizar la cinta de opciones mediante la **cinta (XML)** de elemento, vea [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportar una cinta desde el Diseñador de cinta al XML de cinta
 Si crea una cinta mediante el Diseñador de cinta de opciones y, a continuación, decide que desea personalizar la cinta de maneras que el **cinta (diseñador Visual)** elemento no admite, puede exportar la cinta de opciones a XML.

 Visual Studio crea automáticamente un **cinta (XML)** de elemento y rellena el archivo XML de cinta con elementos y atributos para cada control en la cinta de opciones.

 No todas las propiedades que se encuentran en el **propiedades** ventana del Diseñador de cinta se transfieren al archivo XML de cinta de opciones.  Por ejemplo, Visual Studio no exporta el valor de la **imagen** o **texto** propiedad. Eso es porque debe crear un método de devolución de llamada en el archivo de código de la cinta del proyecto exportado para asignar una imagen o establecer el texto de un control. Visual Studio no genera automáticamente métodos de devolución de llamada como parte del proceso de exportación.

 Además, los valores de propiedad predeterminados sin modificar no aparecen en el archivo XML de la cinta resultante.

 Para obtener más información acerca de cómo exportar la cinta de opciones a XML, vea [Cómo: Exportar una cinta de opciones desde el Diseñador de cinta a cinta XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Actualice el código
 Se agrega un nuevo archivo de código de la cinta de opciones a **el Explorador de soluciones**. Este archivo contiene la clase XML de la cinta. Debe crear métodos de devolución de llamada en la región `Ribbon Callbacks` de esta clase para controlar las acciones del usuario, como es el hacer clic en un botón. Mueva el código de los controladores de eventos a estos métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta (RibbonX). Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

 También debe agregar código a la clase `ThisAddIn`, `ThisWorkbook` o `ThisDocument` que invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML de la cinta a la aplicación de Office.

 Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Agregar varios elementos de la cinta de opciones a un proyecto
 Puede agregar más de un elemento de cinta a un mismo proyecto. Esto resulta útil si desea realizar alguna de las dos tareas indicadas a continuación:

- Crear cintas de opciones para Outlook *inspectores*. Para obtener más información, consulte [personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Un Inspector es una ventana que se abre cuando los usuarios realizan ciertas tareas, como crear un mensaje de correo electrónico.

- Seleccione qué cinta se mostrará en tiempo de ejecución.

### <a name="select-which-ribbons-to-display-at-runtime"></a>Seleccione qué cintas de opciones para mostrar en tiempo de ejecución
 Dado que un proyecto puede contener más de una cinta, puede seleccionar qué cinta se mostrará en tiempo de ejecución.

 Para seleccionar una cinta se mostrará en tiempo de ejecución, invalide el `CreateRibbonExtensibilityObject` método en el `ThisAddin`, `ThisWorkbook`, o `ThisDocument` clase del proyecto y devuelva la cinta que desea mostrar. En el ejemplo siguiente se comprueba el valor de un campo denominado `myCondition` y devuelve la cinta adecuada.

> [!NOTE]
> La sintaxis utilizada en este ejemplo devuelve una cinta de opciones que se creó mediante la **cinta (diseñador Visual)** elemento. La sintaxis para devolver una cinta de opciones que se crea mediante un **cinta (XML)** elemento es ligeramente diferente. Para obtener más información sobre cómo devolver un **cinta (XML)** de elemento, vea [Ribbon XML](../vsto/ribbon-xml.md).

 Agregue el código siguiente:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)|Se muestra cómo personalizar la cinta de opciones de una aplicación de Microsoft Office, agregar un **cinta (diseñador Visual)** o **cinta (XML)** a un proyecto de Office.|
|[Diseñador de cinta](../vsto/ribbon-designer.md)|Describe cómo puede utilizar el Diseñador de cinta de opciones para agregar pestañas personalizadas, grupos y controles a la cinta de opciones de una aplicación de Microsoft Office.|
|[Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta mediante el diseñador de la cinta. Puede usar el diseñador de la cinta para agregar y colocar controles en la pestaña personalizada.|
|[Información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md)|Proporciona información general del modelo de objetos fuertemente tipados que puede usar para obtener y establecer las propiedades de controles de cinta de opciones en tiempo de ejecución.|
|[Tutorial: Actualizar los controles de una cinta en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Muestra cómo usar el modelo de objetos de la cinta para actualizar los controles de una cinta después de cargarla en la aplicación de Office.|
|[Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Proporciona instrucciones para personalizar la cinta de opciones en Microsoft Office Outlook.|
|[Personalizar una cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Proporciona instrucciones para personalizar la cinta de opciones en Microsoft Office InfoPath.|
|[Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)|Se muestra cómo mostrar, ocultar y modificar la cinta de opciones y permitir que los usuarios ejecutar el código desde los controles en un panel de tareas personalizado, un panel de acciones o un formulario de Outlook.|
|[Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Se muestra cómo cambiar el orden de las fichas en una cinta.|
|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|Muestra cómo agregar grupos y controles a una pestaña integrada.|
|[Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Muestra cómo agregar controles al menú que se abre al hacer clic en el **archivo**.|
|[Cómo: Agregar un selector de cuadro de diálogo a un grupo de cinta de opciones](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Muestra cómo para agregar un selector de cuadro de diálogo a cualquier grupo de una cinta.|
|[Cómo: Exportar una cinta desde el Diseñador de cinta al XML de cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Muestra cómo personalizar la cinta de maneras avanzadas exportando la cinta de opciones desde el diseñador al XML de cinta.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Explica cómo puede personalizar una cinta de opciones mediante XML de cinta de opciones.|
|[Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta de opciones mediante la **cinta (XML)** elemento.|
