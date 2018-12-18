---
title: 'Cómo: personalizar una pestaña integrada'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257272"
---
# <a name="how-to-customize-a-built-in-tab"></a>Cómo: personalizar una pestaña integrada
  Puede agregar grupos y controles a una pestaña integrada. Una pestaña integrada es una pestaña que ya existe en la cinta de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel. Al crear un grupo personalizado, este aparece al final de la pestaña, pero puede colocarlo en la parte que quiera de la pestaña.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Puede agregar grupos a una pestaña integrada, pero no puede quitar grupos integrados de una pestaña integrada.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Para agregar grupos a una pestaña integrada  
  
1.  Haga clic en el archivo de código de la cinta de opciones en **el Explorador de soluciones**y, a continuación, haga clic en **Diseñador de vistas**.  
  
    > [!NOTE]  
    >  Si el archivo de código de la cinta de opciones no aparece en **el Explorador de soluciones**, debe agregar un **elemento cinta** al proyecto. Consulte [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Haga clic en cualquier pestaña en el Diseñador de cinta de opciones y, a continuación, haga clic en **propiedades**.  
  
3.  En el **propiedades** ventana, expanda el **ControlId** propiedad y, a continuación, establezca el **ControlIdType** propiedad **Office**.  
  
4.  Establecer el **OfficeId** propiedad a la *Id. de control* de la pestaña integrada que desea personalizar.  
  
     El identificador de control es el nombre que identifica de forma única a las fichas, grupos y controles que se integran en las aplicaciones de Microsoft Office.  
  
     Para obtener una lista de identificadores de control, vea [los archivos de Ayuda de Office 2010: identificadores de control de interfaz de usuario fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre los grupos a la pestaña.  
  
    > [!NOTE]  
    >  Los grupos integrados no aparecen en el diseñador. Por lo tanto, la única manera de determinar si está trabajando con una pestaña integrada es examinar el **ControlId** propiedad de la pestaña.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Para colocar grupos en una pestaña integrada  
  
1.  En el diseñador de la cinta, seleccione un grupo personalizado.  
  
2.  En el **propiedades** ventana, expanda el **posición** propiedad.  
  
3.  Establecer el **PositionType** propiedad en el valor adecuado:  
  
    -   **BeforeOfficeId** coloca el grupo antes de un grupo integrado especificado.  
  
    -   **AfterOfficeId** coloca el grupo después de un grupo integrado especificado.  
  
4.  Establecer el **OfficeId** propiedad para el identificador de control de un grupo integrado.  
  
     Para obtener una lista de identificadores de control, vea [los archivos de Ayuda de Office 2010: identificadores de control de interfaz de usuario fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cómo: agregar en Mostrar errores de interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  