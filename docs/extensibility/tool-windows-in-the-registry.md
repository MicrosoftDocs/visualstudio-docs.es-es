---
title: Herramienta de Windows en el registro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 234a3f50865e77f2c6b5a4057e6766b26d7ff521
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138452"
---
# <a name="tool-windows-in-the-registry"></a>Ventanas de herramientas en el registro
VSPackages que proporcionan las ventanas de herramientas debe registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como proveedores de ventana de herramientas. Ventanas de herramientas creadas mediante la plantilla de paquete de Visual Studio hace esto de forma predeterminada. Los proveedores de ventana de herramienta tienen claves del registro del sistema que especifican los atributos de visibilidad, por ejemplo, el tamaño predeterminado de la ventana de herramienta y la ubicación, el GUID de la ventana que actúa como el panel de la ventana de herramienta y el estilo de acoplamiento.  
  
 Durante el desarrollo, los proveedores de ventana de herramientas administrada registran las ventanas de herramientas agregando atributos al código fuente y, a continuación, ejecuta la utilidad RegPkg.exe en el ensamblado resultante. Para obtener más información, consulte [registrando una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrar proveedores de ventana de herramienta no administrado  
 Proveedores de ventana de herramienta no administrado deben registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la sección de ToolWindows del registro del sistema. El siguiente fragmento del archivo .reg muestra cómo se puede registrar una ventana de herramientas dinámicas:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 En la primera clave en el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 7.1 u 8.0, la subclave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} es el GUID del panel de la ventana de herramienta (DynamicWindowPane) y el valor de predeterminada {} 01069cdd-95ce-4620-ac21-ddff6c57f012} es el GUID del VSPackage proporciona la ventana de herramientas. Para obtener una explicación de las subclaves Float y DontForceCreate, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
 La segunda clave opcional, ToolWindows\Visibility, especifica el GUID de comandos que requieran la ventana de herramientas debe hacer visible. En este caso, no hay ningún comando especificado. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)