---
title: -Build (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8eba6684167e4b60f02512e9b0fc1c7dc514a614
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Compila una solución mediante un archivo de configuración de solución especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Argumentos  
 `SolutionName`  
 Obligatorio. Ruta de acceso completa y nombre del archivo de solución.  
  
 `SolnConfigName`  
 Obligatorio. El nombre de la configuración de solución que se usará para compilar la solución mencionada en `SolutionName`.  
  
 /project `ProjName`  
 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.  
  
 /projectconfig `ProjConfigName`  
 Opcional. El nombre de una configuración de compilación de proyecto que se usará para crear el `/project` mencionado.  
  
## <a name="remarks"></a>Comentarios  
 Este modificador realiza la misma función que el comando de menú **Compilar solución** en el entorno de desarrollo integrado (IDE).  
  
 Escriba las cadenas que incluyen espacios entre comillas dobles.  
  
 Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
 Este comando solo compila proyectos que han cambiado desde la última compilación. Para compilar todos los proyectos en una solución, use [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo compila el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Debug` en la configuración de solución `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Vea también  
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)