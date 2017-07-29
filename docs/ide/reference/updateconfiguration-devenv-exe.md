---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6e74ef38969cb62790629b34041ceef535ff6f9e
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
Notifica a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que combine los paquetes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecuta este comando automáticamente cuando instala un paquete de VSIX. Debe ejecutar `devenv.exe /updateconfiguration` después de revisar los archivos de manera que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] actualice la caché de MEF. Esto le permite evaluar si la corrección es adecuada.  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos hace que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] combine los paquetes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
