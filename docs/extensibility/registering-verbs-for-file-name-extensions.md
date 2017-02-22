---
title: "Registrar los verbos de extensiones de nombre de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verbos, registrar"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrar los verbos de extensiones de nombre de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La asociación de una extensión de nombre de archivo con una aplicación generalmente tiene una acción preferida que se produce cuando un usuario hace doble clic en un archivo. Esta preferencia acción está vinculada al verbo, por ejemplo abierto, que corresponde a la acción.  
  
 Puede registrar los verbos que están asociados a un identificador de programación \(ProgID\) para una extensión mediante la clave de Shell que se encuentra en HKEY\_CLASSES\_ROOT\\*progid*\\shell. Para obtener más información, consulte [tipos de archivo](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## Registrar los verbos estándar  
 El sistema operativo reconoce los siguientes verbos estándares:  
  
-   Abrir  
  
-   Editar  
  
-   Reproducir  
  
-   Imprimir  
  
-   Vista previa  
  
 Siempre que sea posible, registrar un verbo estándar. La opción más común es el verbo Open. Use el verbo de edición solo si hay una diferencia clara entre abrir el archivo y editar el archivo. Por ejemplo, si abre un archivo .htm lo muestra en el explorador, mientras que la edición de un archivo .htm inicia un editor HTML. Los verbos estándar están localizados con la configuración regional del sistema operativo.  
  
> [!NOTE]
>  Al registrar los verbos estándar, no establezca el valor predeterminado para abrir la clave. El valor predeterminado contiene la cadena de presentación en el menú. El sistema operativo proporciona esta cadena para los verbos estándar.  
  
 Archivos de proyecto se deben registrar para iniciar una nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario abre el archivo. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto.  
  
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
  
 Para abrir un archivo en una instancia existente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], registre una clave DDEEXEC. En el ejemplo siguiente se muestra un registro de verbo estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] archivo .cs.  
  
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
  
## Establecer el verbo predeterminado  
 El verbo predeterminado es la acción que se ejecuta cuando un usuario hace doble clic en un archivo en el Explorador de Windows. El verbo predeterminado es el verbo especificado como el valor predeterminado para el HKEY\_CLASSES\_ROOT\\*progid*\\Shell clave. Si no se especifica ningún valor, el verbo predeterminado es el primer verbo especificado en el HKEY\_CLASSES\_ROOT\\*progid*\\Shell lista de claves.  
  
> [!NOTE]
>  Si piensa cambiar el verbo predeterminado para una extensión en una implementación en paralelo, considere el impacto en la instalación y desinstalación. Durante la instalación, se sobrescribe el valor predeterminado original.  
  
## Vea también  
 [Creating a File Association](_win32_file_associations)   
 [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)