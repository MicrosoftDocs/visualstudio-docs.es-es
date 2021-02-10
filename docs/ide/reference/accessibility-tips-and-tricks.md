---
title: Sugerencias y trucos de accesibilidad de Visual Studio
description: Obtenga más información sobre sugerencias y trucos que pueden ayudar a que el entorno de desarrollo integrado (IDE) de Visual Studio sea más accesible para todos los usuarios, incluidas las personas con discapacidades.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939752"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Sugerencias y trucos de accesibilidad de Visual Studio

Visual Studio tiene características de accesibilidad integradas que son compatibles con los lectores de pantalla y otras tecnologías de asistencia. Si quiere usar métodos abreviados para navegar por el IDE o usar temas de contraste alto para mejorar la visibilidad, en esta página encontrará varias sugerencias y trucos sobre cómo hacerlo.

También se indica cómo usar anotaciones para revelar información útil sobre el código y cómo configurar indicaciones sonoras para eventos de compilación y de punto de interrupción.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Accesibilidad de Visual Studio para Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Guardar la configuración del IDE

Puede personalizar la experiencia del IDE si guarda el diseño de ventanas, el esquema de asignación de teclado y otras preferencias. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificar el IDE para la visualización de alto contraste

Algunas personas tienen más dificultades para ver ciertos colores. Si necesita más contraste al escribir código pero no quiere usar los típicos temas de "Contraste alto", ofrecemos un tema "Azul (contraste adicional)".

  ![Comparación del tema "Azul" y el tema "Azul (contraste adicional)"](media/blue-extra-contrast-theme.png "Captura de pantalla que muestra una comparación del tema "Azul" con el tema "Azul (contraste adicional)"")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Uso de anotaciones para revelar información útil sobre el código

El editor de Visual Studio incluye numerosos "adornos" de texto que permiten conocer las características y las funciones en puntos concretos de una línea de código, como los iconos del destornillador y la bombilla, los subrayados ondulados de errores y advertencias, los marcadores, etc. Puede usar el conjunto de comandos "Mostrar anotaciones de línea" para detectar estos adornos y navegar por ellos.

  ![Uso del conjunto de comandos "Mostrar anotaciones de línea"](media/show-line-annotations-command-set.png "Captura de pantalla del elemento de menú "Mostrar anotaciones de línea"")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Acceso a las barras de herramientas a través de métodos abreviados de teclado

El IDE de Visual Studio tiene barras de herramientas igual que muchas ventanas de herramientas. Los métodos abreviados de teclado siguientes lo ayudan a acceder a ellas.

|Característica|Descripción|Método abreviado de teclado|
|-------------|-----------------| - |
|Barras de herramientas del IDE|Seleccionar el primer botón de la barra de herramientas Estándar.|**Alt**, **Ctrl**+**TAB**|
|Ventana de herramientas (barras de herramientas)|Mover el foco a las barras de herramientas en una ventana de herramientas. <br> <br> **NOTA:** Esto funciona para la mayoría de ventanas de herramientas, pero solo cuando el foco está en una ventana de herramientas. Además, debe pulsar la tecla MAYÚS antes que la tecla ALT. En algunas ventanas de herramientas, como Team Explorer, debe mantener pulsada la tecla MAYÚS un momento antes de pulsar la tecla ALT.|**Mayús**+**Alt**|
|Barras de herramientas|Ir al primer elemento en la siguiente barra de herramientas (cuando una barra de herramientas tiene el foco).|**Ctrl**+**Tab**|

### <a name="other-useful-keyboard-shortcuts"></a>Otros métodos abreviados de teclado útiles

Otros métodos abreviados de teclado útiles incluyen los siguientes.

