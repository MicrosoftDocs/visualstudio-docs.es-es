---
title: Personalizar una compilación | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dae51959313a7108c54466dff08b3641525818cd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="customize-your-build"></a>Personalizar una compilación
En versiones de MSBuild anteriores a la versión 15, si quería proporcionar una nueva propiedad personalizada a los proyectos de su solución tenía que agregar manualmente una referencia a esa propiedad en cada archivo de proyecto de la solución. O, tenía que definir la propiedad en un archivo *.props* y, después, importar explícitamente el archivo *.props* en cada proyecto de la solución, entre otras cosas.

En cambio, ahora puede agregar una propiedad nueva a cada proyecto en un paso definiéndola en un único archivo denominado *Directory.Build.props* en la raíz de su repositorio. Cuando se ejecuta MSBuild, *Microsoft.Common.props* busca su estructura de directorio para el archivo *Directory.Build.props* (y *Microsoft.Common.targets* busca *Directory.Build.targets*). Si encuentra uno, importa la propiedad. *Directory.Build.props* es un archivo definido por el usuario que proporciona personalizaciones a los proyectos de un directorio.

## <a name="directorybuildprops-example"></a>Ejemplo de Directory.Build.props
Por ejemplo, si quisiera permitir que todos sus proyectos tuvieran acceso a la nueva característica **/deterministic** de Roslyn (que se expone en el destino `CoreCompile` de Roslyn mediante la propiedad `$(Deterministic)`), podría realizar lo siguiente.

1. Crear un archivo en la raíz de su repositorio denominado *Directory.Build.props*.
2. Agregar el siguiente XML al archivo.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Ejecutar MSBuild. Las importaciones existentes del proyecto de *Microsoft.Common.props* y *Microsoft.Common.targets* encuentran el archivo y lo importan.

## <a name="search-scope"></a>Ámbito de búsqueda
Al buscar el archivo *Directory.Build.props*, MSBuild recorre la estructura del directorio hacia arriba desde la ubicación del proyecto (`$(MSBuildProjectFullPath)`), deteniéndose después de que encuentra un archivo *Directory.Build.props*. Por ejemplo, si su `$(MSBuildProjectFullPath)` fuera *c:\users\username\code\test\case1*, MSBuild empezaría a buscar allí y, después, buscaría en la estructura del directorio hacia arriba hasta que encontrara un archivo *Directory.Build.props*, como en la siguiente estructura de directorio.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
La ubicación del archivo de solución es irrelevante para *Directory.Build.props*.

## <a name="import-order"></a>Orden de importación

*Directory.Build.props* se importa muy pronto en *Microsoft.Common.props*, por lo que las propiedades definidas después no están disponibles en él. Por lo tanto, evite hacer referencia a propiedades que todavía no están definidas (y que, por tanto, se evaluarán como vacías).

*Directory.Build.targets* se importa desde *Microsoft.Common.targets* después de importar los archivos *.targets* de paquetes NuGet. Por lo tanto, puede usarse para invalidar propiedades y destinos que se definen en la mayoría de la lógica de compilación, pero a veces puede que sea necesario realizar personalizaciones dentro del archivo de proyecto después de la importación final.

## <a name="use-case-multi-level-merging"></a>Caso de uso: combinación de varios niveles

Imagínese que tiene esta estructura de solución estándar:

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

Puede que convenga tener propiedades comunes para todos los proyectos *(1)*, propiedades comunes para los proyectos *src* *(2-src)* y propiedades comunes para los proyectos *test* *(2-test)*.

Para que msbuild combine correctamente los archivos "internos" (*2-src* y *2-test*) con el archivo "externo" (*1*), debe tener en cuenta que, cuando msbuild encuentra un archivo *Directory.Build.props*, detiene el análisis. Para continuar con el análisis y efectuar la combinación en el archivo externo, coloque esto en ambos archivos internos:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

A continuación tiene un resumen del enfoque general de MSBuild:

- Para un proyecto dado, MSBuild busca el primer *Directory.Build.props* hacia arriba en la estructura de la solución, lo combina con valores predeterminados y detiene el análisis.
- Si quiere que se busquen y combinen varios niveles, efectúe una [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (que se muestra arriba) del archivo "externo" desde el archivo "interno".
- Si el archivo "externo" no importa algo por encima de él, el análisis se detendrá en ese punto.
- Para controlar el proceso de análisis/combinación, use `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`.

O más sencillo: el primer *Directory.Build.props* que no importa nada es donde se detiene MSBuild.

## <a name="see-also"></a>Vea también  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
