---
title: "Cadenas de sustitución que se usan en. Pkgdef del y. Archivos de Pkgundef | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0405e18419baf8bc152331a2bcfc7254ec602d1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Cadenas de sustitución que se usan en. Pkgdef del y. Archivos de Pkgundef
Puede usar las cadenas de sustitución que se enumeran a continuación en el .pkgdef y archivos de .pkgundef definen para el Visual Studio aislado aplicación del shell.  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
  
|String|Descripción|  
|------------|-----------------|  
|$=*RegistryEntry*$|El valor de la *RegistryEntry* entrada. Si la cadena de entrada del registro finaliza con una barra diagonal inversa (\\), a continuación, se utiliza el valor predeterminado de la subclave del registro. Por ejemplo, la sustitución cadena $= HKEY_CURRENT_USER\Environment\TEMP$ se expande a la carpeta temporal del usuario actual.|  
|$AppName$|El nombre completo de la aplicación que se pasa a los puntos de entrada AppEnv.dll. El nombre completo está formada por el nombre de la aplicación, un carácter de subrayado y el identificador de clase (CLSID) del objeto de automatización de la aplicación, que también se registra como el valor de la configuración de ThisVersionDTECLSID en el archivo .pkgdef del proyecto.|  
|$AppDataLocalFolder|La subcarpeta bajo % LOCALAPPDATA % para esta aplicación.|  
|$BaseInstallDir$|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$CommonFiles$|El valor de la variable de entorno % CommonProgramFiles %.|  
|$MyDocuments$|La ruta de acceso completa de la carpeta Mis documentos del usuario actual.|  
|$PackageFolder$|La ruta de acceso completa del directorio que contiene los archivos de ensamblado de paquete para la aplicación.|  
|$ProgramFiles$|El valor de la variable de entorno % ProgramFiles %.|  
|$RootFolder$|La ruta de acceso completa del directorio raíz de la aplicación.|  
|$RootKey$|La clave del registro raíz para la aplicación. De forma predeterminada es la raíz de HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (cuando la aplicación se está ejecutando, _Config se anexa a esta clave). Se establece el valor de RegistryRoot de la *nombresolución*archivo .pkgdef.<br /><br /> La cadena de $ $RootKey puede utilizarse para recuperar un valor del registro bajo la subclave de la aplicación. Por ejemplo, la cadena "$= $RootKey$ \AppIcon$", devolverá el valor de la entrada AppIcon bajo la subclave de raíz de la aplicación.<br /><br /> El analizador procesa secuencialmente el archivo .pkgdef y puede tener acceso a una entrada del registro bajo la subclave de la aplicación solo si la entrada se ha definido anteriormente|  
|$ShellFolder$|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$System$|La carpeta Windows\system32.|  
|$WINDIR$|La carpeta de Windows.|  
  
 Si el analizador no reconoce la cadena de sustitución o que no puede determinar el valor de una entrada del registro o una variable de entorno, a continuación, que no realiza la sustitución en esa parte de la cadena.