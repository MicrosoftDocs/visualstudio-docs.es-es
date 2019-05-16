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
ms.openlocfilehash: 2f20463cd91148143a1d3fb7f7de5cc1649d683c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689336"
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
 [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
