---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c1cd4b15c3ce3462d6d49eca39fedbc64c744c7
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767307"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en modo seguro, cargando solo el entorno y los servicios predeterminados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador evita que se carguen todos los VSPackages de terceros cuando se inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], lo que garantiza una ejecución estable.  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, se inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en modo seguro.  
  
## <a name="code"></a>Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
