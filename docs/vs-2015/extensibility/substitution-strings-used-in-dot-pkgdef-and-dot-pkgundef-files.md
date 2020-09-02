---
title: Cadenas de sustitución usadas en. Pkgdef y. Archivos Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160533"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Cadenas de sustitución utilizadas en archivos .Pkgdef y .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar las cadenas de sustitución que se enumeran a continuación en los archivos. pkgdef y. pkgundef que defina para la aplicación de Shell aislado de Visual Studio.  
  
## <a name="substitution-strings"></a>Cadenas de sustitución  
  
|String|Descripción|  
|------------|-----------------|  
|$=*RegistryEntry*$|Valor de la entrada *RegistryEntry* . Si la cadena de entrada del registro finaliza en una barra diagonal inversa ( \\ ), se usa el valor predeterminado de la subclave del registro. Por ejemplo, la cadena de sustitución $ = HKEY_CURRENT_USER \Environment\TEMP $ se expande a la carpeta temporal del usuario actual.|  
|$AppName $|Nombre completo de la aplicación que se pasa a los puntos de entrada AppEnv.dll. El nombre completo consta del nombre de la aplicación, un carácter de subrayado y el identificador de clase (CLSID) del objeto de automatización de la aplicación, que también se registra como el valor de la configuración ThisVersionDTECLSID en el archivo Project. pkgdef.|  
|$AppDataLocalFolder|La subcarpeta de% LOCALAPPDATA% para esta aplicación.|  
|$BaseInstallDir $|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$CommonFiles $|El valor de la variable de entorno% CommonProgramFiles%.|  
|$MyDocuments $|La ruta de acceso completa de la carpeta Mis documentos del usuario actual.|  
|$PackageFolder $|La ruta de acceso completa del directorio que contiene los archivos de ensamblado del paquete para la aplicación.|  
|$ProgramFiles $|El valor de la variable de entorno% ProgramFiles%.|  
|$RootFolder $|Ruta de acceso completa del directorio raíz de la aplicación.|  
|$RootKey $|Clave del Registro raíz de la aplicación. De forma predeterminada, la raíz se encuentra en HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *projectname* \\ *versionNumber* (cuando la aplicación se está ejecutando, _Config se anexa a esta clave). Se establece mediante el valor RegistryRoot en el archivo *solutionname*. pkgdef.<br /><br /> Se puede usar el $RootKey $ String para recuperar un valor del registro en la subclave de la aplicación. Por ejemplo, la cadena "$ = $RootKey $ \AppIcon $" devolverá el valor de la entrada appicor en la subclave raíz de la aplicación.<br /><br /> El analizador procesa el archivo. pkgdef secuencialmente y puede tener acceso a una entrada del registro en la subclave de la aplicación solo si la entrada se ha definido previamente.|  
|$ShellFolder $|La ruta de acceso completa de la ubicación donde se instaló Visual Studio.|  
|$System $|La carpeta Windows\System32.|  
|$WINDIR $|La carpeta Windows.|  
  
 Si el analizador no reconoce la cadena de sustitución o no puede determinar el valor de una entrada del registro o una variable de entorno, no realiza la sustitución en esa parte de la cadena.
