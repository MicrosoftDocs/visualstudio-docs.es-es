---
title: Solución de problemas de cobertura de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660373"
---
# <a name="troubleshooting-code-coverage"></a>Solucionar problemas de cobertura de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta de análisis de cobertura de código de Visual Studio recopila datos para ensamblados nativos y administrados (archivos .dll o .exe). Sin embargo, en algunos casos, la ventana Resultados de la cobertura de código muestra un error similar a "resultados vacíos generados:...." Hay varias razones posibles por las que esto puede ocurrir. Este tema está diseñado para ayudar a resolver esos problemas.

## <a name="what-you-should-see"></a>Qué debe ver
 Si se elige un comando **Analizar cobertura de código** en el menú Prueba, y si la compilación y las pruebas se ejecutan correctamente, debería ver una lista de resultados en la ventana Cobertura de código. Es posible que tenga que expandir los elementos para ver los detalles.

 ![Resultados de cobertura de código con colores](../test/media/codecoverage1.png "CodeCoverage1")

 Para obtener más información, consulte [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Causas posibles para no ver ningún resultado o ver resultados antiguos

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>¿Tiene la edición correcta de Visual Studio?
 Necesita Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>No se ejecutó ninguna prueba
 Análisis Compruebe la ventana de salida. En la lista desplegable **Mostrar resultados desde**, elija **Pruebas**. Compruebe si hay advertencias o errores registrados.

 Explicación el análisis de la cobertura de código se realiza mientras se ejecutan las pruebas. Solo incluye los ensamblados cargados en memoria cuando se ejecutan las pruebas. Si no se ejecuta ninguna de las pruebas, no hay nada que notificar con respecto a la cobertura de código.

 Resolución en el explorador de pruebas, elija **ejecutar todas** para comprobar que las pruebas se ejecutaron correctamente. Corrija cualquier error antes de usar **Analizar cobertura de código**.

### <a name="youre-looking-at-a-previous-result"></a>Está viendo un resultado anterior
 Cuando se modifican y se vuelven a ejecutar las pruebas, todavía puede estar visible un resultado de cobertura de código anterior, incluido el color del código de esa ejecución anterior.

1. Ejecute Analizar cobertura de código.

2. Asegúrese de que ha seleccionado el conjunto de resultados más reciente en la ventana de resultados de cobertura de código.

### <a name="pdb-symbol-files-are-unavailable"></a>Los archivos .pdb (símbolo) no están disponibles
 Análisis Abra la carpeta de destino de la compilación (normalmente bin\Debug) y compruebe que, para cada ensamblado, hay un archivo. pdb en el mismo directorio que el archivo. dll o. exe.

 Explicación el motor de cobertura de código requiere que cada ensamblado tenga su archivo. pdb asociado accesible durante la ejecución de pruebas. Si no hay ningún archivo .pdb para un ensamblado determinado, este no se analizará.

 El archivo .pdb se debe generar a partir de la misma compilación que los archivos .dll o .exe.

 Resolución Asegúrese de que la configuración de compilación genere el archivo. pdb. Si los archivos. pdb no se actualizan cuando se compila el proyecto, abra las propiedades del proyecto, seleccione la página **compilación** , elija **avanzadas** e inspeccione **información de depuración**.

 Si los archivos .pdb y .dll o .exe están en distintos lugares, copie el archivo .pdb en el mismo directorio. También es posible configurar el motor de cobertura de código para que busque archivos .pdb en otra ubicación. Para obtener más información, consulte [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Usar un binario instrumentado u optimizado
 El análisis determina si el binario ha experimentado algún tipo de optimización avanzada, como la optimización guiada por perfiles, o si se ha instrumentado mediante una herramienta de generación de perfiles como vsinstr.exe o vsperfmon.exe.

 Explicación si otra herramienta de generación de perfiles ya ha instrumentado u optimizado un ensamblado, el ensamblado se omite en el análisis de cobertura de código.

 El análisis de cobertura de código no se puede realizar en dichos ensamblados.

 Resolución: Desactive la optimización y use una nueva compilación.

### <a name="code-is-not-managed-net-or-native-c-code"></a>El código no es administrado (.NET) o nativo (C++)
 Análisis Compruebe que se están ejecutando algunas pruebas en el código administrado o en C++.

 Explicación el análisis de la cobertura de código en Visual Studio solo está disponible en código administrado y nativo (C++). Si trabaja con herramientas de terceros, puede que parte del código, o todo, se ejecute en una plataforma diferente.

 Resolución ninguno disponible.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen ha instalado el ensamblado
 Análisis Compruebe que el ensamblado no se carga desde la memoria caché de imágenes nativas.

 Explicación por motivos de rendimiento, los ensamblados de imágenes nativas no se analizan. Para obtener más información, vea el artículo sobre [Ngen.exe (generador de imágenes nativas)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 La resolución usa una versión MSIL del ensamblado. No lo procese con NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Archivo .runsettings personalizado con sintaxis incorrecta
 Análisis si usa un archivo. runsettings personalizado, puede que contenga un error de sintaxis.

 Como resultado, no se ejecuta ninguna cobertura de código. La ventana de cobertura de código no se abre al final de la serie de pruebas o muestra resultados antiguos.

 Explicación puede ejecutar las pruebas unitarias con un archivo. runsettings personalizado para configurar las opciones de cobertura de código. Las opciones permiten incluir o excluir archivos. Para obtener más información, consulte [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

 Resolución: hay dos posibles tipos de errores:

- **Error de XML**

     Abra el archivo .runsettings en el editor XML de Visual Studio. Busque las indicaciones del error.

- **Error de expresión regular**

  Cada cadena del archivo es una expresión regular. Revise cada una de ellas en busca de errores y, en particular, busque:

  - Paréntesis no coincidentes (...) o paréntesis sin escape \\(...\\). Si desea asociar un paréntesis en la cadena de búsqueda, debe indicar su secuencia de escape. Por ejemplo, para hacer coincidir una función, use: `.*MyFunction\(double\)`

  - Asterisco o signo más al principio de una expresión. Para asociar cualquier cadena de caracteres, use un punto seguido de un asterisco: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Archivo .runsettings personalizado con exclusiones incorrectas
 Análisis si usa un archivo. runsettings personalizado, asegúrese de que incluye el ensamblado.

 Explicación puede ejecutar las pruebas unitarias con un archivo. runsettings personalizado para configurar las opciones de cobertura de código. Las opciones permiten incluir o excluir archivos. Para obtener más información, consulte [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

 Resolución quite todos los `Include` nodos del archivo. runsettings y, a continuación, quite todos los `Exclude` nodos. Si eso corrige el problema, vuelva a colocarlos en fases.

 Asegúrese de que el nodo DataCollectors especifica la cobertura de código. Compárelo con el ejemplo de [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Siempre se muestra algún código como no cubierto

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>El código de inicialización de archivos DLL nativos se ejecuta antes de la instrumentación
 Análisis en código nativo vinculado estáticamente, parte de la función de inicialización **DllMain** y el código al que llama se muestran a veces como no incluidos, aunque se haya ejecutado el código.

 Explicación la herramienta de cobertura de código funciona insertando la instrumentación en un ensamblado justo antes de que se inicie la ejecución de la aplicación. En cualquier ensamblado cargado antes de ese momento, el código de inicialización de **DllMain** se ejecuta tan pronto como se carga el ensamblado y antes de que se ejecute la aplicación. Ese código aparecerá como no cubierto.

 Normalmente, esto se aplica a los ensamblados cargados estáticamente.

 Resolución ninguno.

## <a name="see-also"></a>Consulte también
 [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
