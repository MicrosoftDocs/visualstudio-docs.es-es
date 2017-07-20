---
title: R Markdown con herramientas de R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
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
ms.openlocfilehash: 972abfcfda570d66b1b15b25b16e68157fc73b81
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---

# <a name="creating-r-markdown-documents"></a>Crear documentos de R Markdown

R Markdown (vea [rmarkdown.rstudio.com](https://rmarkdown.rstudio.com/)) es un formato de documento que convierte el análisis en R en documentos, informes, presentaciones y paneles de gran calidad.

Herramientas de R para Visual Studio proporciona una plantilla de elemento de R Markdown, compatibilidad de editor (incluido IntelliSense para código de R dentro del editor) y funciones de generación de archivos.

Para usar R Markdown:

1. Cierre Visual Studio.
1. (Solo una vez) Instale Pandoc de [pandoc.org](http://pandoc.org/installing.html).
1. Reinicie Visual Studio, que debe admitir la instalación de Pandoc.
1. Instale los paquetes `knitr` y `rmarkdown`. Puede hacerlo desde la [ventana interactiva](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Cree un nuevo archivo de R Markdown con el comando del menú **Archivo > Nuevo** y seleccionando **R Markdown** de la lista, o haciendo clic con el botón derecho en su proyecto en el Explorador de soluciones y seleccionando **Agregar R Markdown** (o **Agregar > Nuevo elemento...** y seleccionando **R Markdown** de la lista).

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

1. En cualquier momento durante la edición, haga clic con el botón derecho en el editor y seleccione **Vista previa**, que tiene opciones para HTML, PDF y Microsoft Word. Desde esa vista previa puede guardar el archivo como proceda para el formato que ha elegido.

