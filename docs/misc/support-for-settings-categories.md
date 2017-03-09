---
title: "Compatibilidad con categor&#237;as de configuraci&#243;n | Microsoft Docs"
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
  - "configuración, compatibilidad con el SDK de Visual Studio"
  - "SDK de Visual Studio, compatibilidad de configuración"
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Compatibilidad con categor&#237;as de configuraci&#243;n
Una categoría de configuración consta de un grupo de opciones que personalizan el entorno de desarrollo integrado \(IDE\). Por ejemplo, la configuración puede controlar el diseño de las ventanas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y el contenido de los menús. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 En el menú **Herramientas**, haga clic en **Importar y exportar configuraciones** para iniciar el **Asistente para importar y exportar configuraciones**. El asistente ofrece tres opciones: exportar, importar o restablecer la configuración. Por ejemplo, si selecciona exportar, se abre la página del asistente **Elija la configuración para exportar**.  
  
 En el control de árbol del panel de navegación de esta página se muestran las categorías. Una categoría es un grupo de valores de configuración relacionados que aparecen como "punto de configuración personalizada", es decir, como una casilla. Estas casillas se usan para seleccionar las categorías de modo que se conserven en un archivo .vsettings. El asistente permite asignar un nombre al archivo .vsettings y especificar su ruta de acceso.  
  
> [!NOTE]
>  La configuración se guarda o se restaura como una categoría y los nombres de los valores de configuración individuales no se muestran en el asistente.  
  
 El marco de trabajo de paquetes administrados \(MPF\) admite la creación de categorías de configuración con un mínimo de código adicional.  
  
-   Cree un VSPackage para proporcionar un contenedor para la categoría mediante la creación de subclases en la clase <xref:Microsoft.VisualStudio.Shell.Package>.  
  
-   Cree la categoría en sí derivándola de la clase <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
-   Conéctelos con <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Compatibilidad con categorías de configuración  
 La clase <xref:Microsoft.VisualStudio.Shell.Package> proporciona compatibilidad para la creación de categorías. La clase <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa una categoría. La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas a un usuario como una categoría. Para obtener más información, consulta [Creación de una categoría de configuración](../extensibility/creating-a-settings-category.md).  
  
 La clase <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que ofrece persistencia para las páginas de opciones y la configuración del usuario. Los métodos <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> conservan la configuración en un archivo .vssettings que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona como <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, respectivamente. El método <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> restablece la configuración a sus valores predeterminados.  
  
 La clase <xref:Microsoft.VisualStudio.Shell.DialogPage> proporciona una implementación del método <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> que lee los pares nombre\-valor de la fuente XML y usa la reflexión para detectar propiedades públicas en la clase derivada <xref:Microsoft.VisualStudio.Shell.DialogPage>. Las propiedades que tienen nombres que coinciden con los pares nombre\-valor reciben los valores correspondientes.  
  
 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> usa la reflexión para detectar propiedades públicas en la clase derivada <xref:Microsoft.VisualStudio.Shell.DialogPage> y escribe los nombres y valores de propiedad en la fuente XML como pares nombre\-valor.  
  
### Ruta de acceso al Registro de la categoría de configuración  
 La ruta de acceso al Registro de la categoría de configuración se determina mediante la combinación de la propiedad <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra UserSettings, la categoría de configuración y el nombre del punto de configuración personalizada. Los nombres de la categoría de configuración y del punto de configuración personalizada se combinan y se separan con un carácter de subrayado para formar el nombre canónico no localizado que aparece en el Registro. Por ejemplo, si la categoría de configuración es "My Category", el nombre del punto de configuración personalizada es "My Settings" y la propiedad ApplicationRegistryRoot es HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, la categoría de configuración tiene la clave del Registro HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\UserSettings\\My Category\_My Settings.  
  
> [!NOTE]
>  El nombre canónico no aparece en una interfaz de usuario. Se usa para asociar un nombre legible con la categoría de configuración, como si se tratase de un identificador de programación \(ProgID\).  
  
### Atributo de la categoría de configuración  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> determina la asignación de categorías a los puntos de configuración personalizada en el **Asistente para importar y exportar configuraciones** asociando una categoría con el VSPackage que la proporciona. Observe el fragmento de código siguiente:  
  
 [!code-vb[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/VisualBasic/support-for-settings-categories_1.vb)]
 [!code-cs[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/CSharp/support-for-settings-categories_1.cs)]  
  
 El identificador de recurso 106 asigna a "My Category", el 107 a "My Settings" y el 108 a "Various Options". Esto declara que `MyPackage` proporciona la categoría, My Category\_My Settings. La categoría se proporcionada mediante la clase `OptionsPageGeneral`, que debe implementar <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Los valores de configuración de esa categoría son las propiedades públicas de la clase `OptionsPageGeneral`.  
  
 En el **Asistente para importar y exportar configuraciones**, el punto de configuración tiene el nombre My Settings. Cuando se selecciona el punto de configuración, aparece la descripción **Various Options**. El nombre y la descripción del punto de configuración se toman de recursos de cadena localizada.  
  
## Vea también  
 [Creación de una página de opciones](../extensibility/creating-an-options-page.md)   
 [Muestras de VSSDK](../misc/vssdk-samples.md)   
 [Estado de VSPackage](../misc/vspackage-state.md)   
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)