|Característica|Descripción|Método abreviado de teclado|
|-------------|-----------------| - |
|IDE|Activar y desactivar el contraste alto. <br> <br> **NOTA:** Método abreviado de teclado estándar|**Alt izquierda**+**Mayús izquierda**+**Impr Pant**|
|Cuadro de diálogo|Activar o desactivar la opción de la casilla de un cuadro de diálogo. <br> <br> **NOTA:** Método abreviado de teclado estándar|**Barra espaciadora**|
|Menús contextuales|Abrir un menú contextual (clic con el botón derecho). <br> <br> **NOTA:** Método abreviado de teclado estándar|**Mayús**+**F10**|
|Menús|Obtener acceso rápidamente a un elemento de menú con sus teclas de aceleración. Pulse la tecla **Alt** seguida de letras subrayadas en un menú para activar el comando. Por ejemplo, para ver el cuadro de diálogo Abrir proyecto en Visual Studio, pulsaría **Alt**+**F**+**O**+**P**.  <br><br> **NOTA:** Método abreviado de teclado estándar|**Alt** +  **[letra]**|
|Cuadro de búsqueda|Usar la característica de búsqueda de Visual Studio.|**Ctrl**+**Q**|
|Ventana Cuadro de herramientas|Desplazarse por las pestañas del cuadro de herramientas.|**Ctrl**+**Flecha arriba**<br /><br /> y<br /><br /> **Ctrl**+**Flecha abajo**|
|Ventana Cuadro de herramientas|Agregar un control del cuadro de herramientas a un formulario o diseñador.|**Entrar**|
|Cuadro de diálogo Opciones: Entorno > Teclado|Eliminar una combinación de teclas especificada en la opción **Presionar teclas de método abreviado**.|**Retroceso**|
|Ventana de herramientas Notificaciones|Para abrir la ventana de herramientas Notificaciones, use dos combinaciones de teclas de método abreviado de teclado, una seguida de la otra. Luego, para ver una notificación, use las teclas de dirección para seleccionarla.| **Ctrl**+ **&#92;** , **Ctrl**+**N**|

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Acceso a notificaciones a través de métodos abreviados de teclado

Cuando aparece una notificación en el IDE, a continuación se muestra cómo puede acceder a la ventana Notificaciones a través de métodos abreviados de teclado:

1. En cualquier parte del IDE, presione los dos métodos abreviados de teclado siguientes en secuencia, uno después del otro: **Ctrl**+ **&#92;** y, luego, **Ctrl**+**N**.

   Se abre la ventana **Notificaciones**.

   ![Ventana de herramientas Notificaciones en el IDE de Visual Studio](media/toast-notification.png "Captura de pantalla de la ventana Notificaciones en el IDE de Visual Studio")

1. Use la tecla **TAB** o las teclas de dirección para seleccionar una notificación.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Usar el applet Sonido para establecer indicaciones sonoras de compilación y punto de interrupción

Puede usar el applet Sonido en Windows para asignar un sonido a los eventos de programa de Visual Studio. En concreto, puede asignar sonidos a los siguientes eventos de programa:

* Punto de interrupción alcanzado
* Compilación cancelada
* Error de compilación
* Compilación correcta

Esta es la manera de hacerlo:

1. En el cuadro **Búsqueda** de un equipo con Windows 10, escriba **Cambiar sonidos del sistema**.

   ![Cuadro de búsqueda en Windows 10](media/type-here-to-search.png "Captura de pantalla del cuadro de búsqueda en Windows 10")

   (O bien, si tiene Cortana habilitado, diga "Hola Cortana" y, después, diga "Cambiar sonidos del sistema").

1. Haga doble clic en **Cambiar sonidos del sistema**.

   ![Resultados de la búsqueda en Windows 10](media/change-system-sounds.png "Captura de pantalla de los resultados de la búsqueda "Cambiar sonidos del sistema" en Windows 10")

1. En el cuadro de diálogo **Sonido**, haga clic en la pestaña **Sonidos**.

1. En **Eventos de programa**, desplácese hasta **Microsoft Visual Studio** y, luego, seleccione los sonidos que quiere aplicar a los eventos seleccionados.

   ![Pestaña Sonidos del applet Sonido en Windows 10](media/sound-applet.png "Pestaña Sonido del applet Sonido en Windows 10")

1. Haga clic en **Aceptar**.

::: moniker range="vs-2017"

> [!TIP]
> Para obtener más información sobre las actualizaciones de accesibilidad, vea la entrada de blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Mejoras de accesibilidad en Visual Studio 2017 versión 15.3).

::: moniker-end

## <a name="see-also"></a>Vea también

* [Características de accesibilidad de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Cómo: Personalizar menús y barras de herramientas en Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accesibilidad (Visual Studio para Mac)](/visualstudio/mac/accessibility)
* [Accesibilidad de Microsoft](https://www.microsoft.com/Accessibility)
