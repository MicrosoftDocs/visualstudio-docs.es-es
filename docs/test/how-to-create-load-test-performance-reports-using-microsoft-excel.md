---
title: Creación de informes de rendimiento de la prueba de carga de Visual Studio con Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b82a35ed56c0930b8d9c0ff8ec7bfcbd008a7648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Cómo: Crear informes de rendimiento de la prueba de carga con Microsoft Excel

Puede generar informes de prueba de carga de Microsoft Excel basados en dos o más resultados de pruebas. Están disponibles dos informes de prueba de carga:

-   **Ejecutar comparación** Crea un conjunto de informes que compara los datos de dos resultados de pruebas de carga usando tablas y gráficos de barras.

-   **Tendencia** Puede generar análisis de tendencias en dos o más resultados de pruebas de carga. Los resultados se muestran con gráficos de líneas, pero los datos están disponibles en tablas dinámicas.

> [!TIP]
> También puede crear manualmente informes de Microsoft Word copiando y pegando datos de las vistas de resumen, gráficos y tablas. Vea [Cómo: Crear manualmente informes de rendimiento de pruebas de carga con Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

 Se puede usar cualquier de estos dos informes para compartir los datos de rendimiento con las partes interesadas y mostrar si el rendimiento global y el estado del sistema mejoran o empeoran.

 Las definiciones de informe están almacenadas en la base de datos de pruebas de carga. Cuando se guarda un informe, su definición se guarda en la base de datos y se puede volver a utilizar más adelante.

 Además, el libro de Excel se puede compartir con las partes interesadas de forma que no tengan que conectarse a la base de datos para ver el informe.

> [!NOTE]
> Puede compartir el libro de Excel; sin embargo, solo los usuarios que tienen Visual Studio instalado en su equipo podrán modificar cualquiera de las hojas de cálculo. Los demás usuarios no verán la opción **Informe de prueba de carga** en la cinta de Office, pero sí el libro.

 La siguiente ilustración es un ejemplo de un informe que muestra una correlación entre un declive en la velocidad de la transacción (Actualizar el carro) y la degeneración del contador (% de procesador). Esto señala un posible problema en el código de aplicación, en lugar de en la base de datos o en la red, y es un buen candidato al diagnóstico usando el Generador de perfiles de ASP.NET.

 ![Problema potencial en el código de la aplicación](../test/media/lt_excel.png "LT_Excel")

 Los informes de Excel se pueden generar en el Analizador de pruebas de carga, usando el botón **Crear informe en Excel** de la barra de herramientas o desde Excel, usando la opción **Cargar informe de pruebas** en la pestaña **Prueba de carga** de la cinta de opciones de Office.

> [!NOTE]
> Si agrega comentarios a una prueba de carga, aparecerán en el informe de Excel. Para más información, vea [Cómo: Agregar comentarios mientras se analiza una prueba de carga completada](../test/how-to-add-comments-on-a-completed-load-test.md).

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Para generar informes de comparación de pruebas de carga mediante Excel

1.  Antes de generar un informe, debe ejecutar una prueba de carga.

2.  Puede crear informes de prueba de carga de Excel de dos maneras:

    1.  Después de completar una prueba de carga, en la página **Resultados de pruebas de carga**, elija el botón **Crear informe en Excel** de la barra de herramientas.

        > [!NOTE]
        > Si el botón **Crear informe en Excel** está deshabilitado en la barra de herramientas del Visor de resultados de pruebas de rendimiento web, es posible que deba ejecutar Microsoft Excel una vez para que se habilite. Cuando se instala Visual Studio Enterprise, el complemento de prueba de carga de Visual Studio Enterprise se copia en su equipo para Microsoft Excel; sin embargo, Microsoft Excel se debe ejecutar para completar el proceso de instalación del complemento.

     Microsoft Excel se abre con el asistente **Generar un informe de pruebas de carga**.

     O bien

    1.  Abra Microsoft Excel, seleccione la pestaña **Prueba de carga** en la cinta de opciones de Office y, después, elija **Informe de prueba de carga**.

         Aparecerá el asistente **Generar un informe de pruebas de carga**.

    2.  En la página **Seleccionar la base de datos que contiene las pruebas de carga**, en **Nombre del servidor**, escriba el nombre del servidor que contiene los resultados de pruebas de carga.

    3.  En la lista desplegable **Databasename**, seleccione la base de datos que contiene los resultados de pruebas de carga.

3.  En la página **¿Cómo desea generar el informe?**, compruebe que **Crear un informe** está seleccionado y elija **Siguiente**.

4.  En la página **¿Qué tipo de informe desea generar?**, compruebe que **Ejecutar comparación** está seleccionado y elija **Siguiente**.

5.  En la página **Especificar detalles de informe de pruebas de carga**, escriba un nombre para el informe en **Nombre del informe**.

6.  Seleccione la prueba de carga cuyo informe quiere generar y elija **Siguiente**.

7.  En la página **Seleccionar las ejecuciones para el informe**, en **Seleccione una o varias ejecuciones para agregarlas al informe**, seleccione dos resultados de pruebas de carga que quiera comparar en el informe y elija **Siguiente**.

    > [!NOTE]
    > Solamente puede generar un informe de comparación a partir de dos resultados de pruebas de carga. Si selecciona un resultado de pruebas de carga o más de dos resultados de pruebas de carga, aparecerá un mensaje de advertencia.

8.  En la página **Seleccionar los contadores del informe**, en **Seleccione uno o más contadores para agregar al informe**, existe una lista ampliable de contadores disponibles para personalizar el informe. Seleccione los contadores que quiera comparar en las dos ejecuciones de pruebas seleccionadas en el informe y elija **Finalizar**.

9. El informe del libro de Excel se genera con las siguientes pestañas de la hoja de cálculo:

    -   **Tabla de contenido**: muestra el nombre del informe de prueba de carga y proporciona una tabla de contenido con vínculos a las diferentes pestañas del informe.

    -   **Ejecuciones**: proporciona detalles sobre las dos ejecuciones que se comparan en el informe.

    -   **Comparación de pruebas**: proporciona detalles en forma de gráfico de barras sobre las regresiones y las mejoras de rendimiento entre las dos ejecuciones que se comparan.

    -   **Comparación de páginas**: proporciona datos de comparación de rendimiento en forma de gráfico de barras y porcentaje entre las dos ejecuciones en las diferentes páginas de las ejecuciones de pruebas.

    -   **Comparación de equipos**: proporciona datos de comparación entre las dos ejecuciones basados en los equipos usados.

    -   **Comparación de errores**: compara los tipos de error encontrados entre los dos ejecuciones y el número de repeticiones.

    > [!TIP]
    > Para conseguir mejores informes, las pruebas de carga y las pruebas de rendimiento web cuenta con varias propiedades disponibles que permiten obtener informes más completos. La solicitud de página tiene dos propiedades que se presentan en los informes: Objetivo y Nombre de informe. Los tiempos de respuesta de página se mostrarán con respecto al objetivo y se usará el nombre del informe en lugar de la dirección URL en los informes. En los parámetros de ejecución de una prueba de carga, en Administrar conjuntos de contadores, se incluye la propiedad Etiquetas de equipo para los nombres del equipo de los informes. Resulta muy útil para describir el rol de un equipo determinado en el informe.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Para generar informes de tendencia de las pruebas de carga mediante Excel

1.  Antes de generar un informe, debe ejecutar una prueba de carga.

2.  Puede crear informes de prueba de carga de Excel de dos maneras:

    1.  Después de completar una prueba de carga, en la página **Resultados de pruebas de carga**, elija el botón **Crear informe en Excel** de la barra de herramientas.

        > [!NOTE]
        > Si el botón **Crear informe en Excel** está deshabilitado en la barra de herramientas del Visor de resultados de pruebas de rendimiento web, es posible que deba ejecutar Microsoft Excel una vez para que se habilite. Cuando se instala Visual Studio Enterprise, el complemento de prueba de carga de Visual Studio Enterprise se copia en su equipo para Microsoft Excel; sin embargo, Microsoft Excel se debe ejecutar para completar el proceso de instalación del complemento.

     Microsoft Excel se abre con el asistente **Generar un informe de pruebas de carga**.

     O bien

    1.  Abra Microsoft Excel, seleccione la pestaña **Prueba de carga** en la cinta de opciones de Office y, después, elija **Informe de prueba de carga**.

         Aparecerá el asistente **Generar un informe de pruebas de carga**.

    2.  En la página **Seleccionar la base de datos que contiene las pruebas de carga**, en **Nombre del servidor**, escriba el nombre del servidor que contiene los resultados de pruebas de carga.

    3.  En la lista desplegable **Databasename**, seleccione la base de datos que contiene los resultados de pruebas de carga.

3.  En la página **¿Cómo desea generar el informe?**, compruebe que **Crear un informe** está seleccionado y elija **Siguiente**.

4.  En la página **¿Qué tipo de informe desea generar?**, compruebe que **Tendencia** está seleccionado y elija **Siguiente**.

5.  En la página **Especificar detalles de informe de pruebas de carga**, escriba un nombre para el informe en **Nombre del informe**.

6.  Seleccione la prueba de carga cuyo informe quiere generar y elija **Siguiente**.

7.  En la página **Seleccionar las ejecuciones para el informe**, en **Seleccione una o varias ejecuciones para agregarlas al informe**, seleccione los resultados de pruebas de carga que quiera comparar en el informe y elija **Siguiente**.

8.  En la página **Seleccionar los contadores del informe**, en **Seleccione uno o más contadores para agregar al informe**, existe una lista ampliable de contadores disponibles para personalizar el informe. Seleccione los contadores que quiera comparar para el análisis de tendencias y elija **Finalizar**.

10. El informe se genera con una tabla de contenido que tiene vínculos a las diferentes pestañas del libro de Excel generadas en el informe. Los vínculos se basan en los contadores seleccionados para el informe de tendencia. Por ejemplo, si conservó los contadores predeterminados seleccionados en el paso 7, el informe generará datos que se presentan en pestañas independientes de Excel para cada contador incluido en el paso 7. Los datos que se generan para cada contador se presentan en gráficos de tendencia.

    > [!TIP]
    > Para conseguir mejores informes, las pruebas de carga y las pruebas de rendimiento web cuenta con varias propiedades disponibles que permiten obtener informes más completos. La solicitud de página tiene dos propiedades que se presentan en los informes: Objetivo y Nombre de informe. Los tiempos de respuesta de página se mostrarán con respecto al objetivo y se usará el nombre del informe en lugar de la dirección URL en los informes. En los parámetros de ejecución de una prueba de carga, en Administrar conjuntos de contadores, se incluye la propiedad Etiquetas de equipo para los nombres del equipo de los informes. Resulta muy útil para describir el rol de un equipo determinado en el informe.

## <a name="net-framework-security"></a>Seguridad de .NET Framework

Los resultados y los informes de pruebas de carga contienen información posiblemente sensible que podría utilizarse para crear ataques contra su equipo o su red. Los resultados y los informes de pruebas de carga contienen nombres de equipo y cadenas de conexión. Debe tenerlo en cuenta cuando comparta informes de pruebas de carga con otros usuarios.

## <a name="see-also"></a>Vea también

- [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md)