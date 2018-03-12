---
title: "Cómo: Compilar destinos específicos en soluciones mediante MSBuild.exe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4437c8030f66ae24d94a83d796c0d0edf7e59c79
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Cómo: Generar destinos específicos en soluciones mediante MSBuild.exe
Puede utilizar MSBuild.exe para compilar determinados destinos de proyectos específicos en una solución.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para compilar un destino concreto de un proyecto específico en una solución  
  
1.  En la línea de comandos, escriba `MSBuild.exe <SolutionName>.sln`, donde `<SolutionName>` corresponde al nombre de archivo de la solución que contiene el destino que quiere ejecutar.  
  
2. Especifique el destino después del modificador `/target:` en el formato **`ProjectName`**`:`**`TargetName`**. Si el nombre del proyecto contiene cualquiera de los caracteres `%`, `$`, `@`, `;`, `.`, `(`, `)` o `'`, reemplácelos con un `_` en el nombre de destino especificado.
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se ejecuta el destino `Rebuild` del proyecto `NotInSlnFolder` y, a continuación, se ejecuta el destino `Clean` del proyecto `InSolutionFolder`, que se encuentra en la carpeta de la solución `NewFolder`.  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>Solución de problemas

Si quiere examinar las opciones disponibles, puede usar la opción de depuración proporcionada por MSBuild para hacerlo. Establezca la variable de entorno `MSBUILDEMITSOLUTION=1` y compile la solución. Esto creará un archivo de MSBuild denominado `<SolutionName>.sln.metaproj` en el que se muestra la vista interna de MSBuild de la solución en tiempo de compilación. Puede inspeccionar esta vista para determinar los destinos que están disponibles para la compilación.

No realice la compilación con esta variable de entorno a menos que necesite esta vista interna. Esta configuración puede causar problemas al compilar los proyectos de la solución.

## <a name="see-also"></a>Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
