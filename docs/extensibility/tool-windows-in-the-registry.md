---
title: Windows en el registro de herramientas | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b74081f474e85b97f46db5250daf042dbd6b917
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316392"
---
# <a name="tool-windows-in-the-registry"></a>Ventanas de herramientas del Registro
Los VSPackages que proporcionan las ventanas de herramientas se debe registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como proveedores de la ventana de herramientas. Ventanas de herramientas creadas con la plantilla de paquete de Visual Studio hace esto de forma predeterminada. Proveedores de ventana de herramientas tienen las claves del registro del sistema que especifican los atributos de visibilidad, como tamaño predeterminado de la ventana de herramienta y la ubicación, el GUID de la ventana que actúa como el panel de ventana de herramientas y el estilo de acoplamiento.

 Durante el desarrollo, los proveedores de ventana de herramientas administrada registran ventanas de herramientas mediante la adición de atributos al código fuente y, a continuación, ejecute la utilidad RegPkg.exe en el ensamblado resultante. Para obtener más información, consulte [registrando una ventana de herramientas](../extensibility/registering-a-tool-window.md).

## <a name="registering-unmanaged-tool-window-providers"></a>Registrar proveedores de ventana de herramienta no administrado
 Proveedores de ventana de herramientas no administrado deben registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la sección de ToolWindows del registro del sistema. El siguiente fragmento del archivo .reg muestra cómo se puede registrar una ventana de herramientas dinámica:

```
- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"
"Float"="250, 250, 410, 430"
"DontForceCreate"=dword:00000001

- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000
```

 En la primera clave en el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 7.1 u 8.0, la subclave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} es el GUID del panel de la ventana de herramienta (DynamicWindowPane) y el valor de predeterminada {} 01069cdd-95ce-4620-ac21-ddff6c57f012} es el GUID del VSPackage que proporciona la ventana de herramientas. Para obtener una explicación de las subclaves Float y DontForceCreate, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).

 La segunda clave opcional, ToolWindows\Visibility, especifica el GUID de los comandos que requieren la ventana de herramientas debe hacer visible. En este caso, no hay ningún comando especificado. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)