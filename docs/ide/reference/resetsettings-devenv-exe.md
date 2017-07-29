---
title: /ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 08d285b07d775f3e46bb2f5106ff8140d3058f8f
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Restaura la configuración predeterminada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e inicia automáticamente el IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Opcionalmente, restablece la configuración de un archivo .vssettings especificado.  
  
 La configuración predeterminada se determina mediante el perfil que se ha seleccionado cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se ha iniciado por primera vez.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumentos  
 `SettingsFile`  
 La ruta de acceso completa y el nombre del archivo .vssettings que se va a aplicar a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para restaurar el perfil de Configuración general de desarrollo, use `General`.  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún elemento `SettingsFile`, se le pedirá que seleccione una colección predeterminada de opciones la próxima vez que inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos se aplica a la configuración almacenada en el archivo `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
