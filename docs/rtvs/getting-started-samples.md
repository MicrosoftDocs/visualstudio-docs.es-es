---
title: Proyectos R de ejemplo
description: Índice de una colección de ejemplos para empezar a trabajar con R y Visual Studio.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: adb26b3cf6097d830c899ef4ef251d2066b81a38
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235448"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Proyectos de ejemplo de Herramientas de R para Visual Studio

Esta colección de ejemplos le ayuda a empezar a trabajar con R, Herramientas de R para Visual Studio (RTVS) y Microsoft Machine Learning Server:

1. Descargue el [archivo zip de ejemplos](https://github.com/Microsoft/RTVS-docs/archive/master.zip) y extraiga en una carpeta de su elección.
1. Abra `examples/Examples.sln` y verá dos carpetas en el proyecto:

    - *A First Look at R (Un primer vistazo a R)* ofrece una ligera introducción para los novatos de R.
    - *MRS and Machine Learning (MRS y aprendizaje automático)* ofrece ejemplos de cómo usar R y Microsoft Machine Learning Server para el aprendizaje automático.

## <a name="a-first-look-at-r"></a>Primer vistazo a R

En este ejemplo se proporciona una introducción detallada de R mediante profusos comentarios en dos archivos de origen. Para disfrutar de la mejor experiencia, ponga el cursor sobre el archivo y pulse Ctrl+Entrar para enviar el código línea por línea a la ventana de **R interactivo**. (Puede que las líneas que instalen paquetes tarden un minuto o dos en completarse).

- `1-Getting Started with R.R` cubre muchos aspectos fundamentales de R, como el uso de paquetes, la carga y el análisis de datos y el trazado.

    ![Resultados de ejemplo de 1-Introducción a R. Ejemplo de R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` presenta el paquete gráfico ggplot2, conocido por sus atractivos trazados y su sencilla sintaxis. En este ejemplo se visualizan datos de terremotos de Fiyi.

    ![Resultados de ejemplo de 2-Introducción a ggplot2. Ejemplo de R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server y Machine Learning

Esta colección de ejemplos muestra cómo utilizar R para crear modelos de aprendizaje automático y para aprovechar las ventajas de [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

Como con todos los ejemplos, abra el archivo, coloque el cursor en la parte superior y luego recorra el código línea a línea con **Ctrl**+**Entrar**. Los archivos Markdown de cada carpeta también contienen otros detalles.

- `Benchmarks` ejecuta una serie de cálculos algebraicos lineales paralelos intensivos para mostrar las mejoras de rendimiento que se pueden obtener al usar Microsoft R Open e Intel Math Kernel Library (MKL). Con datos simulados, las pruebas comparativas comparan específicamente cálculos de matriz en un subproceso frente a dos.

    ![Ejemplo de trazado de prueba comparativa](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crea un modelo de predicción de demanda de bicicletas de alquiler basándose en un conjunto de datos históricos con ML Server. 

- `Data_Exploration` contiene tres scripts:

  - `Import Data from URL.R` muestra cómo cargar un archivo de datos identificado mediante la dirección URL en R.
  - `Import Data from URL to xdf.R` muestra cómo cargar un archivo de datos identificado mediante la dirección URL en ML Server como un archivo xdf.
  - `Using ggplot2.R` es una extensión del ejemplo `A First Look at R/2-Introduction to ggplot2.R` que ofrece un recorrido más amplio por la funcionalidad de ggplot2, incluido el trazado 3D interactivo.

      ![Resultado del uso de ggplot2. Ejemplos de R](media/samples-3d-interactive.png)

- `Datasets` contiene tres archivos *.csv* usados por otros ejemplos
- `Flight_Delays_Prediction_with_R` y `Flight_Delays_Prediction_with_MRS` muestran cómo predecir retrasos de vuelos con R, el aprendizaje automático y los datos históricos de puntualidad y meteorología. 
- `Machine learning` contiene tres ejemplos para aprender a predecir retrasos de vuelos, precios de alojamientos y alquileres de bicicletas. Conjuntamente, estos ejemplos ilustran cómo se aplica R y Microsoft ML Server a problemas del mundo real. También muestran cómo usar varios modelos de aprendizaje automático populares e implementarlos como un servicio web de Azure mediante un área de trabajo de [aprendizaje automático de Azure](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` es una comparación de seis partes en la que se muestran las similitudes y diferencias de R, Microsoft R Open y Microsoft ML Server con comandos, sintaxis, construcciones y rendimiento.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>¿Qué diferencia hay entre Microsoft R Open y Microsoft ML Server?

[Microsoft R Open](http://aka.ms/rtvs-r-open), la distribución de Microsoft de R, se diferencia de [CRAN R](https://cran.r-project.org/) en dos aspectos importantes:

1. [Mejor rendimiento de cálculo](https://mran.revolutionanalytics.com/rro/#intelmkl1) cuando se usa con bibliotecas [Intel Math Kernel Library](https://software.intel.com/intel-mkl). Las bibliotecas se pueden descargar de forma gratuita desde Microsoft para su uso con Microsoft R Open.

1. El [kit de herramientas de R reproducible](https://mran.revolutionanalytics.com/rro/#reproducibility) garantiza que las bibliotecas usadas para compilar el programa de R estén siempre disponibles para los usuarios que quieren reproducir el trabajo.

[Microsoft ML Server (MLS)](/machine-learning-server/what-is-machine-learning-server) es una extensión de R que permite controlar más datos y hacerlo con mayor rapidez. Ofrece dos eficaces capacidades de R:

1. Conjuntos de datos más grandes sin limitaciones de memoria RAM. ML Server puede procesar datos de memoria insuficiente de una variedad de orígenes como clústeres de Hadoop, bases de datos y almacenes de datos.

1. Procesamiento paralelo de varios núcleos. MLS puede distribuir eficazmente los cálculos entre todos los recursos informáticos que tiene disponibles. En la estación de trabajo personal o en un clúster remoto, MLS obtendrá una respuesta más rápido.

La siguiente comparación muestra que MLS y MRO con MKL tienen un rendimiento de cálculo considerablemente mejor relacionado con determinados cálculos de matrices que R y MRO sin MKL. En este cálculo se usan datos simulados:

![Comparación de MLS y MRO con MKL y R y MRO sin MKL](media/samples-speed-comparison.png)

Para obtener una comparación técnica de R con MRO y MLS, vea [la explicación detallada de Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sobre el tema.

En la siguiente ilustración se compara el tiempo transcurrido en segundos empleado en la creación de modelos de regresión logística para predecir retrasos en vuelos de más de 15 minutos.  El tiempo transcurrido empleado en CRAN R aumenta significativamente al agregar un número pequeño de filas, mientras que en MLS solo aumenta aproximadamente el doble. Para obtener detalles de esta prueba comparativa, consulte el ejemplo de *Benchmarks/rxGlm_benchmark.R*.

![Prueba comparativa rxGlm](media/samples-rxGLM-benchmark.png)
