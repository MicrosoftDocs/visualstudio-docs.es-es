---
title: Opciones de Herramientas de R en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: a2f0421ff622483fb53795dac527bb8db3c689e2
ms.contentlocale: es-es
ms.lasthandoff: 08/14/2017

---

# <a name="r-tools-for-visual-studio-options"></a>Opciones de Herramientas de R para Visual Studio
 
Se accede a la configuración a través del menú **R Tools > Opciones** o a través de **Herramientas > Opciones** y desplazándose hasta  **R Tools**:
 
  ![Cuadro de diálogo Opciones de R Tools](media/options-dialog.png)

En las secciones siguientes, se describen las distintas opciones disponibles en esta página.

> [!Note]
> Al acceder a las opciones a través del menú general **Herramientas > Opciones**, es posible que tenga que seleccionar el cuadro **Mostrar todas las configuraciones** en la parte inferior de la página **Herramientas de R** para que aparezca.

<a name="data-scientist-layout"</a>

El elemento de menú **Herramientas de R > Configuración de ciencia de datos** también configura el IDE de Visual Studio con un diseño que está optimizado para las necesidades de los científicos de datos. En concreto, esta opción abre las ventanas [Interactivo](interactive-repl.md), [Explorador de variables](variable-explorer.md) y [Áreas de trabajo](workspaces.md):

![Diseño de la ventana para científicos de datos en Visual Studio](media/installation-data-scientist-layout-result.png)

> [!Important]      
> Para revertir a otra configuración de Visual Studio más adelante, use el comando **Herramientas > Importar y exportar configuraciones**, seleccione **Exportar la configuración de entorno seleccionada** y especifique un nombre de archivo. Para restaurar esa configuración, use el mismo comando y seleccione **Importar la configuración de entorno seleccionada**. También puede usar los mismos comandos si quiere cambiar el diseño de científico de datos y volver a él más adelante, en lugar de usar el comando **Configuración de ciencia de datos** directamente.

## <a name="debugging"></a>Depuración

Estas opciones controlan la forma en la que se tratan los valores en el [Explorador de variables](variable-explorer.md) y en las ventanas del depurador, como Inspección y Variables locales (vea [Depuración](debugging.md)).

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Evaluar enlaces activos | `True` | Cuando es `True`, garantiza que siempre vea el valor más actualizado al inspeccionar variables y propiedades. El riesgo es que evaluar las expresiones puede producir efectos secundarios, dependiendo de cómo se hayan implementado. |
| Mostrar variables fijadas previamente mediante punto | `False` | Especifica si se muestran las variables fijadas previamente mediante `.`. |

## <a name="general"></a>General

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Comprobación de encuesta/novedades | `Once a week` | Especifica la frecuencia con que Herramientas de R debe comprobar en el servidor si hay actualizaciones de novedades y encuestas. | 

## <a name="help"></a>Ayuda

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Explorador web mediante F1 | `Internal` | Controla la forma en que se muestra la ayuda al buscar un término con Ctrl+F1. Cuando se establece en `Internal`, la ayuda se representa dentro de una ventana de herramientas en Visual Studio. Cuando se establece en `External`, la ayuda aparece en el explorador web predeterminado. | 
| Cadena de búsqueda en la Web mediante F1 | `R site:stackoverflow.com` | Controla la forma en que se pasan los términos de búsqueda a su motor de búsqueda al presionar Ctrl+F1 en un término en el editor. De forma predeterminada, la cadena es `R site:stackoverflow.com`, que anexa `R` al término de búsqueda. `site:stackoverflow.com` es una directiva para el motor de búsqueda que le indica que el ámbito de la búsqueda está en las páginas del dominio `stackoverflow.com`. | 
| Explorador de ayuda de R | `Automatic` | Controla la forma en la que se muestra la ayuda al buscar la documentación de R con F1, `?` o `??`. Cuando se establece en `Automatic`, la ayuda se representa en la ventana adecuada. Por ejemplo, la ayuda HTML aparece dentro de una ventana de herramientas de Visual Studio, mientras que los documentos PDF aparecen en el programa PDF predeterminado. Cuando se establece en `External`, la ayuda se representa en el explorador web predeterminado. |

