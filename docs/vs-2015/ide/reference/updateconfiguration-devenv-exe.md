---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed69bf8c54d3b428907b4dbe0636f2966254de75
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253641"
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
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)



