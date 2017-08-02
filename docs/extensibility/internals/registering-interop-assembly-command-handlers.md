---
title: Registrar los controladores de comando de ensamblado de interoperabilidad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 774266bbcd64e87229f8f97626cdff1462b27fcb
ms.contentlocale: es-es
ms.lasthandoff: 04/05/2017

---
# <a name="registering-interop-assembly-command-handlers"></a>Registrar los controladores de comando de ensamblado de interoperabilidad
Debe registrar un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que el entorno de desarrollo integrado (IDE) enruta sus comandos correctamente.  
  
 El registro se puede actualizar mediante la edición manual o mediante el uso de un archivo de registro (.rgs). Para obtener más información, consulte [crear Scripts del registrador](/cpp/atl/creating-registrar-scripts).  
  
 Managed Package Framework (MPF) proporciona esta funcionalidad a través de la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>clase.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
 [Referencia de formato de tabla de comandos](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) recursos se encuentran en archivos DLL de interfaz de usuario de satélite no administrada.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Registro del controlador de comando de un paquete VSPackage  
 Un VSPackage que actúa como un controlador para la interfaz de usuario (UI)-basada en comandos requiere una entrada del registro con el mismo nombre que el VSPackage `GUID`. Esta entrada del registro especifica la ubicación del archivo de recursos de interfaz de usuario de VSPackage y el recurso de menú dentro de ese archivo. La entrada del registro en sí se encuentra en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<versión >*\Menus, donde  *\<versión >* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 9.0.  
  
> [!NOTE]
>  La ruta de acceso raíz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versión >* puede ser invalidado con una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell se inicializa. Para obtener más información acerca de la ruta de acceso raíz, consulte [instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>La entrada del registro de recursos CTMENU  
 La estructura de la entrada del registro es:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> es el `GUID` de VSPackage en el formato {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Información de recursos >* consta de tres elementos separados por comas. Estos elementos son, en orden:  
  
 \<*Ruta de acceso al archivo DLL de recursos*>, \< *Id. de recurso de menú*>, \< *versión de menú*>  
  
 En la tabla siguiente se describe los campos de \< *información del recurso*>.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|\<*Ruta de acceso al archivo DLL de recursos*>|Se trata de la ruta de acceso completa a la DLL de recursos que contiene el recurso de menú o se deja en blanco, que indica que los recursos de VSPackage DLL es que se usará (según lo especificado en la subclave de paquetes donde se registra el VSPackage propio).<br /><br /> Es habitual dejar este campo en blanco.|  
|\<*Id. de recurso de menú*>|Este es el identificador de recurso de la `CTMENU` recursos que contiene todos los elementos de interfaz de usuario para el VSPackage como compilada a partir de un [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) archivo.|  
|\<*Versión de menú*>|Se trata de un número que se utiliza como una versión para el `CTMENU` recursos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Este valor se utiliza para determinar si se debe volver a combinar el contenido de la `CTMENU` recursos con su caché de todos los `CTMENU` recursos. Un volver a combinar se desencadena al ejecutar el comando de instalación de devenv.<br /><br /> Este valor inicialmente se establece en 1 e incrementa después de cada cambio en el `CTMENU` recursos y antes de que ocurra el volver a combinar.|  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo de un par de entradas de recursos:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
