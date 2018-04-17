---
title: Opciones y páginas de opciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d85b900779a5df8af077b292b2e2f70b0592e35c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
Al hacer clic en **opciones** en el **herramientas** menú abre la **opciones** cuadro de diálogo. Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol en el panel de navegación incluye categorías de opciones, y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas le permiten cambiar los valores de las opciones que determinan el estado de un paquete VSPackage.  
  
## <a name="support-for-options-pages"></a>Compatibilidad con páginas de opciones  
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para crear páginas de opciones y las categorías de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.  
  
 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas para un usuario en una cuadrícula de propiedades genérica. Puede personalizar este comportamiento al invalidar los métodos distintos de la página para crear una página de opciones personalizada que tiene su propia interfaz de usuario (UI). Para obtener más información, consulte [crear una página de opciones](../../extensibility/creating-an-options-page.md).  
  
 El <xref:Microsoft.VisualStudio.Shell.DialogPage> la clase implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que proporciona la persistencia de páginas de opciones y de configuración de usuario. Las implementaciones predeterminadas de la <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> métodos conservan los cambios de propiedad en una sección de usuario del registro si la propiedad se puede convertir a y desde una cadena.  
  
## <a name="options-page-registry-path"></a>Ruta de acceso del registro de página de opciones  
 De forma predeterminada, la ruta de acceso del registro de las propiedades administradas por una página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra DialogPage y el nombre de tipo de la clase de página de opciones. Por ejemplo, una clase de página de opciones puede definirse como sigue.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Si la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> es HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, a continuación, los pares de nombre y valor de propiedad son subclaves de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 La ruta de acceso del registro de la propia página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra, ToolsOptionsPages y las opciones de página de categoría y el nombre. Por ejemplo, si la página de opciones de personalización tiene la categoría, páginas de Mis opciones y <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> es HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, a continuación, la página de opciones tiene la clave de registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My opción Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Atributos de la página de herramientas/opciones y el diseño  
 El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina la agrupación de páginas de opciones personalizadas en categorías en el árbol de navegación de la **opciones** cuadro de diálogo. El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones de VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Esto declara que MyPackage proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el **opciones** cuadro de diálogo, las páginas de opciones aparecen en la **Mis páginas de opciones** categoría como **General** y **personalizado**, respectivamente.  
  
## <a name="option-attributes-and-layout"></a>Atributos de opción y el diseño  
 La interfaz de usuario (UI) que proporciona la página determina la apariencia de las opciones de una página de opciones personalizadas. El diseño, el etiquetado y la descripción de las opciones en una página de opciones genéricas se determinan por los atributos siguientes:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Determina la categoría de la opción.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Determina el nombre para mostrar de la opción.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Determina la descripción de la opción.  
  
    > [!NOTE]
    >  Atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usar los recursos de cadena para la localización y se definen en el [proyecto administrado de ejemplo](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Observe el fragmento de código siguiente:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 La opción OptionInteger aparece en la página de opciones como **opción entero** en el **Mis opciones** categoría. Si la opción está seleccionada, la descripción, **mi opción entero**, aparece en el cuadro Descripción.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Acceso a las páginas de opciones desde otro VSPackage  
 Un VSPackage que hospeda y administra una página de opciones puede tener acceso mediante programación desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente se registra un VSPackage como una página de opciones de hospedaje.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 El fragmento de código siguiente obtiene el valor de OptionInteger de MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Cuando el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo registra una página de opciones, la página está registrada en la tecla AutomationProperties si la `SupportsAutomation` argumento del atributo es `true`. Automatización examina esta entrada del registro para buscar el VSPackage asociado y automatización, a continuación, se tiene acceso a la propiedad a través de la página de opciones hospedado, en este caso, mi página de cuadrícula.  
  
 La ruta de acceso del registro de la propiedad de automatización se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra, AutomationProperties y las opciones de página de categoría y el nombre. Por ejemplo, si la página de opciones tiene la categoría de mi categoría, el nombre de mi página de cuadrícula y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp y, a continuación, la propiedad de automatización tiene la clave de registro HKEY_LOCAL_MACHINE\SOFTWARE\ Página de cuadrícula de Microsoft\VisualStudio\8.0Exp\AutomationProperties\My categoría\Mi.  
  
> [!NOTE]
>  El nombre canónico, mi página de cuadrícula de Category.My, es el valor de la subclave de nombre de esta clave.