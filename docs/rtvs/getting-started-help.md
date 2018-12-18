---
title: Ventana de ayuda de R
description: La Ayuda de R se integra directamente en la ventana interactiva de Visual Studio mediante el comando ?. .
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 6576a701abe699bfe47666acfc21c848dde1f53a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666688"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Ayuda de Herramientas de R para Visual Studio

La Ayuda de R se integra directamente en la ventana R interactivo de Visual Studio. Siempre que use el comando `?`, por ejemplo `?mtcars`, aparece ayuda de la documentación de R en una ventana de Visual Studio:

![Ventana de ayuda en Visual Studio](media/help-window.png)

> [!Tip]
> La ventana de ayuda, como las demás de Visual Studio, se puede organizar y acoplar como quiera. Vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Para abrir los resultados de ayuda en un explorador, seleccione el menú **Herramientas de R** > **Opciones** y establezca la propiedad **Explorador de ayuda de R** en `External`. Vea [Opciones](options-for-r-tools-in-visual-studio.md).

Para buscar en la ayuda, use el comando `??` seguido por el término de búsqueda. Use comillas si el término de búsqueda contiene espacios en blanco:

```R
??"Motor Trend"
```

![Resultados de búsqueda de ayuda](media/help-search1.png)

La ventana de ayuda también tiene un campo de entrada de búsqueda con el que se pueden realizar más búsquedas directamente en la documentación de R:

![Resultados de búsqueda de ayuda mediante el campo de entrada](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Búsqueda de ayuda integrada

Los desarrolladores suelen buscar en la documentación de R para obtener ayuda acerca de los nombres de funciones, los conjuntos de datos y otros elementos. Herramientas de R para Visual Studio (RTVS) simplifica el proceso mediante la integración de las búsquedas de ayuda directamente en ventanas interactivas y del editor.

- Al presionar **F1** durante una operación Autocompletar, se genera una lista de resultados de ayuda que coinciden con la subcadena.
- Si hace clic con el botón derecho en un término de búsqueda (como una función) y selecciona el comando **Ayuda sobre**, se abrirá la ayuda para esa función. También puede invocar **Ayuda sobre** para cualquier selección.

    ![Invocación de ayuda a través del menú contextual](media/help-right-click.png)

> [!Tip]
> Para abrir la ayuda integrada en un explorador, seleccione **Herramientas de R** > **Opciones** y establezca **Explorador web mediante F1** en `External`. Vea [Opciones](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Búsqueda integrada de StackOverflow

Además de buscar en la documentación de R, los desarrolladores suelen buscar en StackOverflow mientras escriben código. RTVS también simplifica ese proceso. Haga clic con el botón derecho en un término o una selección, seleccione el comando **Buscar en la Web** (**Ctrl**+**F1**) y Visual Studio abrirá una ventana de resultados de búsqueda de ámbito de StackOverflow:

![Resultados de búsqueda en web en Visual Studio](media/help-web-search-results.png)

Puede cambiar la cadena anexada de ámbito, `R site:stackoverflow`, mediante la opción **Herramientas de R** > **Opciones** > **Cadena de búsqueda en la Web mediante F1**:

![Cambio a la opción Cadena de búsqueda en la Web mediante F1](media/options-dialog.png)

Si prefiere que se muestren resultados en un explorador, cambie la opción **Explorador web mediante F1** tal como se describe en [Opciones](options-for-r-tools-in-visual-studio.md).