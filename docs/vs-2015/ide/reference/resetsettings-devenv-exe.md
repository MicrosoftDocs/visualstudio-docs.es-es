---
title: /ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b35026140b424da0f7fa71cb9e70b72c3dba243
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689659"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restaura la configuración predeterminada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e inicia automáticamente el IDE de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Opcionalmente, restablece la configuración de un archivo .vssettings especificado.  
  
 La configuración predeterminada se determina mediante el perfil que se ha seleccionado cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se ha iniciado por primera vez.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumentos  
 `SettingsFile`  
 La ruta de acceso completa y el nombre del archivo .vssettings que se va a aplicar a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Para restaurar el perfil de Configuración general de desarrollo, use `General`.  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún elemento `SettingsFile`, se le pedirá que seleccione una colección predeterminada de opciones la próxima vez que inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos se aplica a la configuración almacenada en el archivo `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
