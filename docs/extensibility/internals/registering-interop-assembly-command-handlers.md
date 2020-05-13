---
title: Registro de controladores de comandos de ensamblado de interoperabilidad ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705859"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registro de controladores de comandos de ensamblado de interoperabilidad
Un VSPackage debe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrarse para que el entorno de desarrollo integrado (IDE) enrute sus comandos correctamente.

 El registro se puede actualizar mediante la edición manual o mediante un archivo Registrar (.rgs). Para obtener más información, consulta [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed Package Framework (MPF) proporciona esta <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> funcionalidad a través de la clase.

- Los recursos de referencia de [formato](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) de tabla de comandos se encuentran en dll de interfaz de usuario satélite no administradas.

## <a name="command-handler-registration-of-a-vspackage"></a>Registro del controlador de comandos de un VSPackage
 Un VSPackage que actúa como controlador para comandos basados en la interfaz de usuario (UI) requiere una entrada del Registro con el nombre del VSPackage `GUID`. Esta entrada del Registro especifica la ubicación del archivo de recursos de interfaz de usuario de VSPackage y el recurso de menú dentro de ese archivo. La propia entrada del Registro se encuentra en\\HKEY_LOCAL_MACHINE, Software, Microsoft, VisualStudio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*\<Versión>* menús, donde * \<version>* es la versión de , por ejemplo, 9.0.

> [!NOTE]
> La ruta de acceso de la\\raíz de HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VisualStudio*\<Versión>* se puede invalidar con una raíz alternativa cuando se inicializa el shell. Para obtener más información acerca de la ruta de acceso raíz, vea [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>La entrada del Registro de Recursos CTMENU
 La estructura de la entrada del registro es:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` es el de vspackage en el formulario .XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX.

 Resource>consta de tres elementos separados por comas. * \<* Estos elementos son, en orden:

 \<*Ruta de acceso* \<a> DLL de recursos, ID de *recurso* de menú>, \< *Versión de menú*>

 En la tabla siguiente \<se describen los campos de *información* de recursos>.

| Elemento | Descripción |
|---------------------------| - |
| \<*Ruta de acceso a DLL de recursos*> | Esta es la ruta de acceso completa al archivo DLL de recursos que contiene el recurso de menú o se deja en blanco, lo que indica que se va a usar el archivo DLL de recursos de VSPackage (como se especifica en la subclave Packages donde se registra el propio VSPackage).<br /><br /> Es habitual dejar este campo en blanco. |
| \<*ID de recurso de menú*> | Este es el identificador `CTMENU` de recurso del recurso que contiene todos los elementos de interfaz de usuario para el VSPackage compilado a partir de un archivo [.vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Versión del menú*> | Este es un número utilizado `CTMENU` como versión para el recurso. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utiliza este valor para determinar si necesita recuperar `CTMENU` el contenido del `CTMENU` recurso con su caché de todos los recursos. Una refusión se desencadena ejecutando el comando devenv setup.<br /><br /> Este valor debe establecerse inicialmente en 1 e `CTMENU` incrementarse después de cada cambio en el recurso y antes de que se produzca la recombinación. |

### <a name="example"></a>Ejemplo
 A continuación se muestra un ejemplo de un par de entradas de recursos:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos y menús que usan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
