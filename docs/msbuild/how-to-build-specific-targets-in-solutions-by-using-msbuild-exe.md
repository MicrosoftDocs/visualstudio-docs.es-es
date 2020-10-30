---
title: Uso de MSBuild.exe para compilar destinos específicos en soluciones
description: Obtenga información sobre cómo usar la línea de comandos de MSBuild.exe para compilar destinos específicos de proyectos específicos en soluciones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8d774ace7744c90d0cf092faa2786110ed7309
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436434"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Cómo: Compilar destinos específicos en soluciones mediante MSBuild.exe

Puede usar *MSBuild.exe* para compilar destinos concretos de proyectos específicos en una solución.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para compilar un destino concreto de un proyecto específico en una solución

1. En la línea de comandos, escriba `MSBuild.exe <SolutionName>.sln`, donde `<SolutionName>` corresponde al nombre de archivo de la solución que contiene el destino que quiere ejecutar.

2. Especifique el destino después del modificador `-target:` en el formato \<ProjectName>:\<TargetName>. Si el nombre del proyecto contiene cualquiera de los caracteres `%`, `$`, `@`, `;`, `.`, `(`, `)` o `'`, reemplácelos con un `_` en el nombre de destino especificado.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se ejecuta el destino `Rebuild` del proyecto `NotInSlnFolder` y luego se ejecuta el destino `Clean` del proyecto `InSolutionFolder`, que se encuentra en la carpeta de la solución *NewFolder* .

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Solución de problemas

Si quiere examinar las opciones disponibles, puede usar la opción de depuración proporcionada por MSBuild para hacerlo. Establezca la variable de entorno `MSBUILDEMITSOLUTION=1` y compile la solución. Esto generará un archivo de MSBuild denominado *\<SolutionName>.sln.metaproj* que muestra la vista interna de MSBuild de la solución en tiempo de compilación. Puede inspeccionar esta vista para determinar los destinos que están disponibles para la compilación.

No realice la compilación con esta variable de entorno a menos que necesite esta vista interna. Esta configuración puede causar problemas al compilar los proyectos de la solución.

## <a name="see-also"></a>Vea también

- [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
