---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56ff98aa40e122b5067bd17d72334daf93164fe2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262657"
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
 Requerido. La ruta de acceso y el nombre de un archivo .exe.  
  
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



