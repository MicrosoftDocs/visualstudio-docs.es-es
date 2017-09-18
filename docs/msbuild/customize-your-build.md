---
title: "Personalizar una compilación | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
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
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: es-es
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Personalizar una compilación
En versiones de MSBuild anteriores a la versión 15, si quería proporcionar una nueva propiedad personalizada a los proyectos de su solución tenía que agregar manualmente una referencia a esa propiedad en cada archivo de proyecto de la solución. O, tenía que definir la propiedad en un archivo .props y, después, importar explícitamente el archivo .props en cada proyecto de la solución, entre otras cosas.

En cambio, ahora puede agregar una propiedad nueva a cada proyecto en un paso definiéndola en un único archivo denominado Directory.Build.props en la raíz de su repositorio. Cuando se ejecuta MSBuild, Microsoft.Common.props busca su estructura de directorio para el archivo Directory.Build.props (y Microsoft.Common.targets busca Directory.Build.targets). Si encuentra uno, importa la propiedad. Directory.Build.props es un archivo definido por el usuario que proporciona personalizaciones a los proyectos de un directorio.

## <a name="directorybuildprops-example"></a>Ejemplo de Directory.Build.props
Por ejemplo, si quisiera permitir que todos sus proyectos tuvieran acceso a la nueva característica **/deterministic** de Roslyn (que se expone en el destino CoreCompile de Roslyn mediante la propiedad `$(Deterministic)`), podría realizar lo siguiente.

1. Crear un archivo en la raíz de su repositorio denominado Directory.Build.props.
2. Agregar el siguiente XML al archivo.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Ejecutar MSBuild. Las importaciones existentes del proyecto de Microsoft.Common.props y Microsoft.Common.targets encuentran el archivo y lo importan.

## <a name="search-scope"></a>Ámbito de búsqueda
Al buscar el archivo Directory.Build.props, MSBuild recorre la estructura del directorio hacia arriba desde la ubicación del proyecto ($(MSBuildProjectFullPath)), deteniéndose después de que encuentra un archivo Directory.Build.props. Por ejemplo, si su $(MSBuildProjectFullPath) fuera c:\users\username\code\test\case1, MSBuild empezaría a buscar allí y, después, buscaría en la estructura del directorio hacia arriba hasta que encontrara un archivo Directory.Build.props, como en la siguiente estructura de directorio.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
La ubicación del archivo de solución es irrelevante para Directory.Build.props.

## <a name="import-order"></a>Orden de importación

Directory.Build.props se importa muy pronto en Microsoft.Common.props, por lo que las propiedades definidas después no están disponibles en él. Por lo tanto, evite hacer referencia a propiedades que todavía no están definidas (y que, por tanto, se evaluarán como vacías).

Directory.Build.targets se importa desde Microsoft.Common.targets después de importar los archivos .targets de paquetes NuGet. Por lo tanto, puede usarse para invalidar propiedades y destinos que se definen en la mayoría de la lógica de compilación, pero a veces puede que sea necesario realizar personalizaciones dentro del archivo de proyecto después de la importación final.

## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   

