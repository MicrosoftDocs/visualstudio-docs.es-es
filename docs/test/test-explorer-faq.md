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
ms.openlocfilehash: 151f60d21914168ea62bdb2d978d93839c8b859b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975633"
---
# <a name="visual-studio-test-explorer-faq"></a>Preguntas frecuentes del Explorador de pruebas de Visual Studio

## <a name="test-discovery"></a>Detección de pruebas

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. El Explorador de pruebas no detecta las pruebas que están definidas dinámicamente (por ejemplo, teorías, adaptadores personalizados, rasgos personalizados, #ifdefs, etc.) ¿Cómo puedo detectar estas pruebas?

  Compile el proyecto y asegúrese de que está activada la detección basada en ensamblados en **Herramientas > Opciones > Prueba**.

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824) es la detección de pruebas basada en el origen. No puede detectar las pruebas que usan teorías, adaptadores personalizados, rasgos personalizados, instrucciones `#ifdef`, etc. porque ya están definidas en tiempo de ejecución. Se requiere una compilación para que estas pruebas se puedan detectar con precisión. En las versiones preliminares de la versión 15.6, la detección basada en ensamblados (el detector tradicional) se ejecuta solo tras las compilaciones. Esta opción significa que la detección de pruebas en tiempo real detecta tantas pruebas como sea posible mientras está editando, y la detección basada en ensamblados permite que aparezcan teorías (o cualquier prueba definida dinámicamente) después de una compilación. La detección de pruebas en tiempo real mejora la capacidad de respuesta, pero sigue permitiendo la obtención de resultados completos y precisos tras una compilación.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. ¿Qué significa el signo "+" (más) que aparece en la línea superior del Explorador de pruebas?

  El signo "+" (más) indica que se pueden detectar más pruebas después de una compilación siempre y cuando la detección basada en ensamblados esté activada. Aparece si se detectan pruebas definidas dinámicamente en el proyecto.

  ![Línea de resumen del signo más](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. La detección basada en ensamblados ha dejado de funcionar en mi proyecto. ¿Cómo puedo volver a activarla?

  Vaya a **Herramientas > Opciones > Prueba** y active la casilla **Detectar también las pruebas de los ensamblados compilados después de las compilaciones**.

  ![Opción basada en ensamblados](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Ahora aparecen pruebas en el Explorador de pruebas mientras escribo, sin tener que compilar el proyecto. ¿Qué ha cambiado?

  Esta característica se denomina "[detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824)". Utiliza un analizador de Roslyn para detectar pruebas y rellenar el Explorador de pruebas en tiempo real sin necesidad de que compile el proyecto. Vea la pregunta frecuente n.º 1 para más información sobre el comportamiento de la detección de pruebas en las pruebas definidas dinámicamente, como teorías o rasgos personalizados.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. ¿Los lenguajes y marcos de pruebas pueden utilizar la detección de pruebas en tiempo real?

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824) solo funciona en los lenguajes administrados (C# y Visual Basic), porque se ha creado mediante el compilador Roslyn. Por ahora, la detección de pruebas en tiempo real solo funciona en los marcos xUnit, NUnit y MSTest.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. ¿Cómo puedo activar los registros del Explorador de pruebas?

  Vaya a **Herramientas > Opciones > Prueba** y busque la sección Registro ahí.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. ¿Por qué las pruebas de los proyectos de UWP no se detectan hasta que implemento la aplicación?

  Las pruebas de UWP tienen como destino un tiempo de ejecución distinto cuando la aplicación se implementa. Esto significa que, para detectar las pruebas de proyectos de UWP con exactitud, no solo debe compilar el proyecto, sino también implementarlo.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. ¿Cómo funciona la ordenación de los resultados de las pruebas en la vista de jerarquía?

  En la vista de jerarquía, las pruebas se ordenan alfabéticamente, y no por su resultado. Normalmente, la otra configuración de agrupamiento suele ordenar las pruebas por resultados y, después, alfabéticamente. Vea los diferentes grupos por opciones en la imagen siguiente para establecer comparaciones. Puede dejar sus comentarios sobre el diseño [en este problema de GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![Ejemplos de ordenación](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9. En la vista de jerarquía, hay iconos de pasados, con errores, omitidos y no ejecutados junto a los grupos Proyecto, Espacio de nombres y Clase. ¿Qué significan estos iconos?

  Los iconos situados junto a los grupos Proyecto, Espacio de nombres y Clase reflejan el estado de las pruebas dentro de esa agrupación. Vea la siguiente tabla.

  ![Iconos de jerarquía del Explorador de pruebas](media/testex-hierarchyicons.png)
  
### <a name="10-there-is-no-longer-a-file-path-filter-in-the-test-explorer-search-box"></a>10. Ya no hay un filtro "Ruta de acceso de archivo" en el cuadro de búsqueda del Explorador de pruebas.

El filtro de ruta de acceso de archivo en el cuadro de búsqueda **Explorador de pruebas** se quitó en Visual Studio de 2017, versión 15.7 y presentación preliminar 3. Esta característica tenía poca utilización y el Explorador de pruebas puede recuperar los métodos de prueba más rápido excluyendo esta característica. Si este cambio interrumpe el flujo de desarrollo, háganoslo saber enviándonos sus comentarios a la [comunidad de desarrolladores](https://developercommunity.visualstudio.com/).

## <a name="features"></a>Características

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>¿Cómo puedo activar las marcas de características para probar las nuevas características de las pruebas?

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
- [Crear y ejecutar pruebas unitarias para código existente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Haga una prueba unitaria de su código](unit-test-your-code.md)
- [Preguntas más frecuentes de Live Unit Testing](live-unit-testing-faq.md)
