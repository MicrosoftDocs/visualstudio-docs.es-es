---
title: Proyectos de ejemplo de Herramientas de R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
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
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Proyectos de ejemplo de Herramientas de R para Visual Studio

Esta colección de ejemplos le ayuda a empezar a trabajar con R, Herramientas de R para Visual Studio (RTVS) y Microsoft R Server:

1. Descargue el [archivo zip de ejemplos](https://github.com/Microsoft/RTVS-docs/archive/master.zip) y extraiga en una carpeta de su elección.
1. Abra `examples/Examples.sln`; verá dos carpetas en el proyecto:

    - *A First Look at R (Un primer vistazo a R)* ofrece una ligera introducción para los novatos de R.
    - *MRS and Machine Learning (MRS y aprendizaje automático)* ofrece ejemplos de cómo usar R y Microsoft R Server para el aprendizaje automático.

## <a name="a-first-look-at-r"></a>A First Look at R

Este ejemplo proporciona una introducción detallada de R mediante profusos comentarios en los archivos de origen. La mejor manera de experimentar ambos es colocar el cursor en la parte superior del archivo y presionar CTRL+Entrar para enviar cada línea, de una en una, a la ventana **R interactivo** para ver los resultados. Tenga en cuenta que algunas líneas instalarán paquetes que pueden tardar uno o dos minutos.

- `1-Getting Started with R.R` cubre muchos aspectos fundamentales de R, como el uso de paquetes, la carga y el análisis de datos y el trazado.

    ![Resultados de ejemplo de 1-Introducción a R. Ejemplo de R](~/docs/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` presenta el paquete gráfico ggplot2, conocido por sus atractivos trazados y su sencilla sintaxis. En este ejemplo se visualizan datos de terremotos de Fiyi.

    ![Resultados de ejemplo de 2-Introducción a ggplot2. Ejemplo de R](~/docs/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server and Machine Learning

Esta colección de ejemplos muestra cómo usar R y Microsoft R Server para crear modelos de aprendizaje automático y cómo aprovechar la funcionalidad de [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r). Tenga en cuenta que tendrá que instalar MRS para ejecutar scripts con `MRS` en el título y donde aparezca.

Como todos los ejemplos, una excelente manera de experimentarlos es abrir el archivo, colocar el cursor en la parte superior y luego recorrer el código línea a línea con Ctrl+Entrar. Vea también los archivos de Markdown de cada carpeta para obtener más detalles.

- `Benchmarks` ejecuta una serie de pruebas comparativas de proceso intensivo para mostrar las mejoras de rendimiento posibles gracias al uso de Microsoft R Open e Intel Math Kernel Library (MKL) para cálculos algebraicos lineales rápidos y paralelos. Con datos simulados, compara específicamente dos subprocesos frente a uno para ciertos cálculos relacionados con matrices.   

    ![Ejemplo de trazado de prueba comparativa](~/docs/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crea un modelo de predicción de demanda de bicicletas de alquiler basándose en un conjunto de datos históricos con Microsoft R Server. 

- `Data_Exploration` contiene tres scripts:  
    - `Import Data from URL.R` muestra cómo cargar un archivo de datos identificado mediante la dirección URL en R.
    - `Import Data from URL to xdf.R` muestra cómo cargar un archivo de datos identificado mediante la dirección URL en Microsoft R Server como un archivo xdf. (Requiere MRS).
    - `Using ggplot2.R` es una extensión del ejemplo `A First Look at R/2-Introduction to ggplot2.R` que ofrece un recorrido más amplio por la funcionalidad de ggplot2, incluido el trazado 3D interactivo.

        ![Resultado del uso de ggplot2. Ejemplos de R](~/docs/rtvs/media/samples-3d-interactive.png)

- `Datasets` contiene tres archivos `.csv` usados por otros ejemplos
- `Flight_Delays_Prediction_with_R` y `Flight_Delays_Prediction_with_MRS` muestran cómo predecir retrasos de vuelos con R, el aprendizaje automático y los datos históricos de puntualidad y meteorología. 
- `Machine learning` contiene tres ejemplos de aprendizaje para predecir retrasos de vuelos, precios de la vivienda y alquileres de bicicletas que muestran la aplicación de R y MRS a problemas reales. También muestran cómo usar varios modelos de aprendizaje automático populares e implementarlos como un servicio web de Azure mediante un área de trabajo de [aprendizaje automático de Azure](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` es una comparación de seis partes que muestra las similitudes y diferencias de R, Microsoft R Open y Microsoft R Server con comandos, sintaxis, construcciones y rendimiento.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Qué diferencia a Microsoft R Open y Microsoft R Server

[Microsoft R Open](http://aka.ms/rtvs-r-open), la distribución de Microsoft de R, se diferencia de [CRAN R](https://cran.r-project.org/) en dos aspectos importantes:

1. [Mejor rendimiento de cálculo](https://mran.revolutionanalytics.com/rro/#intelmkl1) cuando se usa con bibliotecas [Intel Math Kernel Library](https://software.intel.com/intel-mkl). Estas se pueden descargar de forma gratuita desde Microsoft para su uso con Microsoft R Open.

1. [Kit de herramientas de R reproducible](https://mran.revolutionanalytics.com/rro/#reproducibility), que garantiza que las bibliotecas usadas para compilar el programa de R estén siempre disponibles para los usuarios que quieren reproducir el trabajo.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) es una extensión de R que permite controlar más datos y hacerlo con mayor rapidez. Ofrece dos eficaces capacidades de R:

1. Conjuntos de datos mayores. MRS puede procesar datos de memoria insuficiente de una variedad de orígenes como clústeres de Hadoop, bases de datos y almacenes de datos. Nunca volverá a estar limitado por la RAM.

1. Procesamiento paralelo de varios núcleos. MRS puede distribuir eficazmente los cálculos entre todos los recursos informáticos que tiene disponibles. En la estación de trabajo personal o en un clúster remoto, MRS obtendrá una respuesta más rápido.

La siguiente comparación muestra que MRS y MRO con MKL tienen un rendimiento de cálculo considerablemente mejor relacionado con determinados cálculos de matrices que R y MRO sin MKL. En este cálculo se usan datos simulados:

![Comparación de MRS y MRO con MKL y R y MRO sin MKL](~/docs/rtvs/media/samples-speed-comparison.png)

Para obtener una comparación técnica de R con MRO y MRS, vea [la explicación detallada de Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sobre el tema.

En la siguiente ilustración se compara el tiempo transcurrido en segundos empleado en la creación de modelos de regresión logística para predecir si la llegada programada de vuelos de pasajeros se va a retrasar más de 15 minutos. El tiempo transcurrido empleado en CRAN R aumenta significativamente al agregar un número pequeño de filas, mientras que en MRS solo aumenta aproximadamente el doble. Para obtener detalles de esta prueba comparativa, vea el ejemplo `Benchmarks/rxGlm_benchmark.R`.

![Prueba comparativa rxGlm](~/docs/rtvs/media/samples-rxGLM-benchmark.png)

