---
title: "Introducción a R en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39228cf0-8d21-43bb-a2ce-5e5fdc81ec41
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
ms.openlocfilehash: 27c16d7315acaa0efd4aa8b866b44784ffe056a4
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---

# <a name="getting-started-with-r-tools-for-visual-studio"></a>Introducción a Herramientas de R para Visual Studio

Una vez que Herramientas de R para Visual Studio (RTVS) esté instalado (vea [Instalación](installation.md)), podrá obtener rápidamente una idea de la experiencia que proporcionan esas herramientas. En las secciones siguientes se le guiará a través de un breve paseo:

- [Crear un proyecto de R](#create-an-r-project)
- [Explorar la ventana R interactivo e IntelliSense](#explore-the-interactive-window-and-intellisense)
- [Experimentar las características de edición de código](#experience-code-editing-features)
- [Depurar el código](#debugging-your-code)
- [Pasos siguientes](#next-steps)

## <a name="create-an-r-project"></a>Crear un proyecto de R

1. Inicie Visual Studio.
1. Seleccione **Archivo > Nuevo > Proyecto...** (Ctrl+Mayús+N)
1. Seleccione "Proyecto de R" en **Plantillas > R**, asigne un nombre y una ubicación al proyecto y seleccione **Aceptar**:

   ![Cuadro de diálogo Nuevo proyecto de R en Visual Studio (RTVS en VS2017)](~/rtvs/media/getting-started-01-new-project.png)

1. Una vez creado el proyecto, verá lo siguiente:

    - A la derecha está el Explorador de soluciones de Visual Studio, donde verá el proyecto dentro de una *solución* contenedora. (Las soluciones pueden contener cualquier número de proyectos de distintos tipos; vea [Proyectos](projects.md) para obtener detalles).
    - En la esquina superior izquierda hay un nuevo archivo de R (`script.R`) donde puede editar el código fuente con todas las características de edición de Visual Studio.
    - En la parte inferior izquierda está la ventana **R interactivo**, en la que puede desarrollar y probar el código de forma interactiva.

> [!Note]
> Puede usar la ventana **R interactivo** sin tener ningún proyecto abierto e incluso cuando se cargue un tipo de proyecto diferente. Solo tiene que seleccionar **Herramientas de R > Windows > R interactivo**  en cualquier momento.

## <a name="explore-the-interactive-window-and-intellisense"></a>Explorar la ventana R interactivo e IntelliSense

1. Compruebe que la ventana R interactivo funciona escribiendo `3 + 4` y luego presionando Entrar para ver el resultado:

    ![Ventana R interactivo de Visual Studio 2017 (VS2017)](~/rtvs/media/getting-started-02-interactive1.png)

1. Escriba algo un poco más complicado, `ds <- c(1.5, 6.7, 8.9) * 1:12`, y luego escriba `ds` para ver el resultado:

    ![Ejemplo interactivo adicional de R en Visual Studio](~/rtvs/media/getting-started-03-interactive2.png)

1. Escriba `mean(ds)` pero tenga en cuenta que tan pronto como escriba `m` o `me`, Visual Studio IntelliSense proporcionará opciones de Autocompletar, como se muestra a continuación. Cuando la opción de Autocompletar que quiera esté seleccionada en la lista, presione Tab para insertarla; puede cambiar la selección con las teclas de flecha o el mouse.

    ![IntelliSense apareciendo a medida que se escribe código](~/rtvs/media/getting-started-04-intellisense1.png)

1. Después de completar `mean`, escriba el paréntesis de apertura `(` y observe cómo IntelliSense proporciona ayuda en línea para la función:

    ![IntelliSense mostrando ayuda para una función](~/rtvs/media/getting-started-05-intellisense2.png)

1. Complete la línea `mean(ds)` y presione Entrar para ver el resultado (`[1] 39.51667`).

1. La ventana R interactivo se integra con la ayuda, así que escriba `?mean`, por ejemplo, y verá ayuda para esa función en la ventana **Ayuda de R** de Visual Studio. Para obtener más detalles sobre esta característica, vea [Ayuda de Herramientas de R para Visual Studio](getting-started-help.md).

    ![Ventana Ayuda de R de Visual Studio](~/rtvs/media/getting-started-06-help.png)

1. Algunos comandos, como `plot(1:100)`, abren una nueva ventana en Visual Studio cuando los resultados no se pueden mostrar directamente en la ventana R interactivo.

    ![Visualización de un trazado en Visual Studio](~/rtvs/media/getting-started-07-plot-window.png)

La ventana R interactivo también permite revisar el historial, cargar y guardar áreas de trabajo, adjuntar a un depurador e interactuar con los archivos de código fuente para las operaciones de copiar y pegar accesos directos. Vea [Working with the R Interactive Window (Trabajar con la ventana R interactivo)](interactive-repl.md) para obtener detalles.

## <a name="experience-code-editing-features"></a>Experimentar las características de edición de código

Al trabajar brevemente con la ventana R interactivo anterior se han mostrado características de edición básicas como IntelliSense que también funcionan en el editor de código. Si escribe el mismo código que antes, verá los mismos símbolos del sistema de Autocompletar e IntelliSense, pero no los resultados.

La escritura de código en un archivo `.R` permite ver todo el código de una vez y facilita la realización de pequeños cambios en diferentes partes del código y luego la visualización del resultado al ejecutar rápidamente el código en la ventana R interactivo. También puede tener tantos archivos como quiera en un proyecto. Cuando el código está en un archivo, también puede ejecutarlo paso a paso en el depurador (como se verá más adelante). Todo esto es muy útil al desarrollar algoritmos de cálculo y escribir código para manipular uno o más conjuntos de datos, especialmente si quiere examinar todos los resultados intermedios.

Como ejemplo, los pasos siguientes crean un poco de código para explorar el [teorema del límite central](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Este ejemplo se ha adaptado del libro *R Cookbook*, de Paul Teetor).

1. En el editor `script.R`, escriba el siguiente código:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Para ver rápidamente los resultados, seleccione todo el código (Ctrl+A) y luego presione Ctrl+Entrar o haga clic con el botón derecho y seleccione **Ejecutar en modo interactivo**. Esto especifica todo el código seleccionado en la ventana R interactivo como si lo hubiera escrito directamente y muestra el resultado en una ventana de trazados:

    ![Visualización de un trazado en Visual Studio](~/rtvs/media/getting-started-08-plot1.png)

1. Para una sola línea, puede presionar Ctrl+Entrar en cualquier momento para ejecutar esa línea en la ventana R interactivo.

> [!Tip]
> Aprenda el patrón de realizar ediciones y presionar Ctrl+Entrar (o seleccionar todo con Ctrl+A y luego presionar Ctrl+ Entrar) para ejecutar rápidamente el código. Es mucho más eficaz que usar el mouse para las mismas operaciones.
> 
> Además, puede arrastrar y colocar la ventana de trazados fuera del marco de Visual Studio y ponerla en cualquier otro lugar que quiera de la pantalla. Esto le permite cambiar el tamaño de la ventana de trazados fácilmente a las dimensiones que quiere y luego guardarla en un archivo PDF o de imagen.

1. Agregue algunas líneas más de código para incluir un segundo trazado:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))    
    lines(density(samp.means))
    ```

1. Presione Ctrl+A y Ctrl+Entrar de nuevo para volver a ejecutar el código de modo que genere lo siguiente:

    ![Trazado dual actualizado en Visual Studio](~/rtvs/media/getting-started-09-plot2.png)

1. El problema es que el primer trazado determina la escala vertical, por lo que el segundo (con `lines`) no cabe. Para corregirlo, hay que establecer el parámetro `ylim` en la llamada `plot`, pero para hacerlo correctamente hay que agregar código para calcular el valor máximo vertical. Hacerlo línea a línea en la ventana R interactivo es algo incómodo, dado que hay que reorganizar el código para usar `samp.means` antes de llamar a `plot`. Pero en un archivo de código se pueden realizar fácilmente las ediciones oportunas:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Ctrl+A y Ctrl+Entrar de nuevo para ver el resultado:

    ![Trazado dual actualizado en Visual Studio, con la escala correcta](~/rtvs/media/getting-started-10-plot3.png)

En el editor se pueden hacer más cosas. Para obtener detalles, vea [Edición de código](code-editing.md), [IntelliSense](code-intellisense.md) y [Fragmentos de código](code-snippets.md).

## <a name="debugging-your-code"></a>Depurar el código

Una de las principales ventajas de Visual Studio es su interfaz de usuario de depuración. RTVS se ha creado sobre esta sólida base y agrega innovadoras opciones de interfaz de usuario, como el [explorador de variables y el visor de tablas de datos](variable-explorer.md). Vamos a echar un primer vistazo a la depuración.

1. Para empezar, restablezca el área de trabajo actual para borrar todo lo que ha hecho hasta ahora mediante el comando de menú **Herramientas de R > Sesión > Restablecer**. De forma predeterminada, todo lo que se hace en la ventana R interactivo se acumula a la sesión actual, que luego además usa el depurador. Mediante el restablecimiento de la sesión, se asegura de iniciar una sesión de depuración sin datos preexistentes (si eso es lo que quiere). Tenga en cuenta que esto no afecta al archivo de origen `script.R`, ya que se ha administrado y guardado fuera del área de trabajo.

1. Con el archivo `script.R` creado en la sección anterior, establezca un punto de interrupción en la línea que comienza con `pop <-` colocando el símbolo de inserción en esa línea y luego presionando F9 o seleccionando el comando de menú **Depurar > Alternar punto de interrupción**. Se puede hacer en un paso si se hace clic en el margen izquierdo (o medianil) de esa línea donde aparece el punto de interrupción rojo:

    ![Establecimiento de un punto de interrupción en el editor](~/rtvs/media/getting-started-11-debug1.png)

1. Inicie el depurador con el código de `script.R` seleccionando el botón **Archivo de inicio de origen** en la barra de herramientas, seleccionando los elementos de menú **Depurar > Archivo de inicio de origen** o presionando F5. Esto pone a Visual Studio en su modo de depuración y comienza a ejecutar el código. Pero se detiene en la línea donde se ha establecido el punto de interrupción:

    ![Detención en un punto de interrupción en el depurador de Visual Studio](~/rtvs/media/getting-started-12-debug2.png)

1. Durante la depuración, Visual Studio ofrece la posibilidad de recorrer el código línea a línea, incluida la capacidad de ir a funciones, saltarlas o salir de ellas al contexto de llamada. Estas capacidades y otras más pueden encontrarse en el menú **Depurar**, el menú contextual del editor y la barra de herramientas Depurar:

    ![Barra de herramientas Depurar de Visual Studio](~/rtvs/media/getting-started-13-debug3.png)

1. Cuando se detenga en un punto de interrupción, puede examinar los valores de las variables. Busque la ventana **Automático** de Visual Studio y seleccione la pestaña de la parte inferior denominada **Variables locales**. La ventana **Variables locales** muestra las variables locales en el punto actual del programa. Si se ha detenido en el punto de interrupción establecido anteriormente, verá que la variable `pop` aún no se ha definido. Ahora use el comando **Depurar > Saltar** (F10) y verá cómo aparece el valor del elemento emergente:

    ![Ventana Variables locales de Visual Studio](~/rtvs/media/getting-started-14-debug4.png)

1. Para examinar las variables de distintos ámbitos, incluidos el ámbito global y ámbitos de paquete, se usa el [explorador de variables](variable-explorer.md) que se muestra a continuación. El explorador de variables también ofrece la posibilidad de cambiar a una vista tabular con columnas que se pueden ordenar y de exportar datos a un archivo CSV.

    ![Vista expandida del explorador de variables](~/rtvs/media/variable-explorer-expanded-results.png)

1. Puede continuar pasando por el programa línea a línea o seleccionar **Continuar** (F5) para ejecutarlo hasta su finalización (o el siguiente punto de interrupción).

Para profundizar más, vea [Depuración](debugging.md) y [Explorador de variables](variable-explorer.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha aprendido los conceptos básicos de los proyectos de R y ha usado la ventana R interactivo, la edición de código y la depuración de Visual Studio. Para seguir explorando más capacidades, vea los temas siguientes, así como los que aparecen en la tabla de contenido:

- [Proyectos de ejemplo](getting-started-samples.md)
- [Edición de código](code-editing.md)
- [Depuración](debugging.md)
- [Áreas de trabajo](workspaces.md)
- [Visualización de datos](visualizing-data.md)

