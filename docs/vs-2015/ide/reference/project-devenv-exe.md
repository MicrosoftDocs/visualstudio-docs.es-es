---
title: -Project (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d048edd60d41c3f08a8bd0b731beddb3619a1887
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54776074"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Identifica un único proyecto dentro de la configuración de la solución especificada para compilar, limpiar, recompilar o implementar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## <a name="arguments"></a>Argumentos  
 /build  
 Compila el proyecto especificado por `/project` `ProjName`.  
  
 /clean  
 Limpia todos los archivos intermedios y directorios de salida creados durante una compilación.  
  
 /rebuild  
 Limpia y después compila el proyecto especificado por `/project` `ProjName`.  
  
 /deploy  
 Especifica que el proyecto se implementará después de una compilación o recompilación.  
  
 `SolnConfigName`  
 Obligatorio. El nombre de la configuración de solución que se aplicará a la solución mencionada en `SolutionName`.  
  
 `SolutionName`  
 Obligatorio. Ruta de acceso completa y nombre del archivo de solución.  
  
 /project `ProjName`  
 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.  
  
 /projectconfig `ProjConfigName`  
 Opcional. El nombre de una configuración de compilación de proyecto que se aplicará al `/project` mencionado.  
  
## <a name="remarks"></a>Comentarios  
  
-   Se debe usar como parte de un comando `devenv /build`, /`clean`, `/rebuild` o `/deploy`.  
  
-   Escriba las cadenas que incluyen espacios entre comillas dobles.  
  
-   Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo compila el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Debug` en la configuración de solución `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
