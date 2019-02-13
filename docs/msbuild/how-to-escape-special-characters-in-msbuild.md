---
title: Filtrar Usar caracteres de escape especiales en MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752f4c6535f498b074d2c85b4b7cb6e9870ea862
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853945"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Filtrar Usar caracteres de escape especiales en MSBuild

Ciertos caracteres tienen un significado especial en archivos del proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Algunos ejemplos de estos caracteres son los signos de punto y coma (`;`) y los asteriscos (`*`). Para obtener una lista completa de estos caracteres especiales, vea [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).

Para utilizar estos caracteres especiales con su significado literal en un archivo de proyecto, es preciso especificarlos con la sintaxis `%<xx>`, donde `<xx>` representa el valor hexadecimal ASCII del carácter.

## <a name="msbuild-special-characters"></a>Caracteres especiales de MSBuild

Un ejemplo de dónde se utilizan los caracteres especiales se encuentra en el atributo `Include` de las listas de elementos. Por ejemplo, la siguiente lista de elementos declara dos elementos: *MyFile.cs* y *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Si quiere declarar un elemento que contiene un punto y coma en el nombre, debe usar la sintaxis `%<xx>` para aplicar una secuencia de escape al punto y coma, y evitar que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] declare dos elementos independientes. Por ejemplo, el elemento siguiente escapa el punto y coma y declara un elemento denominado `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

También puede usar una [función de propiedad](../msbuild/property-functions.md) para escapar las cadenas. Por ejemplo, esto es equivalente al ejemplo anterior.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para utilizar un carácter especial de MSBuild como carácter literal

Utilice la notación `%<xx>` en lugar del carácter especial, donde `<xx>` representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (`*`) como un carácter literal, utilice el valor `%2A`.

## <a name="see-also"></a>Vea también
[Conceptos de MSBuild](../msbuild/msbuild-concepts.md)  
[MSBuild](../msbuild/msbuild.md)  
[Elementos](../msbuild/msbuild-items.md)
