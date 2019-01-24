---
title: Procedimiento Limitar la instrumentación a funciones específicas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0135ea7d3a99f54b8bc61fb77c5b1657992033c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895063"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Procedimiento Limitar la instrumentación a funciones específicas
La instrumentación y recopilación de datos se pueden limitar a una o más funciones. Basta con establecer las opciones de la página **Avanzado** de la **Sesión de rendimiento** o las páginas de propiedades del binario de destino:  
  
- Si especifica las funciones en la página de propiedades de la sesión de rendimiento, se instrumentan solo esas funciones en todos los binarios instrumentados de la sesión.  
  
- Si especifica las funciones en la página de propiedades de un binario de destino, solo las funciones que estén en ese binario determinado se instrumentan. Las funciones en otros binarios del rendimiento se instrumentan como de costumbre.  
  
  Este modo de limitar la recopilación de datos solo se admite cuando se selecciona el método de generación de perfiles de instrumentación.  
  
> [!NOTE]
>  También puede usar la página **Avanzado** de las páginas de propiedades de **Sesión de rendimiento** con el fin de establecer otras opciones disponibles para la herramienta de instrumentación de línea de comandos [VSInstr](../profiling/vsinstr.md) de las herramientas de generación de perfiles.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Para limitar la instrumentación a funciones específicas en una sesión de rendimiento  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en el nombre de la sesión y después haga clic en **Propiedades**.  
  
    Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
2. En el cuadro de diálogo **Páginas de propiedades**, haga clic en **Avanzado**.  
  
3. En el cuadro de texto **Opciones de instrumentación adicionales**, use la siguiente sintaxis para escribir el nombre de las funciones que desea instrumentar:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` es el nombre del espacio de nombres y la función. Tiene el formato `Namespace`**::**`FunctionName`. Use un signo de punto y coma para separar varias funciones. Use un asterisco (\*) para especificar un carácter comodín para uno o más caracteres. Por ejemplo, **-include:MyNS::\\*** especifica todas las funciones en el espacio de nombres MyNS.  
  
   > [!NOTE]
   >  Para obtener una lista de las funciones en un archivo binario, abra una ventana de símbolo del sistema en el directorio de instalación de Herramientas de generación de perfiles (vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) y después escriba **vsinstr /DumpFuncs**.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Para limitar la instrumentación a funciones específicas en un binario  
  
1. En **Explorador de rendimiento**, busque el nombre del binario en el nodo **Destinos** de la sesión de rendimiento.  
  
2. Haga clic con el botón derecho en el nuevo nombre de binario y seleccione **Propiedades**.  
  
    Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
3. En el cuadro de diálogo **Páginas de propiedades**, haga clic en **Avanzado**.  
  
4. En el cuadro de texto **Opciones de instrumentación adicionales**, use la siguiente sintaxis para escribir el nombre de las funciones que desea instrumentar:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` es el nombre del espacio de nombres y la función. Tiene el formato `Namespace`**::**`FunctionName`. Use un signo de punto y coma para separar varias funciones. Use un asterisco (\*) para especificar un carácter comodín para uno o más caracteres. Por ejemplo, **-include:MyNS::\\*** especifica todas las funciones en el espacio de nombres MyNS.  
  
   > [!NOTE]
   >  Para obtener una lista de las funciones en un archivo binario, abra una ventana de símbolo del sistema en el directorio de instalación de Herramientas de generación de perfiles (vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) y después escriba **vsinstr /DumpFuncs**.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Limitar la instrumentación a archivos DLL específicos](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Cómo: Especificar opciones de instrumentación adicionales](../profiling/how-to-specify-additional-instrumentation-options.md)