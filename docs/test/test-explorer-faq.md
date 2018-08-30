---
title: Preguntas frecuentes del Explorador de pruebas de Visual Studio
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: douge
ms.openlocfilehash: 4ac7aa7d9fbbf4e6f6ffbe5eafd82ff8f1e0bc44
ms.sourcegitcommit: e04e52bddf81239ad346efb4797f52e38de5cb98
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43054561"
---
# <a name="visual-studio-test-explorer-faq"></a>Preguntas frecuentes del Explorador de pruebas de Visual Studio

## <a name="dynamic-test-discovery"></a>Detección de pruebas dinámicas
**El Explorador de pruebas no detecta las pruebas que están definidas dinámicamente (por ejemplo, teorías, adaptadores personalizados, rasgos personalizados, #ifdefs, etc.) ¿Cómo puedo detectar estas pruebas?**

  Compile el proyecto y asegúrese de que está activada la detección basada en ensamblados en **Herramientas** > **Opciones** > **Prueba**.

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824) es la detección de pruebas basada en el origen. No puede detectar las pruebas que usan teorías, adaptadores personalizados, rasgos personalizados, instrucciones `#ifdef`, etc. porque ya están definidas en tiempo de ejecución. Se requiere una compilación para que estas pruebas se puedan detectar con precisión. En las versiones preliminares de la versión 15.6, la detección basada en ensamblados (el detector tradicional) se ejecuta solo tras las compilaciones. Esta opción significa que la detección de pruebas en tiempo real detecta tantas pruebas como sea posible mientras está editando, y la detección basada en ensamblados permite que aparezcan teorías (o cualquier prueba definida dinámicamente) después de una compilación. La detección de pruebas en tiempo real mejora la capacidad de respuesta, pero sigue permitiendo la obtención de resultados completos y precisos tras una compilación.

