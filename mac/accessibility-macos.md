---
title: Uso de las opciones de accesibilidad de macOS
description: Uso de las opciones y características de accesibilidad de macOS, como contraste alto, navegación con el teclado y VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998391"
---
# <a name="accessibility-features-of-macos"></a>Características de accesibilidad de macOS

macOS es un sistema operativo accesible, con una serie de características para ayudar a los usuarios con distintas habilidades. Estas características incluyen un modo de contraste alto, navegación con el teclado y VoiceOver (el lector de pantalla de macOS).

## <a name="enable-accessibility-features"></a>Habilitación de las características de accesibilidad

En Visual Studio para Mac, la compatibilidad con las tecnologías de asistencia está desactivada de manera predeterminada. Para habilitar la compatibilidad con la accesibilidad:

1. Vaya a **Visual Studio (menú)**  > **Preferencias** > **Otros** y seleccione **Accesibilidad**.

1. Active la casilla **Habilitar la accesibilidad**.

   ![Captura de pantalla de las preferencias de accesibilidad, con la opción Habilitar la accesibilidad seleccionada](media/accessibility-preferences.png)

1. Seleccione **Reiniciar Visual Studio** para permitir la compatibilidad con las tecnologías de asistencia de Apple.

Como alternativa, puede usar la línea de comandos para habilitar las características de accesibilidad. Para ello, especifique el comando siguiente en el terminal:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Después de cambiar esta configuración a través de la línea de comandos, tendrá que reiniciar Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Aumento del contraste en macOS

Visual Studio para Mac admite un mejor contraste en macOS, de forma que el contraste de los elementos de la interfaz de usuario aumenta y los contornos están mejor definidos. Para habilitar esta característica:

1. Abra **Preferencias del sistema**.

1. Vaya a **Accesibilidad** y seleccione **Pantalla**.

1. Active la casilla **Aumentar contraste**.
