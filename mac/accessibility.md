---
title: Accesibilidad
description: Este artículo presenta las características de accesibilidad de Visual Studio para Mac y cómo pueden habilitarse.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 13b8d40a6ab31d7178e95a3896afa1c85c804f6c
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787641"
---
# <a name="accessibility"></a>Accesibilidad

Visual Studio para Mac tiene las características de accesibilidad siguientes, con las que es más accesible para personas con capacidades diferentes:

- Ampliación de texto de los paneles de soluciones y de editores
- Opciones de tamaño de texto en los editores
- Personalización de colores en los editores
- Navegación mediante teclado
- Personalización de métodos abreviados de teclado
- Completado de código para métodos y parámetros

Además de estas características, Apple ofrece una serie de herramientas para ayudar a los usuarios con necesidades especiales, como VoiceOver y Dictado.

Para más información acerca de las características de accesibilidad de macOS, consulte el [sitio web de Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Habilitación de las tecnologías de asistencias de macOS en Visual Studio para Mac

La compatibilidad de Visual Studio para Mac con las tecnologías de asistencia de macOS está deshabilitada de manera predeterminada. Para habilitar, siga estos pasos:

1. Vaya a **Visual Studio (menú) > Preferencias > Otros > Accesibilidad**

2. Active la casilla **Habilitar accesibilidad**:

   ![Casilla de preferencias de accesibilidad](media/accessibility-preferences.png)

3. Seleccione el botón **Reiniciar Visual Studio** para reiniciar Visual Studio y habilitar la compatibilidad con las tecnologías de asistencia de Apple.

## <a name="how-to-use-keyboard-navigation"></a>Procedimiento Uso de la navegación mediante el teclado

La compatibilidad con navegación mediante el teclado está integrada directamente en macOS pero, para tener la experiencia más completa posible, debe establecer que macOS navegue por **Todos los controles**:

![Todos los controles de teclado en las preferencias del sistema](media/accessibility-preferences-keyboard.png)

Establecer **Acceso de teclado completo** en **Todos los controles** permite navegar por todos los controles de una ventana o cuadro de diálogo. Después, se pueden seleccionar los controles mediante:

- Presione la tecla tabulador para avanzar por los controles
- Presione Mayús-Tab para retroceder por los controles
- Teclas de dirección para desplazarse entre los controles en la dirección de las flechas
- Control tabulador para salir de los cuadros de áreas de texto
- Al presionar la barra espaciadora se activa el control actualmente en el foco

## <a name="how-to-enable-and-use-voiceover"></a>Procedimiento Habilitación y uso de VoiceOver

Para habilitar o deshabilitar VoiceOver, presione **&#8984; + F5**

Los comandos de VoiceOver aparecen en esta guía como **VO+_tecla_** , donde **VO** se refiere al modificador establecido en la aplicación **Utilidad VoiceOver**. El modificador predeterminado es **Ctrl + Alt**. Por ejemplo, dependiendo del modificador de VoiceOver que use, **VO + M** significará **Ctrl + Alt + M**. Para no extendernos demasiado, las teclas de dirección se mencionarán como **Izquierda** y **Derecha**, etc.

Para navegar en la interfaz de usuario de Visual Studio para Mac, use estas combinaciones de teclas:

- **VO + Derecha / Izquierda**: Navegación entre los elementos de la interfaz de usuario
  - VoiceOver anunciará la etiqueta y el tipo de control y explicará cómo interactuar con él.
- **VO + Mayús + Abajo / Arriba**: Entrada o salida de un elemento
  - Una vez dentro de un elemento, se puede usar **VO + Izquierda / Derecha** para navegar alrededor de los elementos que están dentro.
- **VO + Espacio**: Selección o interacción con un control
- **VO + M**: Interacción con la barra de menús de Visual Studio para Mac

Para más información sobre el uso de VoiceOver y una lista completa de los comandos, consulte estas guías:

- [Apple VoiceOver Getting Started Guide](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web) (Guía de introducción a Apple VoiceOver)
- [VoiceOver commands in macOS](http://lab.dotjay.com/notes/voiceover-commands/) (Comandos de VoiceOver en macOS)

## <a name="see-also"></a>Vea también

- [Características de accesibilidad de Visual Studio (en Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
