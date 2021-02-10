---
title: Preguntas más frecuentes sobre el Explorador de pruebas
description: Consulte estas preguntas más frecuentes sobre el Explorador de pruebas de Visual Studio, entre las que se incluyen algunas soluciones de problemas comunes.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
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
manager: jmartens
ms.openlocfilehash: a1e0f998b5fff45a8fee9ac6f9cc6a0ce2268907
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894470"
---
# <a name="visual-studio-test-explorer-faq"></a>Preguntas frecuentes del Explorador de pruebas de Visual Studio

## <a name="dynamic-test-discovery"></a>Detección de pruebas dinámicas

**El Explorador de pruebas no detecta las pruebas definidas dinámicamente (por ejemplo, teorías, adaptadores personalizados, rasgos personalizados, #ifdefs, etc.) ¿Cómo puedo detectar estas pruebas?**

::: moniker range=">=vs-2019"
Compile el proyecto para ejecutar la detección basada en ensamblados.
::: moniker-end
::: moniker range="vs-2017"
Compile el proyecto y asegúrese de que está activada la detección basada en ensamblados en **Herramientas** > **Opciones** > **Prueba**.
::: moniker-end
La [detección de pruebas en tiempo real](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) es la detección de pruebas basada en el origen. No puede detectar las pruebas que usan teorías, adaptadores personalizados, rasgos personalizados, instrucciones `#ifdef`, etc., porque ya están definidas en tiempo de ejecución. Se requiere una compilación para que estas pruebas se puedan detectar con precisión. En las versiones 15.6 y posteriores de Visual Studio 2017, la detección basada en ensamblados (el detector tradicional) se ejecuta solo tras las compilaciones. Esta opción significa que la detección de pruebas en tiempo real detecta tantas pruebas como sea posible mientras está editando, y la detección basada en ensamblados permite que aparezcan pruebas definidas dinámicamente después de una compilación. La detección de pruebas en tiempo real mejora la capacidad de respuesta, pero sigue permitiendo la obtención de resultados completos y precisos tras una compilación.

## <a name="test-explorer--plus-symbol"></a>Signo "+" (más) en el Explorador de pruebas

**¿Qué significa el signo "+" (más) que aparece en la línea superior del Explorador de pruebas?**

El signo "+" (más) indica que se pueden detectar más pruebas después de una compilación cuando se lleva a cabo una detección basada en ensamblados. Este símbolo aparece si se detectan pruebas definidas dinámicamente en el proyecto.

![Línea de resumen del signo más](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Detección basada en ensamblados

**La detección basada en ensamblados ha dejado de funcionar en mi proyecto. ¿Cómo puedo volver a activarla?**

Vaya a **Herramientas** > **Opciones** > **Prueba** y active la casilla **Detectar también las pruebas de los ensamblados compilados después de las compilaciones**.

![Opción basada en ensamblados](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Detección de pruebas en tiempo real

**Ahora aparecen pruebas en el Explorador de pruebas mientras escribo, sin tener que compilar el proyecto. ¿Qué ha cambiado?**

Esta característica se denomina [Detección de pruebas en tiempo real](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Usa un analizador de Roslyn para detectar pruebas y rellenar el Explorador de pruebas en tiempo real sin necesidad de que se compile el proyecto. Para más información sobre el comportamiento de la detección de pruebas en las pruebas definidas dinámicamente, como teorías o rasgos personalizados, vea [Detección de pruebas dinámicas](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Compatibilidad de la detección de pruebas en tiempo real

**¿Los lenguajes y marcos de pruebas pueden utilizar la detección de pruebas en tiempo real?**

La [detección de pruebas en tiempo real](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) solo funciona con los lenguajes administrados (C# y Visual Basic), porque se ha compilado mediante el compilador Roslyn. Por ahora, la detección de pruebas en tiempo real solo funciona con los marcos xUnit, NUnit y MSTest.

## <a name="test-explorer-logs"></a>Registros del Explorador de pruebas

**¿Cómo puedo activar los registros del Explorador de pruebas?**

Vaya a **Herramientas** > **Opciones** > **Prueba** y busque ahí la sección Registro.

## <a name="uwp-test-discovery"></a>Detección de pruebas de UWP

**¿Por qué las pruebas de los proyectos de UWP no se detectan hasta que implemento la aplicación?**

Las pruebas de UWP tienen como destino un tiempo de ejecución distinto cuando la aplicación se implementa. Esto significa que, para detectar las pruebas de proyectos de UWP de forma precisa, no solo debe compilar el proyecto, sino también implementarlo.

## <a name="test-explorer-sorting"></a>Ordenación del Explorador de pruebas

**¿Cómo funciona la ordenación de los resultados de las pruebas en la vista de jerarquía?**

En la vista de jerarquía, las pruebas se ordenan alfabéticamente, y no por su resultado. La configuración de agrupamiento anterior ha ordenado las pruebas por resultados y, después, alfabéticamente. Todavía puede habilitar la ordenación por resultados si hace clic con el botón derecho en el encabezado de columna en el Explorador de pruebas, habilita la columna Estado y, después, hace clic en el encabezado de la columna Estado para aplicar la ordenación por esa columna. Puede proporcionar comentarios sobre el diseño en esta [incidencia de GitHub](https://github.com/Microsoft/vstest/issues/1425).

## <a name="test-explorer-hierarchy-view"></a>Vista de jerarquía del Explorador de pruebas

**En la vista de jerarquía, hay iconos de pruebas superadas, no superadas, omitidas y no ejecutadas junto a las agrupaciones de nodo primario. ¿Qué significan estos iconos?**

Los iconos situados junto a los grupos Proyecto, Espacio de nombres y Clase reflejan el estado de las pruebas de ese grupo. Vea la siguiente tabla.

![Iconos de jerarquía del Explorador de pruebas](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Búsqueda por ruta de acceso de archivo

**Ya no hay un filtro "Ruta de acceso de archivo" en el cuadro de búsqueda del Explorador de pruebas.**

El filtro de ruta de acceso de archivo del cuadro de búsqueda **Explorador de pruebas** se ha quitado en Visual Studio de 2017 versión 15.7. Esta característica se usaba poco y el Explorador de pruebas puede recuperar los métodos de prueba más rápido al excluirla. Si este cambio interrumpe el flujo de desarrollo, háganoslo saber enviando sus comentarios a la [Comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=8).

## <a name="remove-undocumented-interfaces"></a>Eliminación de interfaces no documentadas

**Algunas API relacionadas con las pruebas ya no están presentes en Visual Studio de 2019. ¿Qué ha cambiado?**

En Visual Studio 2019, se quitará alguna ventana de prueba de API que anteriormente se han marcado como públicas pero nunca se documentaron oficialmente. Se marcaron como "obsoletas" en Visual Studio 2017 para proporcionar advertencias prematuras a los mantenedores de extensiones. Que nosotros sepamos, muy pocas extensiones encontraron estas API y tenían una dependencia en ellas. Entre estas se incluyen `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken` y `SearchFilterTokenType`. Si este cambio afecta a su extensión, háganoslo saber enviando un error a la [Comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Referencia de NuGet del adaptador de prueba

**En la versión 15.8 de Visual Studio 2017 mis pruebas se detectan, pero no se ejecutan.**

Todos los proyectos de prueba deben incluir la referencia de NuGet del adaptador de prueba de .NET en su archivo csproj. Si no lo incluyen, aparece la siguiente salida de prueba en el proyecto si la detección de una extensión de adaptador de prueba se inicia después de una compilación o si el usuario intenta ejecutar las pruebas seleccionadas:

**El proyecto de prueba {} no hace referencia a ningún adaptador NuGet de .NET. La detección o ejecución de pruebas podría no funcionar para este proyecto. Se recomienda hacer referencia a los adaptadores de prueba de NuGet en cada proyecto de prueba de .NET de la solución.**

En lugar de usar las extensiones del adaptador de prueba, los proyectos deben usar paquetes de NuGet del adaptador de prueba. Este requisito mejora el rendimiento considerablemente y hace que se reduzcan los problemas con la integración continua. Obtenga más información sobre la depreciación de la extensión del adaptador de prueba de .NET en las [notas de la versión](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Si usa NUnit 2 Test Adapter y no puede migrar a NUnit 3 Test Adapter, puede desactivar este nuevo comportamiento de detección en la versión 15.8 de Visual Studio en **Herramientas** > **Opciones** > **Prueba**.

![Comportamiento del adaptador de explorador de pruebas en las opciones de las herramientas](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>No se encuentra TestContainer de UWP

**Ya no se ejecutan las pruebas de UWP en Visual Studio 2017 versión 15.7 y posteriores.**

Los proyectos de prueba recientes de UWP especifican una propiedad de compilación de plataforma de prueba que permite un mejor rendimiento para identificar las aplicaciones de prueba. Si tiene un proyecto de prueba de UWP que se haya inicializado antes de Visual Studio versión 15.7, puede ver este error en **Salida** > **Pruebas**:

**System.AggregateException: Se produjeron uno o varios errores. ---> System.InvalidOperationException: No se encontró el siguiente TestContainer {} en Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

Para corregir este error:

- Actualice la propiedad de compilación del proyecto de prueba con el siguiente código:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Actualice la versión del SDK de TestPlatform con el siguiente código:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Uso de características en versión preliminar

En Visual Studio 2019, puede participar en las características en versión preliminar en **Herramientas > Opciones > Entorno > Características en versión preliminar**.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Uso de marcas de características

**¿Cómo puedo activar las marcas de características para probar las nuevas características de las pruebas?**

Las marcas de características se utilizan para enviar partes experimentales o inacabadas del producto a los usuarios entusiastas que desean ofrecer comentarios al respecto antes de que las características se publiquen oficialmente. Pueden llegar a desestabilizar su experiencia IDE. Úselas solo en entornos de desarrollo seguro, como máquinas virtuales. Las marcas de características deben utilizarse siempre bajo su propia responsabilidad. Puede activar las características experimentales con la [extensión Marcas de características](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), o mediante el símbolo del sistema para desarrolladores.

![Extensión Marcas de características](media/testex-featureflag.png)

Para activar una marca de características a través de la línea de comandos para desarrolladores de Visual Studio, utilice el siguiente comando. Cambie la ruta de acceso de la instalación de Visual Studio en el equipo y cambie la clave del Registro a la marca de características que quiera.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Puede desactivar la marca con el mismo comando, utilizando un valor de 0 en lugar de 1 después de dword.
::: moniker-end
## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code](/previous-versions/dd293546(v=vs.110)) (Crear y ejecutar pruebas unitarias en código existente)
- [Haga una prueba unitaria de su código](unit-test-your-code.md)
- [Preguntas más frecuentes sobre Live Unit Testing](live-unit-testing-faq.md)