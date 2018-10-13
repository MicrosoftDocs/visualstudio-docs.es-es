---
title: Cadenas de sustitución utilizadas en. Pkgdef y. Archivos Pkgundef | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f679f5c4f817002fa92475a1fba7dc38caa34984
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175297"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Cadenas de sustitución utilizadas en. Pkgdef y. Archivos Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar las cadenas de sustitución que se enumeran a continuación en el .pkgdef y .pkgundef los archivos que defina para Visual Studio aislado aplicación del shell.  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
  
|String|Descripción|  
|------------|-----------------|  
|$=*RegistryEntry*$|El valor de la *RegistryEntry* entrada. Si la cadena de entrada del registro termina en una barra diagonal inversa (\\), a continuación, se usa el valor predeterminado de la subclave del registro. Por ejemplo, la sustitución de cadenas $= HKEY_CURRENT_USER\Environment\TEMP$ se expande a la carpeta temporal del usuario actual.|  
|$AppName$|El nombre completo de la aplicación que se pasa a los puntos de entrada AppEnv.dll. El nombre completo consta del nombre de la aplicación, un carácter de subrayado y el identificador de clase (CLSID) del objeto de automatización de la aplicación, que también se registra como el valor de la configuración de ThisVersionDTECLSID en el archivo .pkgdef del proyecto.|  
|$AppDataLocalFolder|La subcarpeta ubicada en % LOCALAPPDATA % para esta aplicación.|  
|$BaseInstallDir$|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$CommonFiles$|El valor de la variable de entorno % CommonProgramFiles %.|  
|$MyDocuments$|La ruta de acceso completa de la carpeta Mis documentos del usuario actual.|  
|$PackageFolder$|La ruta de acceso completa del directorio que contiene los archivos de ensamblado del paquete para la aplicación.|  
|$ProgramFiles$|El valor de la variable de entorno % ProgramFiles %.|  
|$RootFolder$|La ruta de acceso completa del directorio raíz de la aplicación.|  
|$RootKey$|La clave del registro raíz para la aplicación. De forma predeterminada, la raíz es en HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (cuando la aplicación se está ejecutando, _Config se anexa a esta clave). Se establece el valor RegistryRoot en el *SolutionName*archivo .pkgdef.<br /><br /> La cadena de $ $RootKey puede usarse para recuperar un valor del registro bajo la subclave de la aplicación. Por ejemplo, la cadena "$= $RootKey$ \AppIcon$", devolverá el valor de la entrada AppIcon bajo la subclave de raíz de la aplicación.<br /><br /> El analizador procesa secuencialmente el archivo .pkgdef y puede tener acceso a una entrada del registro bajo la subclave de la aplicación solo si la entrada se ha definido anteriormente|  
|$ShellFolder$|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$System$|La carpeta Windows\system32.|  
|$WINDIR$|La carpeta Windows.|  
  
 Si el analizador no reconoce la cadena de sustitución o no puede determinar el valor de una entrada del registro o una variable de entorno, a continuación, que no realiza la sustitución en esa parte de la cadena.

