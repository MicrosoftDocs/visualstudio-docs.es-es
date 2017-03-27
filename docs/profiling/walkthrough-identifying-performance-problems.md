---
title: 'Tutorial: identificar problemas de rendimiento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: e42b90e6e9c3b151ae47032b54686c50bf838426
ms.lasthandoff: 03/07/2017

---
# <a name="walkthrough-identifying-performance-problems"></a>Tutorial: identificar problemas de rendimiento
En este tutorial se muestra cómo generar perfiles de una aplicación para identificar problemas de rendimiento.  
  
 En este tutorial, recorreremos paso a paso el proceso de generación de perfiles de una aplicación administrada, así como el uso del muestreo y la instrumentación para aislar e identificar los problemas de rendimiento de la aplicación.  
  
 En este tutorial realizará los siguientes pasos:  
  
-   Generar perfiles de una aplicación utilizando el método de muestreo.  
  
-   Analizar los resultados de generación de perfiles mediante muestreo para buscar y corregir un problema de rendimiento.  
  
-   Generar perfiles de una aplicación utilizando el método de instrumentación.  
  
-   Analizar los resultados de generación de perfiles mediante instrumentación para buscar y corregir un problema de rendimiento.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Nivel intermedio de comprensión de C#.  
  
-   Una copia de la [muestra PeopleTrax](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Para trabajar con la información proporcionada por la generación de perfiles, es preferible disponer de la información de símbolos de depuración.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Generar perfiles utilizando el método de muestreo  
 El muestreo es un método de generación de perfiles mediante el cual el proceso en cuestión se sondea periódicamente para determinar la función activa. Los datos resultantes proporcionan un recuento de la frecuencia con que esa función ha estado en la parte superior de la pila de llamadas al muestrear el proceso.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Para generar perfiles de una aplicación utilizando el método de muestreo  
  
1.  Abra [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] con privilegios de administrador. La ejecución como administrador es necesaria para la generación de perfiles.  
  
2.  Abra la solución PeopleTrax.  
  
     La solución PeopleTrax rellenará el Explorador de soluciones.  
  
3.  Establezca la opción de configuración del proyecto en **Lanzamiento**.  
  
     Debe usar la compilación de lanzamiento para detectar los problemas de rendimiento de una aplicación. Se recomienda una compilación de lanzamiento para la generación de perfiles porque una compilación de depuración tiene información adicional compilada internamente, lo que puede afectar negativamente al rendimiento e impedir que se muestren con precisión los problemas de rendimiento.  
  
4.  En el menú **Analizar**, seleccione **Generador de perfiles de rendimiento** y luego seleccione **Asistente de rendimiento** e **Iniciar**.  
  
     Aparece el Asistente de rendimiento.  
  
5.  Asegúrese de que la opción **Muestreo de la CPU (recomendado)** está seleccionada y haga clic en **Siguiente**.  
  
6.  En **¿Para qué aplicación desea generar perfiles?**, seleccione PeopleTrax y después haga clic en **Siguiente**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] compila el proyecto y empieza a perfilar la aplicación. Aparecerá la ventana de la aplicación **PeopleTrax**.  
  
7.  Haga clic en **Get People**.  
  
8.  Haga clic en **ExportData**.  
  
     Se abrirá el Bloc de notas con un nuevo archivo que contiene los datos exportados de **PeopleTrax**.  
  
9. Cierre el Bloc de notas y después cierre la aplicación **PeopleTrax**.  
  
     El generador de perfiles crea un archivo de datos de generación de perfiles (\*.vsp), muestra el nombre de archivo en la sección Informes de la ventana Explorador de rendimiento y carga automáticamente la vista **Resumen** del archivo de datos en la ventana principal de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Para analizar los resultados de la generación de perfiles mediante muestreo  
  
1.  En la vista Resumen se muestra una escala de tiempo del uso de la CPU durante la ejecución de la generación de perfiles, la lista **Ruta de acceso activa**, que representa la rama del árbol de llamadas de la aplicación que registro más actividad, y una lista de **Funciones que realizan la mayor parte de trabajo individual**, que muestra las funciones que más se muestrearon durante la ejecución del código en el propio cuerpo de la función.  
  
     Examine la lista **Ruta de acceso activa** y observe que el método PeopleNS.People.GetNames es la función de PeopleTrax más próxima al final de la lista. Su posición la convierte en un buena candidata para el análisis. Haga clic en el nombre de la función para mostrar los detalles de GetNames en la vista **Detalles de la función**.  
  
