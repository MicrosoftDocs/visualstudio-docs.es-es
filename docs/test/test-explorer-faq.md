---
title: Preguntas frecuentes del Explorador de pruebas | Microsoft Docs
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Preguntas frecuentes del Explorador de pruebas de Visual Studio

## <a name="test-discovery"></a>Detección de pruebas

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1. El Explorador de pruebas no detecta las pruebas que tienen teorías, adaptadores personalizados o rasgos personalizados, que usan #ifdefs o que están definidas dinámicamente. ¿Cómo puedo detectar estas pruebas?

  Compile el proyecto y asegúrese de que está activada la detección basada en ensamblados en **Herramientas > Opciones > Prueba**.

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824), que es una detección de pruebas basada en el origen, no puede detectar pruebas que usan teorías, adaptadores personalizados, rasgos personalizados o instrucciones `#ifdef`, o que están definidas dinámicamente de alguna otra manera. Se requiere una compilación para que estas pruebas se puedan detectar con precisión. En las versiones preliminares de la versión 15.6, la detección basada en ensamblados (el detector tradicional) se ejecuta solo tras las compilaciones. Esto significa que la detección de pruebas en tiempo real detecta tantas pruebas como sea posible mientras está editando, y la detección basada en ensamblados permite que aparezcan teorías (o cualquier prueba definida dinámicamente) después de una compilación. La detección de pruebas en tiempo real mejora la capacidad de respuesta, pero sigue permitiendo la obtención de resultados completos y precisos tras una compilación.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. ¿Qué significa el signo "+" (más) que aparece en la línea superior del Explorador de pruebas?

  El signo "+" (más) indica que se pueden detectar más pruebas después de una compilación si se activa la detección basada en ensamblados. Aparecerá si se detectan pruebas definidas dinámicamente en el proyecto.

  ![Línea de resumen del signo más](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. La detección basada en ensamblados ha dejado de funcionar en mi proyecto. ¿Cómo puedo volver a activarla?

  Vaya a **Herramientas > Opciones > Prueba** y active la casilla **Additionally discover tests built from assemblies after builds** (Detectar adicionalmente pruebas compiladas de ensamblados tras las compilaciones).

  ![Opción basada en ensamblados](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Ahora aparecen pruebas en el Explorador de pruebas mientras escribo, sin tener que compilar el proyecto. ¿Qué ha cambiado?

  Esta característica se denomina "[detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824)". Utiliza un analizador de Roslyn para detectar pruebas y rellenar el Explorador de pruebas en tiempo real sin necesidad de que compile el proyecto. Para obtener más información acerca del comportamiento de la detección de pruebas para pruebas definidas dinámicamente, como teorías o rasgos personalizados, consulte la pregunta frecuente núm. 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. ¿Los lenguajes y marcos de pruebas pueden utilizar la detección de pruebas en tiempo real?

  La [detección de pruebas en tiempo real](https://go.microsoft.com/fwlink/?linkid=862824) solo funciona en los lenguajes administrados (C# y Visual Basic), porque se ha creado mediante el compilador Roslyn. Por ahora, la detección de pruebas en tiempo real solo funciona en los marcos xUnit, NUnit y MSTest.

## <a name="features"></a>Características

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>¿Cómo puedo activar las marcas de características para probar las nuevas características de las pruebas?

Las marcas de características se utilizan para enviar partes experimentales o inacabadas del producto a los usuarios entusiastas que desean ofrecer comentarios al respecto antes de que las características se publiquen oficialmente. Pueden llegar a desestabilizar su experiencia IDE. Se recomienda usarlas solo en entornos de desarrollo seguro, como máquinas virtuales. Las marcas de características deben utilizarse siempre bajo su propia responsabilidad. Puede activar las características experimentales con la [extensión Marcas de características](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), o mediante el símbolo del sistema para desarrolladores.

![Extensión Marcas de características](media/testex-featureflag.png)

Para activar una marca de características a través de la línea de comandos para desarrolladores de Visual Studio, utilice el siguiente comando. Cambie la ruta de acceso de la instalación de Visual Studio en su equipo y cambie la clave del Registro a la marca de características deseada.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Puede desactivar la marca con el mismo comando, utilizando un valor de 0 en lugar de 1 después de dword.
  
## <a name="see-also"></a>Vea también

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Crear y ejecutar pruebas unitarias para código existente](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[Haga una prueba unitaria de su código](unit-test-your-code.md)
[Preguntas más frecuentes sobre Live Unit Testing](live-unit-testing-faq.md)
