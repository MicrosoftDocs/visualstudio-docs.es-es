---
title: Introducción a IntelliTest
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3e33bab90c32ca1b7cd92714218e5694daa22aed
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000744"
---
# <a name="get-started-with-microsoft-intellitest"></a>Introducción a Microsoft IntelliTest

* Si es la primera vez que usa IntelliTest:
  * vea el [vídeo de Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * lea esta [información general de MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * lea nuestra [documentación](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Escriba preguntas en [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest).
* Lea el resto de este manual de referencia
* Imprima esta página como referencia rápida

## <a name="important-attributes"></a>Atributos importantes

* [PexClass](attribute-glossary.md#pexclass) marca un tipo que contiene **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marca **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marca un parámetro que no es NULL

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) enlaza un proyecto de prueba a un proyecto
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) especifica un ensamblado que se va a instrumentar

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> clases del asistente estáticas importantes

* [PexAssume](static-helper-classes.md#pexassume) evalúa hipótesis (filtrado de entradas)
* [PexAssert](static-helper-classes.md#pexassert) evalúa aserciones
* [PexChoose](static-helper-classes.md#pexchoose) genera opciones nuevas (entradas adicionales)
* [PexObserve](static-helper-classes.md#pexobserve) registra valores en vivo para las pruebas generadas

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
