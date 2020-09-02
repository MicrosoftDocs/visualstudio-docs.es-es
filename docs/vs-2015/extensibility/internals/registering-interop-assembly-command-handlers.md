---
title: Registrando controladores de comandos de ensamblado de interoperabilidad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d2822e9eef36806f5c251813925fb4244242519
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705811"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registro de controladores de comandos de ensamblado de interoperabilidad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage debe registrarse con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que el entorno de desarrollo integrado (IDE) enrute sus comandos correctamente.  
  
 El registro se puede actualizar mediante la edición manual o mediante un archivo de registrador (. RGS). Para obtener más información, consulta [Creating Registrar Scripts](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 El marco de trabajo de paquetes administrados (MPF) proporciona esta funcionalidad a través de la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> clase.  
  
 Los recursos de [referencia de formato de tabla de comandos](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) se encuentran en archivos dll satélite no administrados.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Registro del controlador de comandos de un VSPackage  
 Un VSPackage que actúa como controlador para comandos basados en la interfaz de usuario (UI) requiere una entrada del registro denominada después del VSPackage `GUID` . Esta entrada del registro especifica la ubicación del archivo de recursos de la interfaz de usuario del VSPackage y el recurso de menú dentro de dicho archivo. La propia entrada del registro se encuentra en HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \Menus, donde *\<Version>* es la versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , por ejemplo 9,0.  
  
> [!NOTE]
> La ruta de acceso raíz de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* se puede invalidar con una raíz alternativa cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se inicializa el shell. Para obtener más información acerca de la ruta de acceso raíz, consulte [Installing VSPackages With Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>La entrada del registro de recursos CTMENU  
 La estructura de la entrada del registro es:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> es el `GUID` del VSPackage con el formato {xxxxxx-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Resource Information>* consta de tres elementos separados por comas. Estos elementos son, en orden:  
  
 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>  
  
 En la tabla siguiente se describen los campos de \<*Resource Information*> .  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|\<*Path to Resource DLL*>|Esta es la ruta de acceso completa a la DLL de recursos que contiene el recurso de menú o se deja en blanco, lo que indica que se va a usar el archivo DLL de recursos del VSPackage (tal y como se especifica en la subclave Packages donde se registra el VSPackage).<br /><br /> Es más personalizado dejar este campo en blanco.|  
|\<*Menu Resource ID*>|Este es el identificador de recurso del `CTMENU` recurso que contiene todos los elementos de la interfaz de usuario para el VSPackage compilados a partir de un archivo [. Vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) .|  
|\<*Menu Version*>|Se trata de un número que se usa como versión para el `CTMENU` recurso. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utiliza este valor para determinar si es necesario recombinar el contenido del `CTMENU` recurso con su memoria caché de todos los `CTMENU` recursos. Para desencadenar una recombinación, se ejecuta el comando de configuración de devenv.<br /><br /> Este valor debe establecerse inicialmente en 1 e incrementarse después de cada cambio en el `CTMENU` recurso y antes de que se produzca la recombinación.|  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo de un par de entradas de recursos:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Consulte también  
 [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos y menús que usan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
