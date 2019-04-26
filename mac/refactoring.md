---
title: Refactorización de código
description: Perfeccionamiento del código con Visual Studio para Mac y acciones rápidas.
author: conceptdev
ms.author: crdun
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 48e290fddd1c4b7c95ac5e76cb6cf5908247e6f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937929"
---
# <a name="refactoring"></a>Refactorización

Mediante la refactorización del código, es posible reorganizar, reestructurar y aclarar el código existente garantizando que no cambie el comportamiento general del código.

La refactorización genera un código base más correcto, lo que lo hace mucho más utilizable, legible y fácil de mantener para cualquier desarrollador o usuario que haga referencia al código.

La integración de Visual Studio para Mac con Roslyn, la plataforma de compilador de .NET de código abierto de Microsoft, permite más operaciones de refactorización.

## <a name="renaming"></a>Cambiar nombre

El comando de refactorización *Cambiar nombre* puede usarse en cualquier identificador de código (por ejemplo, un nombre de clase, un nombre de propiedad, etc.) para buscar todas las apariciones de ese identificador y cambiarlas. Para cambiar el nombre de un símbolo, haga clic con el botón derecho en él y elija **Cambiar nombre...** o use el enlace de teclado **Cmd (⌘) + R**:

![Elemento de menú Cambiar nombre](media/refactoring-renaming1.png)

Esto resalta el símbolo y todas las referencias a él. Al empezar a escribir un nuevo nombre, se cambian automáticamente todas las referencias del código. Para confirmar los cambios, presione **Entrar**:

![Cambiar nombre e identificador](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Acciones rápidas

Las acciones rápidas le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción.

Las acciones rápidas pueden utilizarse para:

* Aplicar una revisión de código en el caso de una infracción de regla del analizador de código.
* Suprimir una infracción de regla del analizador de código.
* Aplicar una refactorización (por ejemplo, insertar una variable temporal).
* Generar código (por ejemplo, introducir una variable local).

Ahora se pueden aplicar acciones rápidas mediante los iconos de bombilla ![light bulb icon](media/quick-actions-light-bulb-icon.png) o de destornillador ![screwdriver icon](media/quick-actions-screwdriver-icon.png) en el editor de C#, o presionando **Opción (⌥)**+**Entrar** cuando el cursor esté en una línea de código para la que haya una acción disponible. Verá una bombilla de error ![icono de bombilla de error](media/quick-actions-error-light-bulb-icon.png) si hay un subrayado ondulado de color rojo que indica un error. Visual Studio tiene una corrección disponible para ese error.

Para cualquier lenguaje, un tercero puede proporcionar diagnósticos y sugerencias, por ejemplo, como parte de un SDK, y las bombillas de Visual Studio se encienden siguiendo esas reglas.

### <a name="quick-action-icons"></a>Iconos de acción rápida
El icono que aparece cuando hay una acción rápida disponible da una indicación del tipo de corrección o refactorización disponible. El icono *destornillador* ![icono de destornillador](media/quick-actions-screwdriver-icon.png) indica que hay acciones disponibles para cambiar el código, pero no es necesario usarlas. El icono *bombilla amarilla* ![icono de bombilla](media/quick-actions-light-bulb-icon.png) indica que hay acciones disponibles que *debe* llevar a cabo para mejorar el código. El icono *bombilla de error* ![icono de bombilla de error](media/quick-actions-error-light-bulb-icon.png) indica que hay una acción disponible que corrige un error del código.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Para ver una bombilla o un destornillador

- Si hay una corrección disponible, aparecerán bombillas espontáneamente cuando mantenga el cursor en la ubicación de un error.

   ![Bombilla con el desplazamiento del mouse](media/refactoring-lightbulb-hover.png)

- Las bombillas y los destornilladores aparecen en el margen izquierdo del editor cuando mueve el acento circunflejo a una línea de código para la que hay una acción rápida disponible.

- Presione **Opción (⌥)**+**Entrar** en cualquier parte de una línea para ver una lista de acciones rápidas y refactorizaciones disponibles.

![Mostrar elementos de contexto](media/refactoring-context-action.png)

Al mantener el puntero sobre cualquiera de las acciones de contexto, aparece una vista previa de lo que se va a agregar o quitar en el código.

![Elementos de contexto Opción + Entrar](media/refactoring-image2a.png)

Para habilitar estas opciones, debe seleccionar *Habilitar análisis de código fuente de archivos abiertos* en las opciones **Visual Studio para Mac > Preferencias > Editor de texto > Análisis de código fuente**:

![Habilitar análisis de código fuente](media/refactoring-options.png)

Se pueden sugerir más de 100 acciones. Para habilitarlas o deshabilitarlas, vaya a **Visual Studio para Mac > Preferencias > Análisis de código fuente > C# > Acciones de código** y active o desactive la casilla situada junto a la acción:

![Acciones de análisis de código fuente de C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Acciones rápidas comunes

Puede aprender más acerca de las acciones rápidas comunes en el artículo [Acciones rápidas comunes](/visualstudio/ide/common-quick-actions).

## <a name="source-analysis"></a>Análisis de código fuente

El análisis de código fuente analiza el código sobre la marcha. Para ello, subraya los posibles errores e infracciones de estilo y proporciona correcciones automáticas como acciones de contexto.

Para ver todos los resultados del análisis de código fuente de un archivo, observe la barra de desplazamiento a la derecha del editor de texto:

![Barra lateral del análisis de código fuente](media/refactoring-image4a.png)

Si hace clic en el círculo situado en la parte superior, puede iterar cada sugerencia. Los problemas con la gravedad más alta se muestran los primeros. Si mantiene el puntero sobre una línea o un resultado individual, se muestra el problema, que se puede corregir mediante las acciones de contexto:

![Elemento Análisis de código fuente](media/refactoring-image5.png)

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Vea también

- [Acciones rápidas (Visual Studio en Windows)](/visualstudio/ide/quick-actions)
- [Refactorizar código (Visual Studio en Windows)](/visualstudio/ide/refactoring-in-visual-studio)