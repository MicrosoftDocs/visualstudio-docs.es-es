---
title: Opciones de Herramientas de R en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: a7680ff2613051cb795d2ca9cb509f725e92dd23
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="r-tools-for-visual-studio-options"></a>Opciones de Herramientas de R para Visual Studio

Se obtiene acceso a la configuración a través del menú **Herramientas de R > Opciones** o a través de **Herramientas > Opciones** y desplazándose hasta **Herramientas de R**:

  ![Cuadro de diálogo Opciones de R Tools](media/options-dialog.png)

Las opciones y configuraciones específicas de R son accesibles mediante los métodos siguientes. Debe activar la casilla **Mostrar todas las configuraciones** en la parte inferior del cuadro de diálogo **Opciones** para que aparezcan todas estas secciones.

- Opciones de formato de código (vea [Opciones del editor](code-editing.md#editor-options): menú **Herramientas > Opciones** y después seleccione **Editor de texto > R > Formato**
- Opciones de linting (vea [Linting](code-linting.md)): menú **Herramientas > Opciones** y, después, seleccione **Editor de texto > R > Lint**
- Opciones avanzadas del Editor ([descritas en este tema](#text-editor-r-advanced-options)): menú **Herramientas > Opciones** y después seleccione **Editor de texto > R > Opciones avanzadas**
- Opciones de comportamiento ([descritas en este tema](#r-tools-advanced-options)): menú **Herramientas de R > Opciones**, o bien **Herramientas > Opciones** y después desplácese a **Herramientas de R**.

El comando **Herramientas de R > Configuración de ciencia de datos** también afecta a un número de valores distintos de forma general en Visual Studio. Este comando se describe en la siguiente sección.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Herramientas de R > Configuración de ciencia de datos

El elemento de menú **Herramientas de R > Configuración de ciencia de datos** configura el IDE de Visual Studio con un diseño que está optimizado para las necesidades de los científicos de datos. En concreto, esta opción abre las ventanas [Interactivo](interactive-repl.md), [Explorador de variables](variable-explorer.md) y [Áreas de trabajo](workspaces.md):

![Diseño de la ventana para científicos de datos en Visual Studio](media/installation-data-scientist-layout-result.png)

Para revertir a otra configuración de Visual Studio más adelante, use el comando **Herramientas > Importar y exportar configuraciones**, seleccione **Exportar la configuración de entorno seleccionada** y especifique un nombre de archivo. Para restaurar esa configuración, use el mismo comando y seleccione **Importar la configuración de entorno seleccionada**. También puede usar los mismos comandos si quiere cambiar el diseño de científico de datos y volver a él más adelante, en lugar de usar el comando **Configuración de ciencia de datos** directamente.

## <a name="text-editor--r--advanced-options"></a>Editor de texto > R > Opciones avanzadas

Estas opciones controlan el comportamiento del formato, IntelliSense, esquematización, aplicación de sangría y comprobación de sintaxis para R.

![Cuadro de diálogo de opciones avanzadas del editor de texto de R](media/options-dialog-advanced-text-editor.png)

Cada opción se establece en Activada o Desactivada para controlar el comportamiento en cuestión. Para obtener más información sobre el efecto de cada opción, mire el panel de ayuda en la parte inferior del cuadro de diálogo. Tenga en cuenta que puede arrastrar la parte superior de ese panel de ayuda hacia arriba para aumentar su tamaño.

![Panel de ayuda expandido en el cuadro de diálogo de opciones avanzadas del editor de texto R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Herramientas de R > Opciones avanzadas

El comando de menú **Herramientas de R > Opciones** abre el cuadro de diálogo **Opciones** por las opciones de R:

  ![Cuadro de diálogo Opciones de R Tools](media/options-dialog.png)

En las secciones siguientes, se describen las distintas opciones disponibles en esta página.

### <a name="debugging"></a>Depuración

Estas opciones controlan la forma en la que se tratan los valores en el [Explorador de variables](variable-explorer.md) y en las ventanas del depurador, como Inspección y Variables locales (vea [Depuración](debugging.md)).

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Evaluar enlaces activos | `True` | Cuando es `True`, garantiza que siempre vea el valor más actualizado al inspeccionar variables y propiedades. El riesgo es que evaluar las expresiones puede producir efectos secundarios, dependiendo de cómo se hayan implementado. |
| Mostrar variables fijadas previamente mediante punto | `False` | Especifica si se muestran las variables fijadas previamente mediante `.`. |

### <a name="grid-view"></a>Vista de cuadrícula

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Evaluación dinámica | `False` | De forma predeterminada, la función `View(<expression>)` toma una instantánea de los datos como una trama de datos, lo que puede consumir una cantidad de memoria considerable con conjuntos de datos grandes. Establecer esta opción en `True` significa que la expresión se evalúa cuando la cuadrícula se actualiza para capturar solo los datos que se muestran. Pero si la expresión cambia, también cambian los datos, lo que es posible que no sea adecuado para las expresiones de canalización del tipo dplyr. |

### <a name="help"></a>Ayuda

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Explorador web mediante F1 | `Internal` | Controla la forma en que se muestra la ayuda al buscar un término con Ctrl+F1. Cuando se establece en `Internal`, la ayuda se representa dentro de una ventana de herramientas en Visual Studio. Cuando se establece en `External`, la ayuda aparece en el explorador web predeterminado. |
| Cadena de búsqueda en la Web mediante F1 | `R site:stackoverflow.com` | Controla la forma en que se pasan los términos de búsqueda a su motor de búsqueda al presionar Ctrl+F1 en un término en el editor. De forma predeterminada, la cadena es `R site:stackoverflow.com`, que anexa `R` al término de búsqueda. `site:stackoverflow.com` es una directiva para el motor de búsqueda que le indica que el ámbito de la búsqueda está en las páginas del dominio `stackoverflow.com`. |
| Explorador de ayuda de R | `Automatic` | Controla la forma en la que se muestra la ayuda al buscar la documentación de R con F1, `?` o `??`. Cuando se establece en `Automatic`, la ayuda se representa en la ventana adecuada. Por ejemplo, la ayuda HTML aparece dentro de una ventana de herramientas de Visual Studio, mientras que los documentos PDF aparecen en el programa PDF predeterminado. Cuando se establece en `External`, la ayuda se representa en el explorador web predeterminado. |

### <a name="history"></a>Historial

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Guardar siempre el historial | `True` | Controla si RTVS escribe el historial de comandos en un archivo `.RHistory` en el directorio de trabajo cada vez que se cierra el proyecto. El historial se guarda incluso si no guarda el proyecto antes de salir. |
| Restablecer filtro de búsqueda | `True` | Determina si la ventana Historial puede filtrar el historial de comandos para mostrar solo los comandos de la subcadena con los que coincide el término de filtro en el cuadro de diálogo Historial de R. Esta configuración determina si se debe restablecer el filtro de búsqueda del historial cada vez que ejecuta un comando nuevo o cambia a un nuevo proyecto, lo que desencadena la carga de otro archivo `.RHistory`. El valor predeterminado de `True` reduce la sorpresa cuando ejecuta un comando con un conjunto de filtros y se pregunta por qué este no aparece en el historial. |
| Usar selección multilínea | `True` | Especifica si puede seleccionar una instrucción multilínea en el historial con un solo clic. También permite la navegación mediante las flechas arriba y abajo en las ventanas interactivas por instrucciones en lugar de líneas. |

### <a name="html"></a>HTML

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Explorador de páginas HTML | `External` | Determina dónde se representa el contenido, como un trazado `ggvis` o una aplicación `shiny`. `Internal` muestra la salida HTML dentro de una ventana de herramientas de Visual Studio; `External` muestra la salida HTML en el explorador predeterminado. |

### <a name="logging"></a>Registro

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Registrar eventos | `Normal` | Controla el nivel de detalle del registro usado para el diagnóstico de RTVS. El valor predeterminado de `Normal` crea un archivo de registro en el directorio `TEMP`. Cuando se establece en `Traffic`, RTVS registra todos los comandos y respuestas en la sesión. Estos archivos de registro nunca salen del equipo, pero pueden resultar útiles para diagnosticar problemas en RTVS. |

### <a name="markdown"></a>Markdown

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Explorador de vista previa de Markdown | `External` | Determina dónde se muestra la salida HTML de RMarkdown. `Internal` muestra el documento HTML de RMarkdown dentro de una ventana de herramientas de Visual Studio; `External` muestra el HTML de RMarkdown mediante el explorador predeterminado. |

### <a name="r-engine"></a>Motor de R

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Página de códigos | `(OS Default)` | Establece la página de códigos (configuración regional) de R. De manera predeterminada, usa la configuración regional subyacente del sistema operativo. | 
| Reflejo de CRAN | `(Use .Rprofile)` | Establece el reflejo de CRAN predeterminado para las instalaciones de paquetes. El valor predeterminado de `Use .Rprofile` respeta la configuración de reflejo de CRAN en su archivo `.RProfile`. |

### <a name="workspace"></a>Área de trabajo

| Opción | Valor predeterminado | Description |
| --- | --- | --- |
| Cargar área de trabajo al abrir el proyecto | `No` | Si se establece en `Yes`, permite cargar datos de la sesión del archivo `.RData` en el entorno global al abrir el proyecto. |
| Aviso para guardar el área de trabajo al restablecer | `Yes` | Si se establece en `No`, deshabilita el aviso para guardar el área de trabajo al hacer clic en el botón Restablecer en la ventana interactiva. |
| Guardar el área de trabajo cuando se cierre el proyecto | `No` | Si se establece en `Yes`, permite guardar el entorno global en el archivo `.RData` cuando se cierra el proyecto. |
| Mostrar el cuadro de diálogo de confirmación antes de cambiar de área de trabajo | `Yes` | Si se establece en `No`, deshabilita la petición de confirmación al usuario al cambiar de área de trabajo. Consulte [Cambiar de área de trabajo](workspaces.md#switching-between-workspaces) |
| Mostrar indicador de carga de la máquina | `False` | Controla la visibilidad del indicador de carga de red, memoria o CPU en la barra de estado. Como el indicador afecta al tráfico de red, es útil mantenerlo en `False` en escenarios de uso medidos remotos. Al cambiar esta opción es necesario reiniciar Visual Studio. |
