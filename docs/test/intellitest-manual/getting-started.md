---
title: "Crear códigos auxiliares de método de pruebas unitarias con el comando Crear pruebas unitarias | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 0194688e9eec258e415a30a8915379affc5f89de
ms.contentlocale: es-es
ms.lasthandoff: 06/02/2017

---
# <a name="get-started-with-microsoft-intellitest"></a>Introducción a Microsoft IntelliTest

* Si es la primera vez que usa IntelliTest:
  * vea el [vídeo de Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * lea esta [información general de MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * lea nuestra [documentación](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)
* Realice preguntas en [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest)
* Lea el resto de este manual de referencia
* Imprima esta página como referencia rápida

<a name="important-attributes"></a>
## <a name="important-attributes"></a>Atributos importantes

* [PexClass](attribute-glossary.md#pexclass) marca un tipo que contiene **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marca **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marca un parámetro que no es NULL 

```
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

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>Clases auxiliares estáticas importantes

* [PexAssume](static-helper-classes.md#pexassume) evalúa hipótesis (filtrado de entradas)
* [PexAssert](static-helper-classes.md#pexassert) evalúa aserciones
* [PexChoose](static-helper-classes.md#pexchoose) genera opciones nuevas (entradas adicionales)
* [PexObserve](static-helper-classes.md#pexobserve) registra valores en vivo para las pruebas generadas

```
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

Publique sus ideas y solicitudes de características en **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

