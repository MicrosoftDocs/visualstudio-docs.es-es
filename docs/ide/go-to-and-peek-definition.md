---
title: "Ir a definición y Ver la definición | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 467d119e67db254b6e15630c08c411bb15283351
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-definition-and-peek-definition"></a>Ir a definición y Ver la definición  
Las características Ir a definición y Ver la definición le permiten ver fácilmente la definición de un tipo o miembro.

## <a name="go-to-definition"></a>Ir a definición  
La característica Ir a definición va hasta el origen de un tipo o miembro y abre el resultado en una nueva pestaña. Si trabaja con el teclado, coloque el cursor de texto en algún lugar del nombre del símbolo y presione **F12**. Si trabaja con el mouse, seleccione **Ir a definición** en el menú contextual o use la función **Ctrl+clic** descrita abajo.  

### <a name="ctrl-click-go-to-definition"></a>Ir a definición con Ctrl+clic  
En Visual Studio 2017 versión 15.4 hay una manera más fácil de que los usuarios que trabajan con el mouse obtengan acceso rápidamente a Ir a definición. Se puede hacer clic en los símbolos si se presiona **Ctrl** y se mantiene el puntero sobre el tipo o miembro. Para desplazarse rápidamente a la definición de un símbolo, presione la tecla **Ctrl** y después haga clic en él. Es así de fácil.

![Animación de clic con el mouse en Ir a definición](../ide/media/click_gotodef.gif)

Puede cambiar la tecla modificadora del clic del mouse de **Ir a definición** si va a **Herramientas**, **Opciones**, **Editor de texto**, **General** y selecciona **Alt** o **Ctrl+Alt** en el menú desplegable **Usar clave de modificador**. También puede deshabilitar el clic del mouse de **Ir a definición**; para ello, desactive la casilla **Habilitar el clic del mouse para Ir a definición**.  

![Habilitación del clic del mouse para Ir a definición](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Ver la definición
La característica Ver la definición le permite obtener una vista previa de la definición de un tipo sin abandonar su ubicación actual en el editor. Si trabaja con el teclado, coloque el cursor de texto en algún lugar del nombre de tipo o miembro y presione **Alt + F12**. Si trabaja con el mouse, puede seleccionar **Ver la definición** en el menú contextual. En Visual Studio 2017 versión 15.4 y posteriores, hay una nueva forma de ver una definición en vista de inspección mediante el mouse. En primer lugar, vaya a **Herramientas**, **Opciones**, **Editor de texto**, **General**. Seleccione la opción **Abrir definición en vista de inspección** y haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  

![Establecer la opción Ver la definición del clic del mouse](../ide/media/editor_options_peek_view.png)  

Después, presione **Ctrl** (o la tecla modificadora que esté activada en **Opciones**) y haga clic en el tipo o miembro.  

![Animación de Ver la definición](../ide/media/peek_definition.gif)

Si ve otra definición de la ventana emergente, iniciará una ruta de navegación en la que puede desplazarse con los círculos y las flechas que aparecen encima de la ventana emergente.  

Para obtener más información, vea [Cómo: Ver y editar código mediante Definición de Peek (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).  

## <a name="see-also"></a>Vea también  
[Navigating Code](../ide/navigating-code.md) (Navegar por el código)  
[Cómo: Ver y editar código mediante Definición de Peek (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
