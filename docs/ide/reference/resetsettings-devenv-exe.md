---
title: /ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22dd925755e996a927664e0a9a5846fc10247882
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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