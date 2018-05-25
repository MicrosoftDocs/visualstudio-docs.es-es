---
title: 'Cómo: agregar controles a la vista Backstage '
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b775c7613b8cc0953e419b2546ec017c96e8454
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Cómo: agregar controles a la vista Backstage
  Puede utilizar el Diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en el **archivo** ficha. Al ejecutar la aplicación, los controles que agregue a la **archivo** ficha aparece un grupo denominado **complementos**.  
  
 No se puede colocar controles antes o después de los controles integrados mediante el Diseñador de la cinta de opciones en Visual Studio. Un control integrado es un control que ya aparece en la vista Backstage. Si desea colocar controles antes o después de los controles integrados, debe usar un XML de cinta de opciones. Para obtener más información acerca de **cinta (XML)**, consulte [XML de cinta de opciones](../vsto/ribbon-xml.md). Para obtener más información acerca de cómo personalizar la vista Backstage, consulte [Introducción a la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182189) y [personalizar la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Para agregar controles a la vista Backstage  
  
1.  Abra el elemento de la cinta de opciones en la vista Diseño.  
  
     Para obtener información sobre cómo agregar un **cinta (diseñador Visual)** elemento al proyecto, vea [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  En el Diseñador de la cinta de opciones, haga clic en el **archivo** ficha.  
  
     Aparece un diseñador de menús. Esta superficie de diseño no contiene todos los controles.  
  
3.  Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre cualquiera de los siguientes controles en el Diseñador de menús:  
  
    -   Botón  
  
    -   CheckBox  
  
    -   Galería  
  
    -   Menú  
  
    -   Separador  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Arrastre controles para moverlos a nuevas posiciones en el menú.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  