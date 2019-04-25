---
title: 'Procedimiento Agregar controles a la vista Backstage '
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: c4241464fe8a43af882fbdbad0f898838e8fd897
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068371"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedimiento Agregar controles a la vista Backstage
  Puede usar el Diseñador de cinta para agregar controles al menú que se abre al hacer clic en el **archivo** ficha. Al ejecutar la aplicación, los controles que agregue a la **archivo** pestaña aparece un grupo denominado **complementos**.

 No se puede colocar controles antes o después de los controles integrados mediante el Diseñador de cinta de opciones en Visual Studio. Un control integrado es un control que ya aparece en la vista Backstage. Si desea colocar controles antes o después de los controles integrados, debe usar un archivo XML de cinta de opciones. Para obtener más información acerca de **cinta (XML)**, consulte [Ribbon XML](../vsto/ribbon-xml.md). Para obtener más información acerca de cómo personalizar la vista Backstage, consulte [Introducción a la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182189) y [personalizar la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Para agregar controles a la vista Backstage

1. Abra el elemento de la cinta de opciones en la vista Diseño.

     Para obtener información sobre cómo agregar un **cinta (diseñador Visual)** elemento al proyecto, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. En el Diseñador de cinta de opciones, haga clic en el **archivo** ficha.

     Aparece un diseñador de menús. Esta superficie de diseño no contiene todos los controles.

3. Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre cualquiera de los siguientes controles en el Diseñador de menús:

    - Botón

    - CheckBox

    - Galería

    - Menú

    - Separador

    - SplitButton

    - ToggleButton

4. Arrastre controles para moverlos a nuevas posiciones en el menú.

## <a name="see-also"></a>Vea también
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Cómo: Empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