## <a name="test-explorer--plus-symbol"></a>Signo "+" (más) en el Explorador de pruebas
**¿Qué significa el signo "+" (más) que aparece en la línea superior del Explorador de pruebas?**

  El signo "+" (más) indica que se pueden detectar más pruebas después de una compilación siempre y cuando la detección basada en ensamblados esté activada. Aparece si se detectan pruebas definidas dinámicamente en el proyecto.

  ![Línea de resumen del signo más](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Detección basada en ensamblados
**La detección basada en ensamblados ha dejado de funcionar en mi proyecto. ¿Cómo puedo volver a activarla?**

  Vaya a **Herramientas** > **Opciones** > **Prueba** y active la casilla **Detectar también las pruebas de los ensamblados compilados después de las compilaciones**.

  ![Opción basada en ensamblados](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Detección de pruebas en tiempo real
**Ahora aparecen pruebas en el Explorador de pruebas mientras escribo, sin tener que compilar el proyecto. ¿Qué ha cambiado?**

  Esta característica se denomina [Detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824). Utiliza un analizador de Roslyn para detectar pruebas y rellenar el Explorador de pruebas en tiempo real sin necesidad de que compile el proyecto. Vea la pregunta frecuente n.º 1 para más información sobre el comportamiento de la detección de pruebas en las pruebas definidas dinámicamente, como teorías o rasgos personalizados.

## <a name="real-time-test-discovery-compatibility"></a>Compatibilidad de detección de pruebas en tiempo real
**¿Los lenguajes y marcos de pruebas pueden utilizar la detección de pruebas en tiempo real?**

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824) solo funciona en los lenguajes administrados (C# y Visual Basic), porque se ha creado mediante el compilador Roslyn. Por ahora, la detección de pruebas en tiempo real solo funciona en los marcos xUnit, NUnit y MSTest.

## <a name="test-explorer-logs"></a>Registros del Explorador de pruebas
**¿Cómo puedo activar los registros del Explorador de pruebas?**

  Vaya a **Herramientas** > **Opciones** > **Prueba** y busque ahí la sección Registro.

## <a name="uwp-test-discovery"></a>Detección de pruebas de UWP
**¿Por qué las pruebas de los proyectos de UWP no se detectan hasta que implemento la aplicación?**

  Las pruebas de UWP tienen como destino un tiempo de ejecución distinto cuando la aplicación se implementa. Esto significa que, para detectar las pruebas de proyectos de UWP con exactitud, no solo debe compilar el proyecto, sino también implementarlo.

## <a name="test-explorer-sorting"></a>Ordenación del Explorador de pruebas
**¿Cómo funciona la ordenación de los resultados de las pruebas en la vista de jerarquía?**

  En la vista de jerarquía, las pruebas se ordenan alfabéticamente, y no por su resultado. Normalmente, la otra configuración de agrupamiento suele ordenar las pruebas por resultados y, después, alfabéticamente. Vea los diferentes grupos por opciones en la imagen siguiente para establecer comparaciones. Puede dejar sus comentarios sobre el diseño [en este problema de GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![Ejemplos de ordenación](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Vista de jerarquía del Explorador de pruebas
**En la vista de jerarquía, hay iconos de pasados, con errores, omitidos y no ejecutados junto a los grupos Proyecto, Espacio de nombres y Clase. ¿Qué significan estos iconos?**

  Los iconos situados junto a los grupos Proyecto, Espacio de nombres y Clase reflejan el estado de las pruebas dentro de esa agrupación. Vea la siguiente tabla.

  ![Iconos de jerarquía del Explorador de pruebas](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Búsqueda por ruta de acceso de archivo
**Ya no hay un filtro "Ruta de acceso de archivo" en el cuadro de búsqueda del Explorador de pruebas.**

El filtro de ruta de acceso de archivo en el cuadro de búsqueda **Explorador de pruebas** se quitó en Visual Studio de 2017, versión 15.7 y presentación preliminar 3. Esta característica tenía poca utilización y el Explorador de pruebas puede recuperar los métodos de prueba más rápido excluyendo esta característica. Si este cambio interrumpe el flujo de desarrollo, háganoslo saber enviando sus comentarios a la [comunidad de desarrolladores](https://developercommunity.visualstudio.com/).

## <a name="test-adapter-nuget-reference"></a>Referencia de NuGet del adaptador de prueba
**En la versión 15.8 de Visual Studio 2017 mis pruebas se detectan, pero no se ejecutan.**

Todos los proyectos de prueba deben incluir la referencia de NuGet del adaptador de prueba de .NET en su archivo csproj. Si no lo incluyen, aparece la siguiente salida de prueba en el proyecto si la detección de una extensión de adaptador de prueba se inicia después de una compilación o si el usuario intenta ejecutar las pruebas seleccionadas: 

**El proyecto de prueba {} no hace referencia a ningún adaptador NuGet de .NET. La detección o ejecución de pruebas podría no funcionar para este proyecto. Se recomienda hacer referencia a los adaptadores de prueba de NuGet en cada proyecto de prueba de .NET de la solución.**

En lugar de usar las extensiones del adaptador de prueba, los proyectos deben usar paquetes de NuGet del adaptador de prueba. Esto mejora el rendimiento considerablemente y hace que se reduzcan los problemas con la integración continua. Obtenga más información sobre la depreciación de la extensión del adaptador de prueba de .NET en las [notas de la versión](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

## <a name="using-feature-flags"></a>Uso de marcas de características
**¿Cómo puedo activar las marcas de características para probar las nuevas características de las pruebas?**

Las marcas de características se utilizan para enviar partes experimentales o inacabadas del producto a los usuarios entusiastas que desean ofrecer comentarios al respecto antes de que las características se publiquen oficialmente. Pueden llegar a desestabilizar su experiencia IDE. Úselas solo en entornos de desarrollo seguro, como máquinas virtuales. Las marcas de características deben utilizarse siempre bajo su propia responsabilidad. Puede activar las características experimentales con la [extensión Marcas de características](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), o mediante el símbolo del sistema para desarrolladores.

![Extensión Marcas de características](media/testex-featureflag.png)

Para activar una marca de características a través de la línea de comandos para desarrolladores de Visual Studio, utilice el siguiente comando. Cambie la ruta de acceso de la instalación de Visual Studio en su equipo y cambie la clave del Registro a la marca de características deseada.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Puede desactivar la marca con el mismo comando, utilizando un valor de 0 en lugar de 1 después de dword.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) (Crear y ejecutar pruebas unitarias en código existente)
- [Haga una prueba unitaria de su código](unit-test-your-code.md)
- [Preguntas más frecuentes sobre Live Unit Testing](live-unit-testing-faq.md)
