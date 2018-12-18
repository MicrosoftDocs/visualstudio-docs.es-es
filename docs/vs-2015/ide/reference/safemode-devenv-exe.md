---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b785a3e43726522f6e6cc6ce99dec4bf3815c81d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230085"
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



