---
title: Filtros de soluciones en MSBuild
description: Explica los filtros de soluciones y muestra cómo compilar un archivo de filtro de soluciones con MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a5c764ad9ea4190df5e533926671dbd88c53b8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937841"
---
# <a name="solution-filters-in-msbuild"></a>Filtros de soluciones en MSBuild

Los archivos de filtro de soluciones son archivos JSON con la extensión *.slnf* que indican qué proyectos se compilarán o cargarán desde todos los proyectos de una solución. A partir de MSBuild 16.7, puede invocar MSBuild en el archivo de filtro de soluciones para compilar la solución con el filtrado habilitado. 

> [!NOTE]
> El archivo de filtro de soluciones reduce el conjunto de proyectos que se cargarán o compilarán y simplifica el formato. El archivo de solución sigue siendo necesario.

## <a name="build-a-solution-filter-from-the-command-line"></a>Compilar un filtro de soluciones desde la línea de comandos

Al compilar un archivo de filtro de soluciones desde la línea de comandos, se usa exactamente la misma sintaxis que compilando un archivo de solución. Especifique el archivo de filtro de soluciones en lugar de la solución que se va a compilar con el filtrado habilitado, como se indica a continuación:

```console
msbuild [options] solutionFilterFile.slnf
```

También puede anexar modificadores y propiedades adicionales como de costumbre. Consulte [Referencia de línea de comandos de MSBuild](msbuild-command-line-reference.md). Este comando compila los proyectos filtrados y los proyectos de los que dependen. Al compilar un filtro de soluciones desde la línea de comandos, MSBuild seguirá automáticamente las dependencias. Compila un proyecto si se especifica en el filtro o si un proyecto compilado hace referencia a este.

## <a name="solution-filter-files"></a>Archivos de filtro de soluciones

Puede usar Visual Studio para trabajar con archivos de filtro de soluciones. Al abrir un filtro de soluciones en Visual Studio, se muestran los proyectos descargados y cargados. Además, se ofrece la opción de cargar más proyectos con el fin de seleccionarlos para su compilación. También puede cargar todos los proyectos de los que dependen los proyectos iniciales para su compilación, pero no es necesario. Consulte [Soluciones filtradas](../ide/filtered-solutions.md).

El filtro de soluciones no tiene que estar en la misma carpeta que la solución. La ruta de acceso al archivo de solución es relativa a la ubicación del archivo de filtro de soluciones, pero las rutas de acceso a cada proyecto son relativas al propio archivo de solución y deben coincidir con las rutas de acceso del proyecto del archivo de solución. En el siguiente ejemplo se muestra el uso de rutas de acceso relativas:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Las barras diagonales inversas de las rutas de acceso deben duplicarse, ya que se convierten en caracteres de escape.

## <a name="example"></a>Ejemplo

Este es un ejemplo de una solución filtrada en Visual Studio:

![Captura de pantalla de la solución filtrada en Visual Studio](media/solution-with-filter.png)

En esta solución, tanto ProyectoA como ProyectoB usan ClassLibrary1, por lo que aparece como referencia de proyecto.

Este es el archivo de filtro de soluciones que genera Visual Studio:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

En este ejemplo, al compilar con el filtrado habilitado (mediante el comando `MSBuild [options] MyFilter.slnf`), MSBuild compila MiAplicación y ProyectoA porque se enumeran explícitamente en el archivo de filtro de soluciones. Como parte de la compilación de ProyectoA, MSBuild compila ClassLibrary1 porque ProyectoA depende de él.  ProyectoB no se compila (en esta discusión se da por hecho una compilación limpia. Si los proyectos se han compilado anteriormente, se aplicarán las reglas habituales para omitir los proyectos ya actualizados).

## <a name="see-also"></a>Consulte también

- [Soluciones filtradas](../ide/filtered-solutions.md)
- [Referencia de línea de comandos de MSBuild](msbuild-command-line-reference.md)
