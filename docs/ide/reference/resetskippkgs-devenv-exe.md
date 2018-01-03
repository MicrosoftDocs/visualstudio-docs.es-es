---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f84b4a8f73d378629edcf862f1aa53aa478fa1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Borra todas las opciones para omitir la carga agregada a VSPackages por usuarios que quieren evitar problemas al cargar VSPackages. Después, inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
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