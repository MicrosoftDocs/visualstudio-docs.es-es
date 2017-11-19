---
title: "Información general sobre la cinta de opciones | Documentos de Microsoft"
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
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 52583bdbf6edf4f2a698bc8662a0faf659841926
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ribbon-overview"></a>Información general sobre la cinta de opciones
  La cinta es una manera de organizar comandos relacionados para que sean fáciles de encontrar. Los comandos aparecen como controles en la cinta. Los controles se organizan en *grupos* a lo largo de una franja horizontal en el borde superior de una ventana de aplicación. Los grupos relacionados se organizan en pestañas.  
  
 Ahora se puede acceder mediante la cinta a la mayoría de las características a las que se accedía mediante menús y barras de herramientas en versiones anteriores de Microsoft Office System. Para obtener más información, consulte el artículo técnico [Introducción para desarrolladores de la interfaz de usuario de 2007 Microsoft Office System](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>Personalizar la cinta de Microsoft Office  
 Para personalizar la cinta, agregue uno de los siguientes elementos de cinta al proyecto de Office:  
  
-   **Cinta (diseñador Visual)**  
  
-   **Cinta (XML)**  
  
 Por ejemplo, para personalizar la cinta de Excel, agregue un elemento de cinta a un proyecto de complemento de Excel de VSTO.  
  
### <a name="ribbon-visual-designer-item"></a>Elemento de cinta (diseñador visual)  
 El **cinta (diseñador Visual)** elemento proporciona herramientas avanzadas que facilitan el diseño y el desarrollo de una cinta personalizada. Use la **cinta (diseñador Visual)** elemento para personalizar la cinta de opciones de las maneras siguientes:  
  
-   Agregue pestañas personalizadas o integradas a una cinta.  
  
-   Agregue grupos personalizados a una pestaña personalizada o integrada.  
  
    > [!NOTE]  
    >  Una pestaña o grupo integrado es uno que ya existe en la cinta de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel. El **conexiones** grupo es un grupo integrado en la **datos** ficha.  
  
-   Agregue controles personalizados a un grupo personalizado.  
  
-   Agregue controles personalizados a la vista Backstage.  
  
 Para obtener más información acerca de cómo personalizar una cinta de opciones mediante la **cinta (diseñador Visual)** de elemento, vea [Diseñador de la cinta](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Elemento Cinta (XML)  
 Use la **cinta (XML)** elemento si desea personalizar la cinta de opciones de forma que no es compatible con la **cinta (diseñador Visual)** elemento. Use la **cinta (XML)** elemento para personalizar la cinta de opciones de las maneras siguientes:  
  
-   Agregar *integrados* grupos a una ficha personalizada o integrada.  
  
-   Agregue controles integrados a un grupo personalizado.  
  
-   Agregue código personalizado para invalidar los controladores de eventos de los controles integrados.  
  
-   Personalice la barra de herramientas de acceso rápido.  
  
-   Comparta una personalización de cinta entre el complemento de VSTO usando un identificador calificado.  
  
 Para obtener más información acerca de cómo personalizar la cinta de opciones mediante la **cinta (XML)** de elemento, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportar una cinta del diseñador de la cinta al XML de la Cinta  
 Si crea una cinta mediante el Diseñador de la cinta de opciones y, a continuación, decide que desea personalizar la cinta de maneras que el **cinta (diseñador Visual)** elemento no admite, puede exportar la cinta de opciones a XML.  
  
 Visual Studio crea automáticamente un **cinta (XML)** de elemento y rellena el archivo XML de cinta de opciones con los elementos y atributos para cada control en la cinta de opciones.  
  
 No todas las propiedades que se encuentran en el **propiedades** ventana del Diseñador de la cinta se transfieren al archivo XML de cinta de opciones.  Por ejemplo, Visual Studio no exporta el valor de la **imagen** o **texto** propiedad. Eso es porque debe crear un método de devolución de llamada en el archivo de código de la cinta del proyecto exportado para asignar una imagen o establecer el texto de un control. Visual Studio no genera automáticamente métodos de devolución de llamada como parte del proceso de exportación.  
  
 Además, los valores de propiedad predeterminados sin modificar no aparecen en el archivo XML de la cinta resultante.  
  
 Para obtener más información acerca de cómo exportar la cinta de opciones a XML, vea [Cómo: exportar una cinta de opciones desde el Diseñador de la cinta de opciones a XML de cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="updating-the-code"></a>Actualizar el código  
 Se agrega un nuevo archivo de código de la cinta de opciones a **el Explorador de soluciones**. Este archivo contiene la clase XML de la cinta. Debe crear métodos de devolución de llamada en la región `Ribbon Callbacks` de esta clase para controlar las acciones del usuario, como es el hacer clic en un botón. Mueva el código de los controladores de eventos a estos métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta (RibbonX). Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).  
  
 También debe agregar código a la `ThisAddIn`, `ThisWorkbook`, o `ThisDocument` clase que invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML Ribbon a la aplicación de Office.  
  
 Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>Agregar varios elementos de cinta a un proyecto  
 Puede agregar más de un elemento de cinta a un mismo proyecto. Esto resulta útil si desea realizar alguna de las dos tareas indicadas a continuación:  
  
-   Crear cintas de opciones para Outlook *inspectores*. Para obtener más información, consulte [personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un Inspector es una ventana que se abre cuando los usuarios realizan ciertas tareas, como crear un mensaje de correo electrónico.  
  
-   Seleccione qué cinta se mostrará en tiempo de ejecución.  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>Seleccionar qué cintas se mostrarán en tiempo de ejecución.  
 Dado que un proyecto puede contener más de una cinta, puede seleccionar qué cinta se mostrará en tiempo de ejecución.  
  
 Para seleccionar una cinta se mostrará en tiempo de ejecución, invalide el método CreateRibbonExtensibilityObject en el `ThisAddin`, `ThisWorkbook`, o `ThisDocument` clase del proyecto y devuelva la cinta que desea mostrar. En el ejemplo siguiente se comprueba el valor de un campo denominado `myCondition` y se devuelve la cinta adecuada.  
  
> [!NOTE]  
>  La sintaxis utilizada en este ejemplo devuelve una cinta de opciones que se creó mediante la **cinta (diseñador Visual)** elemento. La sintaxis para devolver una cinta que se crea mediante un **cinta (XML)** elemento es ligeramente diferente. Para obtener más información sobre cómo devolver un **cinta (XML)** de elemento, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
 Agregue el código siguiente:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Iniciarse en la personalización de la cinta](../vsto/how-to-get-started-customizing-the-ribbon.md)|Muestra cómo personalizar la cinta de opciones de una aplicación de Microsoft Office, agregue un **cinta (diseñador Visual)** o **cinta (XML)** elemento a un proyecto de Office.|  
|[Diseñador de la cinta](../vsto/ribbon-designer.md)|Describe cómo puede usar el Diseñador de la cinta para agregar pestañas, grupos y controles personalizados a la cinta de una aplicación de Microsoft Office.|  
|[Tutorial: Creación de una pestaña personalizada mediante el diseñador de la cinta](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta mediante el diseñador de la cinta. Puede usar el diseñador de la cinta para agregar y colocar controles en la pestaña personalizada.|  
|[Información general sobre el modelo de objetos para la cinta](../vsto/ribbon-object-model-overview.md)|Proporciona información general sobre el modelo de objetos de diferentes tipos que puede usar para obtener y establecer las propiedades de controles de la cinta en tiempo de ejecución.|  
|[Tutorial: Actualización de los controles de una cinta en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Muestra cómo usar el modelo de objetos de la cinta para actualizar los controles de una cinta después de cargarla en la aplicación de Office.|  
|[Personalización de una cinta para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Proporciona instrucciones para personalizar la cinta en Microsoft Office Outlook.|  
|[Personalización de una cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Proporciona instrucciones para personalizar la cinta en Microsoft Office InfoPath.|  
|[Obtener acceso a la cinta en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)|Indica cómo mostrar, ocultar y modificar la cinta y permitir a los usuarios ejecutar el código desde los controles de un panel de tareas personalizado, un panel de acciones o un área del formulario de Outlook.|  
|[Cómo: Cambiar la posición de una pestaña en la cinta](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Indica cómo cambiar el orden de las pestañas de una cinta.|  
|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|Muestra cómo agregar grupos y controles a una pestaña integrada.|  
|[Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Muestra cómo agregar controles al menú que se abre al hacer clic en el **archivo**.|  
|[Cómo: Agregar un selector de cuadro de diálogo a un grupo de la cinta](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Muestra cómo agregar un selector de cuadro de diálogo a cualquier grupo de una cinta.|  
|[Cómo: Exportar una cinta desde el diseñador de la cinta a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Muestra cómo personalizar la cinta de maneras avanzadas exportando la cinta del diseñador al XML de la cinta.|  
|[XML de la cinta](../vsto/ribbon-xml.md)|Explica cómo personalizar una cinta mediante el XML de la cinta.|  
|[Tutorial: Creación de una pestaña personalizada mediante el diseñador de la cinta](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Muestra cómo crear una pestaña personalizada de la cinta de opciones mediante el uso de la **cinta (XML)** elemento.|  
  
  