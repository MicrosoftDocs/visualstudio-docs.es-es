---
title: "Registrar controladores de comandos de ensamblado de interoperabilidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ensamblados de interoperabilidad, controladores de comandos"
  - "control con ensamblados de interoperabilidad, registro de comandos"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Registrar controladores de comandos de ensamblado de interoperabilidad
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debe registrar un paquete VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que el entorno de desarrollo integrado \(IDE\) enruta los comandos correctamente.  
  
 El registro se puede actualizar mediante la edición manual o mediante un archivo de registro \(.rgs\). Para obtener más información, consulta [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
 El marco de paquete administrados \(MPF\) proporciona esta funcionalidad a través de la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> clase.  
  
 [Command Table Format Reference](http://msdn.microsoft.com/es-es/09e9c6ef-9863-48de-9483-d45b7b7c798f) los recursos se encuentran en archivos DLL de la interfaz de usuario de satélite no administrada.  
  
## Registro del controlador de comando de un paquete VSPackage  
 Un VSPackage que actúa como un controlador de interfaz de usuario \(UI\)\-comandos según se requiere una entrada del registro con el mismo nombre que el paquete VSPackage `GUID`. Esta entrada del registro especifica la ubicación del archivo de recursos de interfaz de usuario de VSPackage y el recurso de menú dentro de ese archivo. La propia entrada del registro se encuentra en HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< versión \>*\\Menus, donde *\< versión \>* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 9.0.  
  
> [!NOTE]
>  La ruta de acceso raíz de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versión \>* puede ser invalidado con una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell se inicializa. Para obtener más información acerca de la ruta de acceso, consulte [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### La entrada del registro de recursos CTMENU  
 La estructura de la entrada del registro es:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> es el `GUID` habilitarla en el formulario {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}.  
  
 *\< información de recursos \>* consta de tres elementos separados por comas. Estos elementos son, en orden:  
  
 \<*Ruta de acceso al archivo DLL de recursos*\>, \<*Id. de recurso de menú*\>, \<*menú versión*\>  
  
 En la tabla siguiente se describe los campos de \<*información de recursos*\>.  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|\<*Ruta de acceso al archivo DLL de recursos*\>|Se trata de la ruta de acceso completa a la DLL de recursos que contiene el recurso de menú o se deja en blanco, que indica que recurso del VSPackage DLL que se usará \(según lo especificado en la subclave paquetes donde se registra el VSPackage propio\).<br /><br /> Es habitual dejar este campo en blanco.|  
|\<*Id. de recurso de menú*\>|Es el identificador de recurso de la `CTMENU` recursos que contiene todos los elementos de interfaz de usuario para el VSPackage como compilados a partir de un [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) archivo.|  
|\<*Menú versión*\>|Se trata de un número que se utiliza como una versión para el `CTMENU` recursos.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Este valor se utiliza para determinar si necesita volver a combinar el contenido de la `CTMENU` recursos con su caché de todos los `CTMENU` recursos. Un volver a combinar se desencadena al ejecutar el comando de instalación de devenv.<br /><br /> Este valor debe inicialmente establecido en 1 y se incrementa después de cada cambio en el `CTMENU` recursos y antes de que aparezca el volver a combinar.|  
  
### Ejemplo  
 Este es un ejemplo de un par de entradas de recursos:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)