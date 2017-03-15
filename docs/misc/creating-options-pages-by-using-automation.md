---
title: "Crear p&#225;ginas de opciones mediante automatizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "páginas de opciones de herramientas [SDK de Visual Studio], crear"
  - "automatización [SDK de Visual Studio], crear páginas de opciones de herramientas"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Crear p&#225;ginas de opciones mediante automatizaci&#243;n
VSPackages administrado puede utilizar la automatización para extender el entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agregando las páginas de **Opciones** al menú de **Herramientas** .  
  
 una página de **Opciones de herramientas** es fundamental un control de usuario, y se codifica igual que cualquier otro control de usuario.  Normalmente, utilizaría a uno de los diseñadores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el IDE para crear el objeto y agregar los controles de usuario.  
  
> [!NOTE]
>  Las páginas de**Opciones de herramientas** implementadas como cuadro de diálogo, mediante `DialogProc` para controlar mensajes de ventanas, deben ser cuadros de diálogo no modal, y no deben llamar a la función de `EndDialog` .  
  
 Debe utilizar el objeto de automatización que el paquete VSPackage proporciona el entorno a las propiedades admiten el control de usuario.  
  
## Compatibilidad con la automatización de las páginas opciones de herramientas implementadas con ensamblados de Interoperabilidad  
 Para admitir el modelo de automatización, un VSPackage debe crear y registrar un objeto de automatización.  Para obtener más información, consulte [Automatización de VSPackages](../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Cuando el código que utiliza el modelo de automatización llama `DTE.Properties` para la colección de las propiedades de una página determinada de **Opciones de herramientas** , el IDE utiliza el objeto de automatización proporciona la implementación del Paquete de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> para devolver la colección y para permitir el acceso a los objetos constituyentes de <xref:EnvDTE.Property> .  
  
 El objeto de automatización de**la nota**devuelto por <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> depende de GUID proporcionado \(como un VSPackage puede admitir más de un objeto de automatización\).  Para obtener más información sobre cómo implementar objetos de automatización, vea [Compatibilidad de automatización para las páginas de opciones](../extensibility/internals/automation-support-for-options-pages.md).  
  
 una página de **Opciones de herramientas** es especificada por dos identificadores.  El primer identificador es una cadena que indica la carpeta que contiene el elemento en la sección de **Opciones** de menú de **Herramientas** .  El segundo identificador es una cadena que indica el elemento específico de la carpeta.  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md).  
  
 Dos entradas de Registro se requieren para registrar un objeto de automatización:  
  
-   En HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<versión* \\Packages \\*\< PackageGUID\>* \\Automation  
  
-   En HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\ *\<versión\>* \\AutomationProperties  
  
     donde es la versión  *\<versión\>*  de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como 8,0\) y  *\<PackageGUID\>*  es el GUID del Paquete que implementa el objeto de automatización.  
  
 Dependiendo de la configuración bajo la entrada del Registro AutomationProperties, el estado de una página de **Opciones de herramientas** puede automáticamente guardarse y ser restaurada a través del mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario selecciona el comando de **Opciones para importar o exportar** en el menú de **Herramientas** .  Para obtener más información sobre cómo la configuración de **Opciones de herramientas** , vea [Registro de páginas de opciones personalizadas](../misc/registering-custom-options-pages.md).  
  
 Una aplicación no puede usar el modelo de automatización para implementar la compatibilidad para las propiedades y valores de una página de **Opciones de herramientas** .  
  
 esto puede ser deseable por varias razones:  
  
-   Los valores controla la página de **Opciones de herramientas** son más complejos en estructura que el modelo relativamente plano de la propiedad de automatización admite.  
  
-   Es necesario para evitar que otras aplicaciones mediante programación administrar la página de **Opciones de herramientas** .  
  
-   se requieren los controles de acceso o las características de seguridad especiales.  
  
 En estos casos, VSPackages puede implementar la compatibilidad de la página de **Opciones de herramientas** de la forma apropiada.  Sin embargo, debe:  
  
-   Controle el valor de las propiedades de página de **Opciones de herramientas** .  
  
-   Administrar la persistencia del estado de la página de **Opciones de herramientas** a través de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
-   Proporcione API, si se desea, para que otras aplicaciones utilizan la página de **Opciones de herramientas** .  
  
 Propiedades del cuadro de diálogo de **Fuentes y colores** son un ejemplo de una página de **Opciones de herramientas** que no puedan modificar a través del modelo de automatización.  En su lugar, API independiente se proporciona, en función de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para permitir la manipulación mediante programación de la página de **Fuentes y coloresOpciones de herramientas** .  Para obtener más información sobre cómo controlar la página de **Fuentes y coloresOpciones de herramientas** , vea [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## Compatibilidad con la automatización de las páginas opciones Dentro de las herramientas el managed package  
 Establezca la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> de la instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> de una implementación que registrando para indicar que una implementación administrada de la Marco\-base de paquete de una página de **Opciones de herramientas** admita automatización.  
  
 Las páginas de**Opciones de herramientas** derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> se proporcionan con un objeto predeterminado de automatización, que puede ser invalidado.  
  
 Si una aplicación de página de **Opciones de herramientas** no admite la automatización, la implementación debe proporcionar su propio API para permitir el acceso mediante programación a la página de **Opciones de herramientas** .  
  
> [!NOTE]
>  La página de **Fuentes y colores** del IDE es un ejemplo de una página de **Opciones de herramientas** que no admite la automatización, pero proporciona acceso a la página de **Opciones de herramientas** con su propio API.  Para obtener más información, vea [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
## Vea también  
 [Ampliar el entorno de Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Crear páginas de opciones mediante ensamblados de interoperabilidad](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Crear páginas de opciones](../extensibility/internals/creating-options-pages.md)   
 [Cómo: Crear páginas de opciones personalizadas](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Compatibilidad de automatización para las páginas de opciones](../extensibility/internals/automation-support-for-options-pages.md)   
 [Usar páginas de opciones](../misc/using-options-pages.md)