2.  La vista **Detalles de la función** contiene dos ventanas. La ventana de distribución del costo proporciona una vista gráfica del trabajo realizado por la función, el trabajo realizado por las funciones a las que llamó y la contribución de las funciones que llamaron a la función en el número de instancias que se usaron en el muestreo. Puede cambiar la función que está en el foco de la vista haciendo clic en el nombre de otra función. Por ejemplo, puede hacer clic en PeopleNS.People.GetPeople para hacer que GetPeople sea la función seleccionada.  
  
     En la ventana **Vista de código de función** se muestra el código fuente de la función si está disponible y se resaltan las líneas menos eficaces de la función seleccionada. Si selecciona GetNames, puede observar que esta función lee una cadena de los recursos de aplicación y, a continuación, usa un <xref:System.IO.StringReader> para agregar cada una de las líneas de la cadena a una <xref:System.Collections.ArrayList>. No existe ningún mecanismo claro para optimizar esta función.  
  
3.  Dado que PeopleNS.People.GetPeople es el único llamador de GetNames, en la ventana de distribución del costo, haga clic en GetPeople para examinar el código. Este método devuelve una <xref:System.Collections.ArrayList> de los objetos PersonInformationNS.PersonInformation a partir de los nombres de las personas y compañías generados por GetNames. Sin embargo, GetNames se invoca dos veces cada vez que se crea un objeto PersonInformation. Puede ver que el método se puede optimizar fácilmente creando las listas una sola vez al comienzo del método y creando índices en esas listas durante el bucle de creación de PersonInformation.  
  
4.  Con el código de la aplicación de ejemplo se suministra una versión alternativa de GetPeople. Puede llamar a la función optimizada agregando un símbolo de compilación adicional a las propiedades de compilación. En la ventana del Explorador de soluciones, haga clic con el botón derecho en el proyecto People y después haga clic en **Propiedades**. En el menú de la página de propiedades, haga clic en **General** y escriba **OPTIMIZED_GETPEOPLE** en el cuadro de texto del símbolo de compilación condicional. La versión optimizada de GetPeople reemplazará al método original en la compilación siguiente.  
  
5.  Vuelva a ejecutar la sesión de rendimiento. En la barra de herramientas del Explorador de rendimiento, haga clic en **Iniciar con generación de perfiles**. Haga clic en **Get People** y después en **Exportar datos**. Cierre la ventana del Bloc de notas que aparece y, a continuación, cierre la aplicación People Trax.  
  
     Se genera un nuevo archivo de datos de generación de perfiles y aparece una vista **Resumen** de los nuevos datos en la ventana principal de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  Para comparar las dos generaciones de perfiles, seleccione los dos archivos de datos en el Explorador de rendimiento, haga clic con el botón derecho en los archivos y después haga clic en **Comparar informes de rendimiento**. Se abre una ventana de Informe de comparación en la ventana principal de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. En la columna **Delta** se muestra el cambio en el valor de rendimiento de las funciones entre el valor de **Línea base** anterior y el valor de **Comparación** posterior. Puede seleccionar los valores que se van comparar en la lista desplegable **Columna**. Seleccione **Porcentaje de muestras inclusivas**.  
  
     Observe que los métodos GetNames y GetPeople muestran un aumento de rendimiento considerable.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Generar perfiles utilizando el método de instrumentación  
 La instrumentación es un método de generación de perfiles en el que el generador de perfiles inserta funciones de sondeo en versiones con compilaciones especiales de los archivos binarios perfilados. Los sondeos recopilan información sobre el control de tiempo en la entrada y salida de las funciones de los módulos instrumentados y en todos los sitios de llamada de estas funciones. El proceso de instrumentación resulta útil para analizar problemas relacionados con las operaciones de entrada y salida, como las operaciones de escritura en disco y la comunicación a través de una red. La instrumentación proporciona información más detallada que el muestreo, pero es más intrusiva en la ejecución de procesos y produce una sobrecarga mucho mayor. Los binarios instrumentados también son más grandes que los binarios de depuración o lanzamiento, y no están pensados para su implementación.  
  
 En esta sección del tutorial, usaremos el método de instrumentación para detectar otro código que se pueda optimizar en la aplicación PeopleTrax que perfilamos previamente. Si usamos el filtro de la escala de tiempo de la vista Resumen, centraremos nuestro análisis en los datos exportados en nuestra aplicación perfilada, donde la lista de personas se escribe en un archivo del Bloc de notas.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Para generar perfiles de una aplicación existente utilizando el método de instrumentación  
  
