---
title: 'Cómo: personalizar una pestaña integrada'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f73ec7a8555a5e5d569d4316ca619747550bf11
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547191"
---
# <a name="how-to-customize-a-built-in-tab"></a>Cómo: personalizar una pestaña integrada
  Puede agregar grupos y controles a una pestaña integrada. Una pestaña integrada es una pestaña que ya está en la cinta de opciones de una aplicación Microsoft Office. Por ejemplo, la pestaña **datos** es una pestaña integrada en Excel. Al crear un grupo personalizado, este aparece al final de la pestaña, pero puede colocarlo en la parte que quiera de la pestaña.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Puede agregar grupos a una pestaña integrada, pero no puede quitar grupos integrados de una pestaña integrada.

### <a name="to-add-groups-to-a-built-in-tab"></a>Para agregar grupos a una pestaña integrada

1. Haga clic con el botón secundario en el archivo de código de la cinta de **Explorador de soluciones**y, a continuación, haga clic en **Ver diseñador**.

    > [!NOTE]
    > Si el archivo de código de la cinta de opciones no aparece en **Explorador de soluciones**, debe agregar un elemento de la **cinta** de opciones al proyecto. Vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Haga clic con el botón secundario en cualquier pestaña del diseñador de la cinta de opciones y, a continuación, haga clic en **propiedades**.

3. En la ventana **propiedades** , expanda la propiedad **ControlID** y, a continuación, establezca la propiedad **ControlIdType** en **Office**.

4. Establezca la propiedad **OfficeId** en el *identificador de control* de la pestaña integrada que desea personalizar.

     El identificador de control es el nombre que identifica de forma única a las fichas, grupos y controles que se integran en las aplicaciones de Microsoft Office.

     Para obtener una lista de identificadores de control, consulte [archivos de ayuda de office 2010: identificadores de control de la interfaz de usuario de Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

5. En la pestaña controles de la cinta de opciones de **Office** del **cuadro de herramientas**, arrastre grupos a la pestaña.

    > [!NOTE]
    > Los grupos integrados no aparecen en el diseñador. Por lo tanto, la única manera de determinar si está trabajando con una pestaña integrada es examinar la propiedad **ControlID** de la pestaña.

### <a name="to-position-groups-on-a-built-in-tab"></a>Para colocar grupos en una pestaña integrada

1. En el diseñador de la cinta, seleccione un grupo personalizado.

2. En la ventana **propiedades** , expanda la propiedad **posición** .

3. Establezca la propiedad **PositionType** en el valor adecuado:

    - **BeforeOfficeId** coloca el grupo antes de un grupo integrado especificado.

    - **AfterOfficeId** coloca el grupo después de un grupo integrado especificado.

4. Establezca la propiedad **OfficeId** en el identificador de control de un grupo integrado.

     Para obtener una lista de identificadores de control, consulte [archivos de ayuda de office 2010: identificadores de control de la interfaz de usuario de Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Cómo cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: Mostrar errores de la interfaz de usuario de complementos](../vsto/how-to-show-add-in-user-interface-errors.md)
