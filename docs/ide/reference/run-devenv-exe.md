---
title: -Run (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 97e4339546eda741ba961b0015f9f62edf231d24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Compila y ejecuta el proyecto o la solución especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumentos  
 `SolutionName`  
 Obligatorio. Ruta de acceso completa y nombre de un archivo de solución.  
  
 `ProjectName`  
 Obligatorio. Ruta de acceso completa y nombre de un archivo de proyecto.  
  
## <a name="remarks"></a>Comentarios  
 Compila y ejecuta el proyecto o solución especificados según los ajustes indicados para la configuración de soluciones activas. Este modificador inicia el entorno de desarrollo integrado (IDE) y lo deja activo después de que el proyecto o la solución hayan acabado de ejecutarse.  
  
-   Escriba las cadenas que incluyen espacios entre comillas dobles.  
  
-   Se puede mostrar información de resumen, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se ejecuta la solución `MySolution` con la configuración de implementación activa.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)