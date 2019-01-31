---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 59bde318995ed8b66637a2220ae1817db2a1e800
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834683"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Borra todas las opciones para omitir la carga agregada a VSPackages por usuarios que quieren evitar problemas al cargar VSPackages. Después, inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Comentarios  
 La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage; al borrar la etiqueta, se rehabilita la carga de VSPackage.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se borran todas las etiquetas SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
