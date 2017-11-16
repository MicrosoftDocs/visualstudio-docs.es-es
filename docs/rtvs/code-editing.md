---
title: "Edición de código con Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a198ccc3-5506-48e7-b3b2-9399661b80d5
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5c856bb02ca33f999273fd6da782226be5f0f2d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="editing-r-code-in-visual-studio"></a>Edición de código de R en Visual Studio
 
Herramientas de R para Visual Studio (RTVS) adapta la experiencia de edición de Visual Studio expresamente para R, mientras que conserva todas las características y la capacidad de usar extensiones. (Por ejemplo, si prefiere enlaces de teclado de VIM, puede instalar la [extensión gratuita VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) desde la Galería de Visual Studio).

En este tema:

- [Resalte de sintaxis](#syntax-highlighting)
- [Edición y organización del código](#editing-and-organizing-code)
- [Navegación por el código](#code-navigation)
- [Envío de código a la ventana interactiva](#sending-code-to-the-interactive-window)
- [Formato de código](#formatting-code)
- [Inserción de comentarios Roxygen](#inserting-roxygen-comments)
- [Opciones del editor](#editor-options)

Vea también los temas en [IntelliSense](code-intellisense.md), [fragmentos de código](code-snippets.md) y [R Markdown](rmarkdown.md).


## <a name="syntax-highlighting"></a>Resalte de sintaxis 

Además de colorear diferentes partes del código, como cadenas, comentarios y palabras clave, RTVS también resalta y permite vínculos en comentarios:

![Color de sintaxis para código de R](media/editing-syntax-colors.png)

Para personalizar las fuentes y determinados colores de resaltado, seleccione el comando **Herramientas > Opciones**, vaya a **Entorno > Fuentes y colores** y después cambie la configuración de elementos relacionados con R en el cuadro **Mostrar elementos**:

![Opciones de color y fuentes para el código de R](media/editing-syntax-colors-options.png)

Visual Studio también subraya los errores de sintaxis en el editor:

![Resaltado de errores de sintaxis en código de R](media/editing-syntax-error.png)

Para cambiar este comportamiento, consulte la configuración **Avanzadas > Comprobación de sintaxis** en [Opciones del editor](#editor-options).

## <a name="editing-and-organizing-code"></a>Edición y organización del código

Mientras escribe código, RTVS proporciona finalización automática, como se describe en la página [IntelliSense](code-intellisense.md). También realiza formato automático como la finalización de paréntesis y llaves: 

![Animación de formato en línea](media/editing-inline-formatting.gif)

Si al escribir se llama a funciones que tienen muchos parámetros, a menudo querrá alinear los parámetros para que el código sea más fácil de leer. RTVS recuerda la sangría establecida para los parámetros y la aplica automáticamente a las líneas siguientes:

![Animación de sangría automática](media/editing-auto-indentation.gif)

Para cambiar este comportamiento, vea las [Opciones del editor](#editor-options) para el grupo **Pestañas**.

Las regiones de código contraíbles le permiten ocultar temporalmente parte del código en el editor. Visual Studio crea varias regiones automáticamente (por ejemplo, en instrucciones multilínea), a menos que la opción **Avanzadas > Esquematización > Esquematización de código** esté establecida en Desactivado.

Para crear una región propia, rodee el código que quiera con comentarios que terminen con `---`. Los pequeños controles +/- a la izquierda del código permiten expandir y contraer las regiones:

![Creación de una región contraíble con comentarios](media/editing-collapsible-regions.gif)
 
De forma predeterminada, Visual Studio inserta espacios al presionar la tecla Tab. De nuevo, puede cambiar este comportamiento como se describe en [Opciones, Editor de texto, Todos los lenguajes](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navegación por el código

La navegación por el código le permite acceder rápidamente al código fuente de su programa de R y sus bibliotecas. Estas características le mantienen en su flujo de trabajo en lugar de tener que buscar el código manualmente.

**Ir a definición** salta rápidamente a una definición de función o muestra un pequeño editor en línea para leer el código fuente de una función de biblioteca. Solo tiene que hacer clic con el botón derecho en la función que le interese y seleccionar **Ir a definición** o colocar el cursor en la función y presionar F12.

Este comando abre una nueva ventana de editor que contiene el código fuente de la función. El cursor se coloca convenientemente al principio de la definición de la función.

**Ver la definición**, invocado desde el menú contextual o Alt+F12, inserta una región desplazable de solo lectura que contiene el código fuente de la función bajo la llamada de función:

![Animación de Ver la definición](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Envío de código a la ventana interactiva

A muchos desarrolladores les gusta escribir código en el editor y después enviarlo a la [ventana interactiva](interactive-repl.md) para realizar pruebas de inmediato (también conocido como read-eval-print loop o REPL). Al presionar Ctrl+Entrar en el editor de R se envía la línea actual de código a la ventana interactiva, que después coloca el cursor en la línea siguiente. Con Ctrl+Entrar, puede examinar el código de forma eficaz desde el editor.

También puede seleccionar código y presionar Ctrl+ Entrar para aplicar toda la selección. Como alternativa, haga clic con el botón derecho en la selección y seleccione **Ejecutar en modo interactivo**.

## <a name="formatting-code"></a>Formato de código

El formato automático de Visual Studio mantiene el código que escriba, así como el código que pegue en el editor, con el formato que establezca en las preferencias. También puede hacer una selección, hacer clic con el botón derecho y seleccionar **Dar formato a la selección** (Ctrl+K,F) para aplicar esas preferencias. Por ejemplo, si tuviera una definición de función en una sola línea:

```R
f<-function  (a){  return(a + 1) }
```

Aplicar formato la limpia para que quede de esta forma:

```R
f <- function(a) { return(a + 1) }
```

Para volver a aplicar formato a todo el archivo de código, seleccione **Editar > Avanzadas > Dar formato al documento** (Ctrl+E,D).

El formato automático es una operación independiente que se puede deshacer. Por ejemplo, si pega código en el editor y se aplica el formato, al seleccionar **Editar > Deshacer** o presionar Ctrl+Z una vez se deshace el formato; si vuelve a seleccionar Deshacer, se deshará también el pegado.
 
Las opciones de formato (incluida la desactivación del formato) se establecen mediante **Herramientas > Opciones** en la pestaña **Editor de texto > R > Opciones avanzadas**. Puede ir directamente a esta página mediante el comando **Herramientas de R > Opciones del editor...** o haciendo clic con el botón derecho en el editor y seleccionando **Opciones de formato...** Vea la sección [Opciones del editor](#editor-options) para obtener más información.
 
## <a name="inserting-roxygen-comments"></a>Inserción de comentarios Roxygen

RTVS proporciona un acceso directo para generar comentarios [Roxygen](http://roxygen.org/) con los nombres de parámetro de una función. Solo tiene que escribir `###` en una línea en blanco encima de la definición de función:

![Animación de la inserción de un comentario Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opciones del editor

Las opciones específicas del editor se establecen a través del comando **Herramientas > Opciones**, al ir a **Editor de texto > R** o al usar el comando de acceso directo **Herramientas de R > Opciones del editor...**

Las opciones de las pestañas **General**, **Barras de desplazamiento** y **Pestañas** no son específicas de R, pero son opciones de configuración generales de Visual Studio que están disponibles para todos los lenguajes, pero que se aplican por lenguaje. Para obtener más información, consulte los siguientes temas:

- [Opciones, Editor de texto, Todos los lenguajes](../ide/reference/options-text-editor-all-languages.md)
- [Hacer un seguimiento del código personalizando la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opciones, editor de texto, todos los lenguajes, pestañas](../ide/reference/options-text-editor-all-languages-tabs.md)

Las opciones de la pestaña **R > Avanzadas** son específicas de RTVS:

| Agrupar | Opción | Default | Descripción |
| --- | --- | --- | --- |
| Formato | Formato automático | Activado | Cambia el formato del código a medida que escribe. No afecta a los comandos **Dar formato a la selección** ni **Dar formato al documento**. |
| | Llaves expandidas | Desactivado | Coloca una { de apertura en una nueva línea. |
| | Dar formato al pegar | Activado | Aplica formato al pegar. |
| | Dar formato al ámbito en } | Activado | Da formato al ámbito después de escribir una } de cierre. |
| | Espacio después de coma | Activado | Coloca un espacio después de las comas. |
| | Espacio después de palabra clave | Activado | Coloca un espacio después de palabras clave como `if`, `while` y `repeat`. |
| | Espacio antes de { | Activado | Coloca un espacio antes de una { de apertura. |
| | Espacios alrededor de = | Activado | Coloca espacios alrededor de un signo igual. |
| IntelliSense | Confirmar con la tecla Entrar | Desactivado | Confirma la selección de finalización automática al presionar Entrar. |
| | Confirmar con la barra espaciadora | Desactivado | Confirma la selección de finalización automática al presionar la barra espaciadora.|
| | Lista de finalización en el primer carácter | Activado | Muestra la lista de finalización en los primeros tipos de caracteres. Si está desactivado, se muestra una lista de finalización con **Editar > IntelliSense > Lista de miembros** (Ctrl+J). |
| | Lista de finalización en la tecla TAB | Desactivado | Invoca la lista de finalización al escribir uno o varios caracteres y presionar TAB. |
| | Hacer coincidir nombres de argumentos escritos de forma parcial | Desactivado | Al escribir nombres de argumentos en una llamada de función, la ayuda de signatura muestra una descripción del argumento que coincide mejor. |
| Ventana interactiva | Comprobación de sintaxis en la consola de R | Desactivado | Aplica la comprobación de sintaxis en la ventana interactiva. Es posible que la comprobación de sintaxis no funcione correctamente con instrucciones multilínea. | 
| esquematizar | Esquematización de código | Activado | Crea automáticamente regiones contraíbles para áreas como instrucciones multilínea. | 
| Comprobación de sintaxis | Mostrar errores de sintaxis | Activado | Habilita la comprobación automática de sintaxis del código. |