1.  Si es necesario, abra la aplicación PeopleTrax en Visual Studio.  
  
     Asegúrese de que se está ejecutando como administrador y de que la configuración de compilación de la solución está establecida en **Lanzamiento**.  
  
2.  En el Explorador de rendimiento, haga clic en **Instrumentación**.  
  
3.  En la barra de herramientas del Explorador de rendimiento, haga clic en **Iniciar con generación de perfiles**.  
  
     El generador de perfiles compila el proyecto y comienza a perfilar la aplicación. Aparecerá la ventana de la aplicación PeopleTrax.  
  
4.  Haga clic en **Get People**.  
  
     La cuadrícula de datos de PeopleTrax se rellena con datos.  
  
5.  Espere unos 10 segundos y, a continuación, haga clic en **Exportar datos**.  
  
     Se iniciará el **Bloc de notas** con un nuevo archivo que contiene una lista de personas de PeopleTrax. Si espera, le resultará más fácil identificar el procedimiento de exportación de datos de la generación de perfiles.  
  
6.  Cierre el **Bloc de notas** y después cierre la aplicación **PeopleTrax**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] genera un informe de sesión de rendimiento (*.vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Par analizar los resultados de la generación de perfiles mediante instrumentación  
  
1.  En el gráfico de escala de tiempo de la vista **Resumen** del informe, se muestra la utilización de CPU del programa a lo largo de la ejecución de la generación de perfiles. La operación de exportación de datos debería corresponderse con el pico destacado o la altiplanicie que registra la línea a la derecha del gráfico. Podemos filtrar la sesión de rendimiento para mostrar y analizar únicamente los datos recopilados en la operación de exportación. Haga clic a la izquierda del punto del gráfico en el que comienza la operación de exportación de datos. Haga clic de nuevo en el lado derecho de la operación. A continuación, haga clic en **Filtrar por selección** en la lista de vínculos situada a la derecha de la escala de tiempo.  
  
     En el árbol **Ruta de acceso activa**, se muestra que el método <xref:System.String.Concat%2A> invocado por el método PeopleTrax.Form1.ExportData emplea un gran porcentaje de tiempo. Dado que **System.String.Concat** también está en la parte superior de la lista **Funciones con la mayor parte del trabajo individual**, un posible punto de optimización consistiría en reducir el tiempo invertido en la función.  
  
2.  Haga doble clic en **System.String.Concat** en cualquiera de las tablas de resumen para ver más información en la vista Detalles de la función.  
  
3.  Puede ver que PeopleTrax.Form1.ExportData es el único método que llama a Concat. Haga clic en **PeopleTrax.Form1.ExportData** en la lista **Funciones que llaman** para seleccionar el método que actúa como destino de la vista Detalles de la función.  
  
4.  Examine el método en la ventana Vista de código de función. Observe que no hay llamadas literales a **System.String.Concat**. En su lugar, se usa varias veces el operando +=, que el compilador reemplaza por llamadas a **System.String.Concat**. Cualquier modificación de una cadena en .NET Framework provoca la asignación de una nueva cadena. .NET Framework incluye una clase <xref:System.Text.StringBuilder> que está optimizada para la concatenación de cadenas  
  
5.  Para reemplazar esta área de problema con código optimizado, agregue OPTIMIZED_EXPORTDATA como símbolo de compilación condicional al proyecto PeopleTrax.  
  
6.  En el Explorador de soluciones, haga clic con el botón derecho en el proyecto PeopleTrax y después haga clic en **Propiedades**.  
  
     Aparece el formulario de propiedades del proyecto PeopleTrax.  
  
7.  Haga clic en la pestaña **Compilar**.  
  
8.  En el cuadro de texto **Símbolos de compilación condicional**, escriba **OPTIMIZED_EXPORTDATA**.  
  
9. Cierre el formulario de propiedades del proyecto y elija **Guardar todo** cuando se le pregunte.  
  
 Cuando vuelva a ejecutar la aplicación, observará que el rendimiento ha mejorado de manera clara. Se recomienda que ejecute de nuevo la sesión de generación de perfiles, aunque haya mejoras de rendimiento visibles para el usuario. Es importante revisar los datos después de corregir un problema por si el primer problema ocultaba algún otro.  
  
## <a name="see-also"></a>Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Introducción](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Formato de la información de depuración)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)
