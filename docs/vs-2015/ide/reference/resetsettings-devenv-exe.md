---
title: /ResetSettings (devenv.exe) | Microsoft Docs
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
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 276205ae2aab3c38ceb3d4f1419e0bac13ae626c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273499"
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
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)



