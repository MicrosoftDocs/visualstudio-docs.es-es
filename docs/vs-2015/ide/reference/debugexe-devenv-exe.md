---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1edbcddd27f2c3637e0e56dd9b4841e17ace16af
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767568"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Abre el archivo ejecutable especificado que se va a depurar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argumentos  
 `ExecutableFile`  
 Obligatorio. La ruta de acceso y el nombre de un archivo .exe.  
  
 Si el archivo .exe no se encuentra o no existe, no se muestra ningún error ni advertencia y [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se inicia normalmente.  
  
## <a name="remarks"></a>Comentarios  
 Las cadenas que siguen al parámetro `ExecutableFile` pasan a dicho archivo como argumentos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se abre el archivo `MyApplication.exe` para depurar.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
