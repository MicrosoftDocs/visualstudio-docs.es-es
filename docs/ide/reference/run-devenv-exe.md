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
ms.openlocfilehash: 5be97e75ac7dc29a6dd0244293259bcd17591233
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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