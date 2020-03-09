---
title: Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21e3b6554a9d6e0024cc21fd898962177acfffa7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633634"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Elemento ItemDefinitionGroup (MSBuild)

El elemento `ItemDefinitionGroup` permite definir un conjunto de definiciones de elementos, que son valores de metadatos que, de forma predeterminada, se aplican a todos los elementos del proyecto. Con ItemDefinitionGroup, ya no es necesario usar [CreateItem (Tarea)](../msbuild/createitem-task.md) ni [CreateProperty (Tarea)](../msbuild/createproperty-task.md). Para obtener más información, vea [Definiciones de elementos](../msbuild/item-definitions.md).

\<Project> \<ItemDefinitionGroup>

## <a name="syntax"></a>Sintaxis

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Condition`|Atributo opcional. Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación. Puede haber cero o más elementos `Item` en un `ItemDefinitionGroup`.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se definen dos elementos de metadatos, m y n, en ItemDefinitionGroup. En este ejemplo, los metadatos predeterminados "m" se aplican al elemento "i" porque los metadatos "m" no están definidos explícitamente por el elemento "i". Sin embargo, los metadatos predeterminados "n" no se aplican al elemento "i" porque los metadatos "n" ya están definidos por el elemento "i".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementos](../msbuild/msbuild-items.md)
