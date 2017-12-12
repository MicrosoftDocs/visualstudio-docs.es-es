---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72630bd7c16c3830fecddc34a71b7ea1e4cf382c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando solo el entorno y los servicios predeterminados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador evita que se carguen todos los VSPackages de terceros cuando se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], lo que garantiza una ejecución estable.  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro.  
  
## <a name="code"></a>Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)