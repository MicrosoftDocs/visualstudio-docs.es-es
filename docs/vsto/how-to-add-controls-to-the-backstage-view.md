---
title: 'Cómo: agregar controles a la vista backstage '
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b4ea5cdcd869f16f987e9431359511831af9573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538351"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Cómo: agregar controles a la vista backstage
  Puede usar el diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en la pestaña **archivo** . Al ejecutar la aplicación, los controles que se agregan a la pestaña **archivo** muestran un grupo denominado **Complementos**.

 No se pueden colocar controles antes o después de los controles integrados mediante el diseñador de la cinta de opciones en Visual Studio. Un control integrado es un control que ya aparece en la vista backstage. Si desea colocar los controles antes o después de los controles integrados, debe usar un XML de la cinta de opciones. Para obtener más información acerca de **la cinta (XML)**, vea [XML de la cinta](../vsto/ribbon-xml.md). Para obtener más información sobre cómo personalizar la vista backstage, vea [Introducción a la vista backstage de office 2010 para desarrolladores](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) y [Personalización de la vista backstage de Office 2010 para desarrolladores](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Para agregar controles a la vista backstage

1. Abra el elemento de la cinta de opciones en Vista de diseño.

     Para obtener información sobre cómo agregar un elemento **cinta (diseñador visual)** al proyecto, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. En el diseñador de la cinta de opciones, haga clic en la pestaña **archivo** .

     Aparece un diseñador de menús. Esta superficie de diseño no contiene ningún control.

3. En la pestaña controles de la cinta de opciones de **Office** del **cuadro de herramientas**, arrastre cualquiera de los siguientes controles al diseñador de menús:

    - Botón

    - CheckBox

    - Galería

    - Menú

    - Separador

    - SplitButton

    - ToggleButton

4. Arrastre controles para moverlos a nuevas posiciones en el menú.

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
