---
title: Ventana de ayuda de Herramientas de R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Ayuda de Herramientas de R para Visual Studio

La Ayuda de R se integra directamente en la ventana R interactivo de Visual Studio. Siempre que use el comando `?`, por ejemplo `?mtcars`, aparece ayuda de la documentación de R en una ventana de Visual Studio:

![Ventana de ayuda en Visual Studio](media/help-window.png)

> [!Tip]
> La ventana de ayuda, como las demás de Visual Studio, se puede organizar y acoplar como quiera. Vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> También puede abrir resultados de ayuda en un explorador si selecciona el menú **Herramientas de R > Opciones** y establece la propiedad **Explorador de ayuda de R** en `External`. Vea [Opciones](options.md).

Para buscar ayuda, use el comando `??` con el término de búsqueda entre comillas si incluye espacios:

```R
??"Motor Trend"
```

![Resultados de búsqueda de ayuda](media/help-search1.png)

La ventana de ayuda también tiene un campo de entrada de búsqueda con el que se pueden realizar más búsquedas directamente en la documentación de R:

![Resultados de búsqueda de ayuda mediante el campo de entrada](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Búsqueda de ayuda integrada

Dado que los desarrolladores suelen buscar ayuda en la documentación de R sobre los nombres de función, los conjuntos de datos y otros elementos, Herramientas de R para Visual Studio simplifica el proceso mediante la integración de las búsquedas de ayuda directamente en el editor y la ventana R interactivo.

- Al presionar F1 durante una operación Autocompletar, se genera una lista de resultados de ayuda que coinciden con la subcadena.
- Haga clic con el botón derecho en un término de búsqueda (por ejemplo, una función) y seleccione el comando **Ayuda sobre** o simplemente presione F1 para abrir ayuda sobre esa función. También puede invocar **Ayuda sobre** para cualquier selección.

    ![Invocación de ayuda a través del menú contextual](media/help-right-click.png)

> [!Tip]
> Para abrir la ayuda integrada en un explorador, seleccione **Herramientas de R > Opciones** y establezca **Explorador web mediante F1** en `External`. Vea [Opciones](options.md).

## <a name="integrated-stackoverflow-search"></a>Búsqueda integrada de StackOverflow

Además de buscar en la documentación de R, los desarrolladores suelen buscar en StackOverflow mientras escriben código. RTVS también simplifica ese proceso. Al hacer clic con el botón derecho en un término o una selección y seleccionar el comando **Buscar en la Web**, o simplemente al presionar Ctrl+F1, se abre una ventana de Visual Studio (o de un explorador, si ha cambiado a la opción **Explorador web mediante F1**) que contiene resultados de búsqueda para ese término restringidos a StackOverflow de forma predeterminada:

![Resultados de búsqueda en web en Visual Studio](media/help-web-search-results.png)

Puede cambiar la cadena anexada, `R site:stackoverflow`, mediante la opción **Herramientas de R > Opciones > Cadena de búsqueda en la Web mediante F1**:

![Cambio a la opción Cadena de búsqueda en la Web mediante F1](media/options-dialog.png)
