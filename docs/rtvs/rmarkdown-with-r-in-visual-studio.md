---
title: R Markdown con herramientas de R para Visual Studio | Microsoft Docs
description: "Describe cómo crear documentos de R Markdown en Visual Studio para generar informes, presentaciones y paneles de alta calidad."
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 982dc9a2fbcb8e6cb790ec64c07d83f02017c803
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="creating-r-markdown-documents"></a>Crear documentos de R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) es un formato de documento que convierte el análisis en R en documentos, informes, presentaciones y paneles de gran calidad.

Herramientas de R para Visual Studio (RTVS) proporciona una plantilla de elemento de R Markdown, compatibilidad de editor (incluido IntelliSense para código de R dentro del editor), características de generación de archivos y vista previa dinámica.

## <a name="using-r-markdown"></a>Uso de R Markdown

1. Cierre Visual Studio.
1. (Solo una vez) Instale `pandoc` de [pandoc.org](http://pandoc.org/installing.html).
1. Reinicie Visual Studio, que debe admitir la instalación de Pandoc.
1. Instale los paquetes `knitr` y `rmarkdown`. Puede hacerlo desde la [ventana interactiva](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Cree un archivo de R Markdown mediante el comando de menú **Archivo > Nuevo > Archivo** y seleccionando **R > R Markdown** en la lista. En el contexto de un proyecto, haga clic con el botón derecho en el proyecto en el Explorador de soluciones, seleccione **Agregar Markdown de R** (o **Agregar > Nuevo elemento...** y seleccione **R Markdown** en la lista).

1. El contenido predeterminado del archivo nuevo es de la manera siguiente:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Vistas previas

En Visual Studio 2017 15.5 y versiones posteriores se proporcionan automáticamente vistas previas dinámicas para R Markdown. Para activar la sincronización automática entre el editor y la vista previa, seleccione **Herramientas de R > Markdown > Sincronización automática** (Ctrl+Mayús+Y). Si no está usando la sincronización automática, puede actualizar la vista previa mediante **Herramientas de R > Markdown > Recargar la vista previa de R Markdown**.

También puede obtener una vista previa del archivo en formato HTML, PDF y de Microsoft Word si hace clic con el botón derecho en el editor y selecciona uno de los comandos de **Vista previa**. Los mismos comandos también están disponibles en el menú **Herramientas de R > Markdown**. (En versiones anteriores de Visual Studio, estos comandos se encuentran en el menú **Herramientas de R > Publicar**).

![Vista previa dinámica de R Markdown y otros comandos de menú de vista previa](media/rmarkdown-live-preview.png)
