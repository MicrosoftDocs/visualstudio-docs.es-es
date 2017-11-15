---
title: -Setup (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e63b69c9d97edf5049dfb6e55b8f9d5010984d4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
Fuerza a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a combinar los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador no toma ningún argumento. El comando `devenv /setup` suele ser el último paso del proceso de instalación. El uso del modificador `/setup` no inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Debe ejecutar `devenv` como administrador para poder usar los modificadores [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) y [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el último paso de la instalación de una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que incluye VSPackages.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)