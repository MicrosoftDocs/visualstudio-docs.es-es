---
title: Registrar los verbos para las extensiones de nombre de archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 692b94cc9bba5bf200d71f4356bef849ec2f3aae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138111"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrar los verbos para las extensiones de nombre de archivo
La asociación de una extensión de nombre de archivo con una aplicación normalmente tiene una acción preferida que se produce cuando un usuario hace doble clic en un archivo. Esta preferencia acción está vinculada a un verbo, por ejemplo abierto, de que se corresponde con la acción.  
  
 Puede registrar los verbos que están asociados a un identificador de programación (ProgID) de una extensión mediante la clave de Shell que se encuentran en HKEY_CLASSES_ROOT\\*progid*\shell. Para obtener más información, consulte [tipos de archivo](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registrar los verbos estándar  
 El sistema operativo reconoce los siguientes verbos estándares:  
  
-   Abrir  
  
-   Editar  
  
-   Reproducir  
  
-   Imprimir  
  
-   Vista previa  
  
 Siempre que sea posible, registrar un verbo estándar. La opción más común es el verbo Open. Utilice el verbo de edición solo si hay una diferencia clara entre abrir el archivo y editar el archivo. Por ejemplo, abrir un archivo .htm lo muestra en el explorador, mientras que la edición de un archivo .htm inicia un editor de HTML. Los verbos estándar están localizados con la configuración regional del sistema operativo.  
  
> [!NOTE]
>  Al registrar los verbos estándar, no establezca el valor predeterminado para abrir la clave. El valor predeterminado contiene la cadena de presentación en el menú. El sistema operativo proporciona esta cadena para los verbos estándar.  
  
 Archivos de proyecto deben registrarse para iniciar una nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario abre el archivo. En el ejemplo siguiente se muestra el registro de un verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Para abrir un archivo en una instancia existente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], registre una clave DDEEXEC. En el ejemplo siguiente se muestra el registro de un verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] archivo .cs.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Establecer el verbo predeterminado  
 El verbo predeterminado es la acción que se ejecuta cuando un usuario hace doble clic en un archivo en el Explorador de Windows. El verbo predeterminado es el verbo especificado como el valor predeterminado para el HKEY_CLASSES_ROOT\\*progid*\Shell clave. Si no se especifica ningún valor, el verbo predeterminado es el primer verbo especificado en HKEY_CLASSES_ROOT\\*progid*\Shell lista de claves.  
  
> [!NOTE]
>  Si piensa cambiar el verbo predeterminado para una extensión en una implementación en paralelo, tenga en cuenta el impacto sobre la instalación y eliminación. Durante la instalación se sobrescribe el valor predeterminado original.  
  
## <a name="see-also"></a>Vea también  
 [Administración de asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)