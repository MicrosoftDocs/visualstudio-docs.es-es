---
title: "Opciones y p&#225;ginas de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Opciones de páginas [Visual Studio SDK] administradas paquete framework compatibilidad de las herramientas"
  - "marco de paquete administrado, compatibilidad de páginas de opciones de herramientas"
  - "compatibilidad de páginas de opciones de herramientas"
  - "Las páginas de opciones [Visual Studio SDK], los diseños de las herramientas"
  - "Páginas de opciones de herramientas [Visual Studio SDK], atributos"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Opciones y p&#225;ginas de opciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Haga clic en **opciones** en el **herramientas** menú abre la **opciones** cuadro de diálogo. Las opciones de este cuadro de diálogo se conocen como páginas de opciones. El control de árbol en el panel de navegación incluye las categorías de opciones, y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas le permiten cambiar los valores de las opciones que determinan el estado de un paquete VSPackage.  
  
## Compatibilidad con las páginas de opciones  
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para crear categorías de opciones y páginas de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.  
  
 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas a un usuario en una cuadrícula de propiedades genérica. Puede personalizar este comportamiento invalidando los métodos distintos de la página para crear una página de opciones personalizadas que tiene su propia interfaz de usuario \(UI\). Para obtener más información, consulta [Creación de una página de opciones](../../extensibility/creating-an-options-page.md).  
  
 La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que proporciona la persistencia de las páginas de opciones y de configuración de usuario. Las implementaciones predeterminadas de los <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> métodos conservan los cambios de propiedad en una sección del registro de usuario si la propiedad se puede convertir a y desde una cadena.  
  
## Ruta de acceso del registro de página de opciones  
 De forma predeterminada, la ruta de acceso del registro de las propiedades administradas por una página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra DialogPage y el nombre de tipo de la clase de página de opciones. Por ejemplo, una clase de página de opciones puede definirse como sigue.  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 Si la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> es HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, entonces los pares de nombre y valor de propiedad son subclaves de HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral.  
  
 La ruta de acceso del registro de la página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra, ToolsOptionsPages y las opciones de página de categoría y el nombre. Por ejemplo, si la página de opciones personalizado tiene la categoría, Mis páginas de opciones y <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> es HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, entonces la página de opciones tiene la clave de registro HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My opción Pages\\Custom.  
  
## Atributos de la página de herramientas, opciones y el diseño  
 El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina la agrupación de páginas de opciones personalizadas en categorías en el árbol de navegación de la **opciones** cuadro de diálogo. El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones de VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 Esto declara que MyPackage proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el **opciones** cuadro de diálogo, las páginas de opciones aparecen en la **opción Mis páginas** categoría como **General** y **personalizado**, respectivamente.  
  
## Atributos de opciones y el diseño  
 La interfaz de usuario \(UI\) que proporciona la página determina la apariencia de las opciones de una página de opciones personalizadas. El diseño, etiquetado y descripción de las opciones en una página de opciones genéricas están determinados por los siguientes atributos:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Determina la categoría de la opción.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Determina el nombre para mostrar de la opción.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Determina la descripción de la opción.  
  
    > [!NOTE]
    >  Atributos equivalentes, SRCategory, LocDisplayName y SRDescription, utilice los recursos de cadena para la localización y se definen en el [proyecto administrado de ejemplo](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Observe el fragmento de código siguiente:  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 La opción OptionInteger aparece en la página de opciones como **opción entero** en el **Mis opciones** categoría. Si la opción está seleccionada, la descripción, **Mi opción entero**, aparece en el cuadro Descripción.  
  
## Acceso a las páginas de opciones de VSPackage otro  
 Puede accederse mediante programación a un VSPackage que se hospeda y administra una página de opciones de VSPackage otro mediante el modelo de automatización. Por ejemplo, en el código siguiente se registra un VSPackage como una página de opciones de hospedaje.  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 El fragmento de código siguiente obtiene el valor de OptionInteger de MyOptionPage:  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 Cuando el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo registra una página de opciones, la página está registrada en la clave AutomationProperties si la `SupportsAutomation` es el argumento del atributo `true`. Automatización examina esta entrada del registro para buscar el VSPackage asociado y automatización, a continuación, se tiene acceso a la propiedad a través de la página de opciones hospedado, en este caso, mi página de cuadrícula.  
  
 La ruta de acceso del registro de la propiedad de automatización se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra AutomationProperties y las opciones de página de categoría y el nombre. Por ejemplo, si la página de opciones tiene mi la categoría, el nombre de mi página de cuadrícula y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp y, a continuación, la propiedad de automatización tiene una clave del registro, página de cuadrícula de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My categoría\\Mi.  
  
> [!NOTE]
>  El nombre canónico, mi página de cuadrícula de Category.My es el valor de la subclave de nombre de esta clave.