## <a name="history"></a>Historial

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Guardar siempre el historial | `True` | Controla si RTVS escribe el historial de comandos en un archivo `.RHistory` en el directorio de trabajo cada vez que se cierra el proyecto. El historial se guarda incluso si no guarda el proyecto antes de salir. |
| Restablecer filtro de búsqueda | `True` | Determina si la ventana Historial puede filtrar el historial de comandos para mostrar solo los comandos de la subcadena con los que coincide el término de filtro en el cuadro de diálogo Historial de R. Esta configuración determina si se debe restablecer el filtro de búsqueda del historial cada vez que ejecuta un comando nuevo o cambia a un nuevo proyecto, lo que desencadena la carga de otro archivo `.RHistory`. El valor predeterminado de `True` reduce la sorpresa cuando ejecuta un comando con un conjunto de filtros y se pregunta por qué este no aparece en el historial. |
| Usar selección multilínea | `True` | Especifica si puede seleccionar una instrucción multilínea en el historial con un solo clic. También permite la navegación mediante las flechas arriba y abajo en las ventanas interactivas por instrucciones en lugar de líneas. |

## <a name="html"></a>HTML

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Explorador de páginas HTML | `External` | Determina dónde se representa el contenido, como un trazado `ggvis` o una aplicación `shiny`. `Internal` muestra la salida HTML dentro de una ventana de herramientas de Visual Studio; `External` muestra la salida HTML en el explorador predeterminado. | 

## <a name="logging"></a>Registro

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Registrar eventos | `Normal` | Controla el nivel de detalle del registro usado para el diagnóstico de RTVS. El valor predeterminado de `Normal` crea un archivo de registro en el directorio `TEMP`. Cuando se establece en `Traffic`, RTVS registra todos los comandos y respuestas en la sesión. Estos archivos de registro nunca salen del equipo, pero pueden resultar útiles para diagnosticar problemas en RTVS. |

## <a name="markdown"></a>Markdown

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Explorador de vista previa de Markdown | `External` | Determina dónde se muestra la salida HTML de RMarkdown. `Internal` muestra el documento HTML de RMarkdown dentro de una ventana de herramientas de Visual Studio; `External` muestra el HTML de RMarkdown mediante el explorador predeterminado. | 

## <a name="r-engine"></a>Motor de R

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Página de códigos | `(OS Default)` | Establece la página de códigos (configuración regional) de R. De manera predeterminada, usa la configuración regional subyacente del sistema operativo. | 
| Reflejo de CRAN | `(Use .Rprofile)` | Establece el reflejo de CRAN predeterminado para las instalaciones de paquetes. El valor predeterminado de `Use .Rprofile` respeta la configuración de reflejo de CRAN en su archivo `.RProfile`. |
| Directorio de trabajo | carpeta específica del usuario | Establece el directorio de trabajo actual, que normalmente se establece cada vez que se abre un proyecto. |

## <a name="workspace"></a>Área de trabajo

| Opción | Valor predeterminado | Descripción | 
| --- | --- | --- |
| Cargar área de trabajo al abrir el proyecto | `No` | Si se establece en `Yes`, permite cargar datos de la sesión del archivo `.RData` en el entorno global al abrir el proyecto. |
| Aviso para guardar el área de trabajo al restablecer | `Yes` | Si se establece en `No`, deshabilita el aviso para guardar el área de trabajo al hacer clic en el botón Restablecer en la ventana interactiva. |
| Guardar el área de trabajo cuando se cierre el proyecto | `No` | Si se establece en `Yes`, permite guardar el entorno global en el archivo `.RData` cuando se cierra el proyecto. |
| Mostrar el cuadro de diálogo de confirmación antes de cambiar de área de trabajo | `Yes` | Si se establece en `No`, deshabilita la petición de confirmación al usuario al cambiar de área de trabajo. Consulte [Cambiar de área de trabajo](workspaces.md#switching-between-workspaces) |
 

