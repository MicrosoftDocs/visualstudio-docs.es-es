---
title: Sugerencias y trucos de accesibilidad de Visual Studio
description: Obtenga más información sobre sugerencias y trucos que pueden ayudar a que el entorno de desarrollo integrado (IDE) de Visual Studio sea más accesible para todos los usuarios, incluidas las personas con discapacidades.
ms.date: 09/15/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6451b45f8bb98232ea0c3a1b3cb96d37cf303ccc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010394"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Sugerencias y trucos de accesibilidad de Visual Studio

> [!TIP]
> Para más información sobre las actualizaciones de accesibilidad recientes, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

Visual Studio tiene características de accesibilidad integradas que son compatibles con los lectores de pantalla y otras tecnologías de asistencia. En este tema se enumeran combinaciones comunes de teclas de método abreviado que puede usar para realizar tareas únicamente con el teclado y se muestra información sobre el uso de temas de alto contraste para mejorar la visibilidad. Además, en el tema se indica cómo usar anotaciones para revelar información útil sobre el código y cómo configurar indicaciones sonoras para eventos de compilación y de punto de interrupción.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Accesibilidad de Visual Studio para Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Guardar la configuración del IDE

 Puede personalizar la experiencia del IDE si guarda el diseño de ventanas, el esquema de asignación de teclado y otras preferencias. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificar el IDE para la visualización de alto contraste

Algunas personas tienen más dificultades para ver ciertos colores. Si necesita más contraste al escribir código pero no quiere usar los típicos temas de "Contraste alto", ofrecemos un tema "Azul (contraste adicional)".

  ![Compare el tema Azul y el tema Azul (contraste adicional)](media/blue-extra-contrast-theme.png)

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Uso de anotaciones para revelar información útil sobre el código

El editor de Visual Studio incluye numerosos elementos gráficos en el texto que le permiten conocer las características y las funciones en puntos concretos de una línea de código, como bombillas, subrayados ondulados de error y advertencia, marcadores, etc. Puede usar el conjunto de comandos "Mostrar anotaciones de línea" para detectar estos elementos gráficos y navegar por ellos.

  ![Use el conjunto de comandos Mostrar anotaciones de línea](media/show-line-annotations-command-set.png)

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Obtener acceso a las barras de herramientas mediante combinaciones de teclas de método abreviado

El IDE de Visual Studio tiene barras de herramientas igual que muchas ventanas de herramientas. Las siguientes combinaciones de teclas de método abreviado le ayudarán a tener acceso a ellas.

|Característica|Descripción|Combinación de teclas|
|-------------|-----------------| - |
|Barras de herramientas del IDE|Seleccionar el primer botón de la barra de herramientas Estándar.|**ALT**, **CTRL** + **TAB**|
|Ventana de herramientas (barras de herramientas)|Mover el foco a las barras de herramientas en una ventana de herramientas. <br> <br> **NOTA:** Esto funciona para la mayoría de ventanas de herramientas, pero solo cuando el foco está en una ventana de herramientas. Además, debe pulsar la tecla MAYÚS antes que la tecla ALT. En algunas ventanas de herramientas, como Team Explorer, debe mantener pulsada la tecla MAYÚS un momento antes de pulsar la tecla ALT.|**MAYÚS** + **ALT**|
|Barras de herramientas|Ir al primer elemento en la siguiente barra de herramientas (cuando una barra de herramientas tiene el foco).|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>Otras combinaciones útiles de teclas de método abreviado

Otras combinaciones útiles de teclas de método abreviado son las siguientes.

|Característica|Descripción|Combinación de teclas|
|-------------|-----------------| - |
|IDE|Activar y desactivar el contraste alto. <br> <br> **NOTA:** Acceso directo estándar de Windows|**ALT izquierda + MAYÚS izquierda + IMPR PANT**|
|Cuadro de diálogo|Activar o desactivar la opción de la casilla de un cuadro de diálogo. <br> <br> **NOTA:** Acceso directo estándar de Windows|**BARRA ESPACIADORA**|
|Menús contextuales|Abrir un menú contextual (clic con el botón derecho). <br> <br> **NOTA:** Acceso directo estándar de Windows|**MAYÚS** + **F10**|
|Menús|Obtener acceso rápidamente a un elemento de menú con sus teclas de aceleración. Pulse la tecla **ALT** seguida de letras subrayadas en un menú para activar el comando. Por ejemplo, para ver el cuadro de diálogo Abrir proyecto en Visual Studio, pulsaría **ALT** + **F** + **O** + **P**.  <br><br> **NOTA:** Acceso directo estándar de Windows|**ALT** + **[letra]**|
|Ventana Cuadro de herramientas|Desplazarse por las pestañas del cuadro de herramientas.|**CTRL** + **FLECHA ARRIBA**<br /><br /> y<br /><br /> **CTRL** + **FLECHA ABAJO**|
|Ventana Cuadro de herramientas|Agregar un control del cuadro de herramientas a un formulario o diseñador.|**ENTRAR**|
|Teclado, Entorno, Opciones (cuadro de diálogo)|Eliminar una combinación de teclas especificada en la opción **Presionar teclas de método abreviado**.|**RETROCESO**|

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Usar el applet Sonido para establecer indicaciones sonoras de compilación y punto de interrupción

Puede usar el applet Sonido en Windows para asignar un sonido a los eventos de programa de Visual Studio. En concreto, puede asignar sonidos a los siguientes eventos de programa:

 * Punto de interrupción alcanzado
 * Compilación cancelada
 * Error de compilación
 * Compilación correcta

Esta es la manera de hacerlo.

1. En el cuadro **Búsqueda** de un equipo con Windows 10, escriba **Cambiar sonidos del sistema**.

   ![Cuadro de búsqueda en Windows 10](media/type-here-to-search.png)

   (O bien, si tiene Cortana habilitado, diga "Hola Cortana" y, después, diga "Cambiar sonidos del sistema").

2. Haga doble clic en **Cambiar sonidos del sistema**.

   ![Resultados de la búsqueda en Windows 10](media/change-system-sounds.png)

3. En el cuadro de diálogo **Sonido**, haga clic en la pestaña **Sonidos**. <br><br>
   Después, en **Eventos de programa**, desplácese hasta **Microsoft Visual Studio** y seleccione los sonidos que quiere aplicar a los eventos seleccionados.

   ![Pestaña Sonido del applet Sonido en Windows 10](media/sound-applet.png)

4. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

* [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Cómo: Personalizar menús y barras de herramientas en Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accesibilidad de Microsoft](https://www.microsoft.com/Accessibility)
* [Accesibilidad (Visual Studio para Mac)](/visualstudio/mac/accessibility)