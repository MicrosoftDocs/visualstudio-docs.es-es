---
title: Registrar controladores de comandos de ensamblado de interoperabilidad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5373e292192294b5dd27eff87c9f9f2b2f97820a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602798"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registro de controladores de comandos de ensamblado de interoperabilidad
Debe registrar un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que el entorno de desarrollo integrado (IDE) enruta sus comandos correctamente.

 El registro se puede actualizar mediante la edición manual o mediante un archivo de registrador (.rgs). Para obtener más información, consulta [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed Package Framework (MPF) proporciona esta funcionalidad a través de la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> clase.

- [Referencia de formato de tabla del comando](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) los recursos se encuentran en archivos DLL de interfaz de usuario de satélite no administrado.

## <a name="command-handler-registration-of-a-vspackage"></a>Registro del controlador de comando de un paquete VSPackage
 Un VSPackage que actúa como un controlador para la interfaz de usuario (UI)-en función de comandos requiere una entrada del registro con el nombre del VSPackage `GUID`. Esta entrada del registro especifica la ubicación del archivo de recursos de la interfaz de usuario de VSPackage y el recurso de menú dentro de ese archivo. La entrada del registro en sí se encuentra en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<versión >* \Menus, donde  *\<versión >* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 9.0.

> [!NOTE]
>  La ruta de acceso raíz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versión >* puede reemplazarse por una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell se ha inicializado. Para obtener más información acerca de la ruta de acceso raíz, consulte [Installing VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>La entrada del registro de recursos CTMENU
 La estructura de la entrada del registro es:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> es el `GUID` de VSPackage en el formulario {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Información de recursos >* consta de tres elementos separados por comas. Estos elementos son, en orden:

 \<*Ruta de acceso al archivo DLL de recursos*>, \< *Id. de recurso de menú*>, \< *menú versión*>

 En la tabla siguiente se describe los campos de \< *información del recurso*>.


| Elemento | Descripción |
|---------------------------| - |
| \<*Ruta de acceso al archivo DLL de recursos*> | Se trata de la ruta de acceso completa a la DLL que contiene el recurso de menú de recursos o se deja en blanco, que indica que del VSPackage DLL de recursos es que se usará (como se especifica en la subclave paquetes donde se registra el VSPackage del propio).<br /><br /> Se suele dejar en blanco este campo. |
| \<*Id. de recurso de menú*> | Es el identificador de recurso de la `CTMENU` recursos que contiene todos los elementos de interfaz de usuario para el VSPackage como compilado a partir de un [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) archivo. |
| \<*Versión de menú*> | Se trata de un número que se utiliza como una versión para el `CTMENU` recursos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Este valor se utiliza para determinar si necesita volver a combinar el contenido de la `CTMENU` recursos con su memoria caché de todos los `CTMENU` recursos. Se desencadena un volver a combinar ejecutando el comando de instalación de devenv.<br /><br /> Este valor inicialmente se establece en 1 e incrementa después de cada cambio en el `CTMENU` recursos y antes de que ocurra el volver a combinar. |

### <a name="example"></a>Ejemplo
 Este es un ejemplo de un par de entradas de recursos:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vea también
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)