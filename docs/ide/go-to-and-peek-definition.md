---
title: Visualización de definiciones de tipo
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7b159eb48e995fa0bca6ea86299d09c1a10cf27
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062087"
---
# <a name="view-type-and-member-definitions"></a>Vista de definiciones de tipo y miembro

Los desarrolladores suelen necesitar ver las definiciones de código fuente para los tipos o miembros de clase que usan en su código. En Visual Studio, las características **Ir a definición** y **Ver la definición** le permiten ver fácilmente la definición de un tipo o miembro. Si el código fuente no está disponible, los metadatos se muestran en su lugar.

## <a name="go-to-definition"></a>Ir a definición

La característica **Ir a definición** va hasta el origen de un tipo o miembro y abre el resultado en una nueva pestaña. Si trabaja con el teclado, coloque el cursor de texto en algún lugar del nombre del símbolo y presione **F12**. Si trabaja con el mouse, seleccione **Ir a definición** en el menú contextual o use la función **Ctrl+clic** descrita en la sección siguiente.

### <a name="ctrl-click-go-to-definition"></a>Ir a definición con Ctrl+clic

En Visual Studio 2017 versión 15.4 hay una manera más fácil de que los usuarios que trabajan con el mouse obtengan acceso rápidamente a **Ir a definición**. Se puede hacer clic en los símbolos si se presiona **Ctrl** y se mantiene el puntero sobre el tipo o miembro. Para desplazarse rápidamente a la definición de un símbolo, presione la tecla **Ctrl** y después haga clic en él. Es así de fácil.

![Animación de clic con el mouse en Ir a definición](../ide/media/click_gotodef.gif)

Para cambiar la tecla modificadora del clic del mouse de **Ir a definición**, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **General** y seleccione **Alt** o **Ctrl+Alt** en el menú desplegable **Usar clave de modificador**. También puede deshabilitar el clic del mouse de **Ir a definición**; para ello, desactive la casilla **Habilitar el clic del mouse para Ir a definición**.

![Habilitación del clic del mouse para Ir a definición](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Definición de Peek

La característica **Ver la definición** le permite obtener una vista previa de la definición de un tipo sin abandonar su ubicación actual en el editor. Si trabaja con el teclado, coloque el cursor de texto en algún lugar del nombre de tipo o miembro y presione **Alt + F12**. Si trabaja con el mouse, puede seleccionar **Ver la definición** en el menú contextual. En Visual Studio 2017 versión 15.4 y posteriores, hay una nueva forma de ver una definición en vista de inspección mediante el mouse. En primer lugar, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **General**. Seleccione la opción **Abrir definición en vista de inspección** y haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.

![Establecer la opción Ver la definición del clic del mouse](../ide/media/editor_options_peek_view.png)

Después, presione **Ctrl** (o la tecla modificadora que esté activada en **Opciones**) y haga clic en el tipo o miembro.

![Animación de Ver la definición](../ide/media/peek_definition.gif)

Si ve otra definición en la ventana emergente, iniciará una ruta de navegación en la que puede desplazarse con los círculos y las flechas que aparecen encima de la ventana emergente.

Para obtener más información, vea [Cómo: Ver y editar código mediante Ver la definición (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Visualización de metadatos como código fuente (C#)

Al ver la definición de tipos o miembros de C# cuyo código fuente no está disponible, en su lugar se muestran los metadatos. Puede ver las declaraciones de los tipos y miembros, pero no sus implementaciones.

Al ejecutar el comando **Ir a definición** o **Ver la definición** para un elemento cuyo código fuente no está disponible, un documento con pestañas que contiene una vista de los metadatos de ese elemento, que se muestra como código fuente, aparece en el editor de código. El nombre del tipo, seguido de **[desde metadatos]**, aparece en la pestaña del documento.

Por ejemplo, si ejecuta el comando **Ir a definición** para <xref:System.Console>, los metadatos de <xref:System.Console> aparecen en el editor de código como código fuente de C#. El código es similar a su declaración, pero no muestra una implementación.

![Metadatos como origen](../ide/media/metadatasource.png)

> [!NOTE]
> Al intentar ejecutar el comando **Ir a definición** o **Ver la definición** para tipos o miembros marcados como internos, Visual Studio no muestra sus metadatos como código fuente, independientemente de si el ensamblado de referencia es de confianza o no.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Visualización de definiciones de origen descompiladas en lugar de metadatos (C#)

Como novedad en Visual Studio 2017, versión 15.6, puede configurar una opción para ver código fuente descompilado al ver la definición de un tipo o un miembro de C# cuyo código fuente no está disponible. Para activar esta característica, elija **Herramientas** > **Opciones** en la barra de menús. A continuación, expanda **Editor de texto** > **C#** > **Opciones avanzadas** y seleccione **Enable navigation to decompiled sources** (Habilitar la navegación a orígenes descompilados).

![Visualización de una definición descompilada](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio reconstruye cuerpos de método con la descompilación ILSpy. La primera vez que acceda a esta característica, debe aceptar un aviso legal sobre la licencia de software y el copyright y las leyes sobre marcas comerciales.

## <a name="see-also"></a>Vea también

- [Navegación en el código](../ide/navigating-code.md)
- [Cómo: Ver y editar código mediante Ver la definición (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)