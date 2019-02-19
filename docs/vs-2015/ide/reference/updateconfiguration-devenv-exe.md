---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9e058d18c0a7c6d1d3b26a5b379c308d26f790ca
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783166"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Notifica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que combine los paquetes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ejecuta este comando automáticamente cuando instala un paquete de VSIX. Debe ejecutar `devenv.exe /updateconfiguration` después de revisar los archivos de manera que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] actualice la caché de MEF. Esto le permite evaluar si la corrección es adecuada.  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos hace que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] combine los paquetes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
