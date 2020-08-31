---
title: Condiciones de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5994e3f5b17f50d707c4c5a00666d60c2efd3184
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711708"
---
# <a name="msbuild-conditions"></a>Condiciones de MSBuild

MSBuild admite un conjunto específico de condiciones que se pueden aplicar allá donde se permita un atributo `Condition`. En la siguiente tabla se explican esas condiciones.

|Condición|Descripción|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Se evalúa como `true` si `stringA` es igual a `stringB`.<br /><br /> Por ejemplo:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos. Esta comprobación no distingue mayúsculas de minúsculas.|
|'`stringA`' != '`stringB`'|Se evalúa como `true` si `stringA` no es igual a `stringB`.<br /><br /> Por ejemplo:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos. Esta comprobación no distingue mayúsculas de minúsculas.|
|\<, >, \<=, >=|Evalúa los valores numéricos de los operandos. Devuelve `true` si la evaluación relacional es verdadera. Los operandos deben evaluarse como un número decimal o hexadecimal. Los números hexadecimales deben comenzar con "0x". **Nota:**  En XML, los caracteres `<` y `>` deben ser de escape. El símbolo `<` se representa como `&lt;`. El símbolo `>` se representa como `&gt;`.|
|Existe ('`stringA`')|Se evalúa como `true` si existe un archivo o una carpeta con el nombre `stringA`.<br /><br /> Por ejemplo:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|
|HasTrailingSlash ('`stringA`')|Se evalúa como `true` si la cadena especificada contiene al final un carácter de barra inversa (\\) o barra diagonal (/).<br /><br /> Por ejemplo:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|
|!|Se evalúa como `true` si el operando se evalúa como `false`.|
|`And`|Se evalúa como `true` si ambos operandos se evalúan como `true`.|
|`Or`|Se evalúa como `true` si al menos uno de los operandos se evalúa como `true`.|
|()|Mecanismo de agrupamiento que se evalúa como `true` si las expresiones que contiene se evalúan como `true`.|
|$if$ ( %expression% ), $else$, $endif$|Comprueba si el `%expression%` especificado coincide con el valor de cadena del parámetro de plantilla personalizado pasado. Si la condición `$if$` se evalúa como `true`, sus instrucciones se ejecutan; en caso contrario, se comprueba la condición `$else$`. Si la condición `$else$` es `true`, sus instrucciones se ejecutan; en caso contrario, la condición `$endif$` finaliza la evaluación de expresiones.<br /><br /> Para obtener ejemplos de uso, vea [Visual Studio project/item template parameter logic](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic) (Lógica del parámetro de plantillas de proyecto o elemento de Visual Studio).|

En las condiciones se pueden usar métodos de cadena, como se muestra en el ejemplo siguiente, donde la función [TrimEnd()](/dotnet/api/system.string.trimend) se usa para comparar solo la parte pertinente de la cadena, con el fin de diferenciar entre las plataformas de destino .NET Framework y .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

En los archivos del proyecto MSBuild, no hay ningún tipo booleano true. Los datos booleanos se representan en propiedades que podrían estar vacías o establecerse en cualquier valor. Por lo tanto, `'$(Prop)' == 'true'` significa "si Prop es `true`", pero `'$(Prop)' != 'false'` significa "si Prop es `true` o anular o establecer en otra cosa".

La lógica booleana solo se evalúa en el contexto de las condiciones, por lo que los valores de propiedad como `<Prop2>'$(Prop1)' == 'true'</Prop>` se representan como una cadena (después de la expansión de variables), no se evalúan como valores booleanos.  

MSBuild implementa algunas reglas de procesamiento especiales para facilitar el trabajo con propiedades de cadena que se usan como valores booleanos. Los literales booleanos se aceptan, por lo que `Condition="true"` y `Condition="false"` funcionan según lo previsto. MSBuild también incluye reglas especiales para admitir el operador booleano de negación. Por lo tanto, si `$(Prop)` es "true", `!$(Prop)` se expande a `!true` y se compara igual que `false`, como cabría esperar.

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md)
- [Tutorial: Crear un archivo de proyecto de MSBuild desde cero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
