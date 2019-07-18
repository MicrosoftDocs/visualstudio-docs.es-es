---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e5bbbf3a1a9601a46aa9d3080f0d20583b43d22
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163308"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fuerza a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a combinar los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador no toma ningún argumento. El comando `devenv /setup` suele ser el último paso del proceso de instalación. El uso del modificador `/setup` no inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Debe ejecutar `devenv` como administrador para poder usar los modificadores [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) y [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el último paso de la instalación de una versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que incluye VSPackages.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Otras referencias  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
