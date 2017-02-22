---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/ResetSettings (modificador para Devenv)"
  - "Devenv, /ResetSettings (modificador)"
  - "ResetSettings (modificador)"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restaura la configuración predeterminada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e inicia automáticamente el IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Opcionalmente, restablece la configuración del archivo .vssettings especificado.  
  
 Las configuraciones predeterminadas vienen determinadas por el perfil seleccionado cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inició por primera vez.  
  
## Sintaxis  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## Argumentos  
 `SettingsFile`  
 Ruta de acceso completa y nombre del archivo .vssettings que se aplicará a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para restaurar el perfil Configuración general de desarrollo, utilice `General`.  
  
## Comentarios  
 Si no se especifica `SettingsFile`, se le pedirá que seleccione una colección predeterminada de valores la próxima vez que inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Ejemplo  
 La línea de comandos siguiente aplica la configuración almacenada en el archivo `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## Vea también  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)