---
title: "Cadenas de sustitución que se usan en. Pkgdef y. Archivos Pkgundef | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Cadenas de sustitución que se usan en. Pkgdef y. Archivos de Pkgundef
Puede utilizar las cadenas de sustitución que se enumeran a continuación en el .pkgdef y archivos .pkgundef definir para Visual Studio aislada aplicación del shell.  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
  
|Cadena|Descripción|  
|------------|-----------------|  
|$=*RegistryEntry*$|El valor de la *RegistryEntry* entrada. Si la cadena de entrada del registro termina en una barra diagonal inversa (\\), se utiliza el valor predeterminado de la subclave del registro. Por ejemplo, la sustitución cadena $= HKEY_CURRENT_USER\Environment\TEMP$ se expande a la carpeta temporal del usuario actual.|  
|$AppName$|El nombre completo de la aplicación que se pasa a los puntos de entrada AppEnv.dll. El nombre calificado se compone del nombre de la aplicación, un carácter de subrayado y el identificador de clase (CLSID) del objeto de automatización de la aplicación, que también se registra como el valor de la configuración de ThisVersionDTECLSID en el archivo .pkgdef del proyecto.|  
|$AppDataLocalFolder|La subcarpeta % LOCALAPPDATA % para esta aplicación.|  
|$BaseInstallDir$|Ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$CommonFiles$|El valor de la variable de entorno % CommonProgramFiles %.|  
|$MyDocuments$|Ruta de acceso completa de la carpeta Mis documentos del usuario actual.|  
|$PackageFolder$|Ruta de acceso completa del directorio que contiene los archivos de ensamblado de paquete para la aplicación.|  
|$ProgramFiles$|El valor de la variable de entorno % ProgramFiles %.|  
|$RootFolder$|Ruta de acceso completa del directorio raíz de la aplicación.|  
|$RootKey$|La clave del registro raíz para la aplicación. De forma predeterminada, la raíz es en HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (cuando se ejecuta la aplicación, _Config se anexa a esta clave). Se establece el valor de RegistryRoot en el *SolutionName*archivo .pkgdef.<br /><br /> La cadena de $RootKey$ puede utilizarse para recuperar un valor del registro bajo la subclave de la aplicación. Por ejemplo, la cadena "$= $RootKey$ \AppIcon" devolverá el valor de la entrada AppIcon bajo la subclave de raíz de la aplicación.<br /><br /> El analizador procesa el archivo .pkgdef secuencialmente y puede tener acceso a una entrada del registro bajo la subclave de la aplicación sólo si la entrada se ha definido previamente|  
|$ShellFolder$|Ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$System$|La carpeta Windows\system32.|  
|$WINDIR$|La carpeta de Windows.|  
  
 Si el analizador no reconoce la cadena de sustitución o no puede determinar el valor de una entrada del registro o una variable de entorno, a continuación, no funciona en esa parte de la cadena de sustitución.
