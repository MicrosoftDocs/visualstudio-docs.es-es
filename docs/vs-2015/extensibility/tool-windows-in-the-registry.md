---
title: Ventanas de herramientas en el registro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186383"
---
# <a name="tool-windows-in-the-registry"></a>Ventanas de herramientas del Registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los VSPackages que proporcionan ventanas de herramientas deben registrarse con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como proveedores de ventanas de herramientas. Las ventanas de herramientas creadas con la plantilla de paquete de Visual Studio lo hacen de forma predeterminada. Los proveedores de ventanas de herramientas tienen claves de registro del sistema que especifican atributos de visibilidad, como el tamaño y la ubicación de la ventana de herramientas predeterminada, el GUID de la ventana que actúa como el panel de la ventana de herramientas y el estilo de acoplamiento.  
  
 Durante el desarrollo, los proveedores de ventanas de herramientas administradas registran las ventanas de herramientas agregando atributos al código fuente y, a continuación, ejecutan la utilidad RegPkg.exe en el ensamblado resultante. Para obtener más información, vea [registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrar proveedores de ventanas de herramientas no administradas  
 Los proveedores de ventanas de herramientas no administradas deben registrarse [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en en la sección ToolWindows del registro del sistema. En el siguiente fragmento de archivo. reg se muestra cómo se puede registrar una ventana de herramientas dinámica:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 En la primera clave del ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , como 7,1 o 8,0, la subclave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} es el GUID del panel de la ventana de herramientas (DynamicWindowPane) y el valor predeterminado {01069cdd-95CE-4620-AC21-ddff6c57f012} es el GUID del VSPackage que proporciona la ventana de herramientas. Para obtener una explicación de las subclaves float y DontForceCreate, consulte Configuración de presentación de la [ventana de herramientas](../extensibility/tool-window-display-configuration.md).  
  
 La segunda clave opcional, ToolWindows\Visibility, especifica los GUID de los comandos que requieren que la ventana de herramientas se haga visible. En este caso, no se han especificado comandos. Para obtener más información, vea configuración de visualización de la [ventana de herramientas](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Consulte también  
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)
