---
title: 'Cómo: Compilar destinos específicos en soluciones mediante MSBuild.exe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d07c0e11d47e20f43f4d4173de4bcc3c24b864b1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652735"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Cómo: Generar destinos específicos en soluciones mediante MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar MSBuild.exe para compilar determinados destinos de proyectos específicos en una solución.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para compilar un destino concreto de un proyecto específico en una solución  
  
1.  En la línea de comandos, escriba `MSBuild.exe <SolutionName>.sln`, donde `<SolutionName>` corresponde al nombre de archivo de la solución que contiene el destino que quiere ejecutar.  
  
2.  Especifique el destino después del modificador **/t** en el formato *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se ejecuta el destino `Rebuild` del proyecto `NotInSlnFolder` y, a continuación, se ejecuta el destino `Clean` del proyecto `InSolutionFolder`, que se encuentra en la carpeta de la solución `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
