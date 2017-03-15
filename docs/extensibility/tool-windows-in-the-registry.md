---
title: "Ventanas de herramientas en el registro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, registrar"
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Ventanas de herramientas en el registro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages que proporcionan las ventanas de herramientas debe registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como proveedores de la ventana de herramientas.  Las ventanas de herramientas creadas con la plantilla paquete de Visual Studio hacen esto de forma predeterminada.  Los proveedores de la ventana de herramientas tienen claves del registro del sistema que especifican atributos de visibilidad, como el tamaño y ubicación de la ventana de herramientas predeterminada, GUID de la ventana que actúa como el panel de la ventana de herramientas, y el estilo de acoplamiento.  
  
 Durante el desarrollo, los proveedores administrados de la ventana de herramientas registran las ventanas de herramientas agregando atributos al código fuente, y después ejecutando la utilidad de RegPkg.exe en el ensamblado resultante.  Para obtener más información, vea [Registrar una ventana de herramientas](../extensibility/registering-a-tool-window.md).  
  
## Registrar los proveedores no administrada de la ventana de herramientas  
 Los proveedores no administrada de la ventana de herramientas deben registrar con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la sección de ToolWindows de registro del sistema.  El siguiente fragmento de archivo .reg muestra cómo una ventana de herramientas dinámica puede registrarse:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 En la primera clave en el ejemplo anterior, el número de versión es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 7,1 o 8,0, la subclave {f0e1e9a1\-9860\-484d\-ad5d\-367d79aabf55} es el GUID del panel de la ventana de herramientas \(DynamicWindowPane\), y el valor predeterminado {01069cdd\-95ce\-4620\-ac21\-ddff6c57f012} es el GUID del Paquete que proporciona a la ventana de herramientas.  Para obtener una explicación de las subclaves Float y de DontForceCreate, vea [Configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
 La segunda clave opcional, ToolWindows \\Visibility, specifies the GUIDs de los comandos que requieren la ventana de herramientas para crear visible.  en este caso, no hay comandos especificados.  Para obtener más información, vea [Configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).  
  
## Vea también  
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)