---
title: Opciones y páginas de opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4512867f636e2362aa28d52c5af28bf8eb9697f9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851148"
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al hacer clic en **Opciones** en el menú **herramientas** , se abre el cuadro de diálogo **Opciones** . Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol del panel de navegación incluye las categorías de opciones, y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.  
  
## <a name="support-for-options-pages"></a>Compatibilidad con páginas de opciones  
 La clase <xref:Microsoft.VisualStudio.Shell.Package> proporciona compatibilidad para crear páginas de opciones y categorías de opciones. La clase <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa una página de opciones.  
  
 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas a un usuario en una cuadrícula genérica de propiedades. Puede personalizar este comportamiento invalidando varios métodos en la página para crear una página de opciones personalizada que tenga su propia interfaz de usuario (IU). Para obtener más información, consulte [crear una página de opciones](../../extensibility/creating-an-options-page.md).  
  
 La clase <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que proporciona persistencia para las páginas de opciones y también para la configuración de usuario. Las implementaciones predeterminadas de los métodos <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> conservan los cambios de propiedad en una sección de usuario del registro si la propiedad se puede convertir en una cadena y desde ella.  
  
## <a name="options-page-registry-path"></a>Página de opciones ruta de acceso del registro  
 De forma predeterminada, la ruta de acceso del registro de las propiedades administradas por una página de opciones se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra DialogPage y el nombre de tipo de la clase de página Options. Por ejemplo, una clase de página de opciones podría definirse como se indica a continuación.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Si el <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> es HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, los pares de nombre y valor de propiedad son subclaves de HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.  
  
 La ruta de acceso del registro de la página de opciones se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra ToolsOptionsPages y la categoría y el nombre de la página de opciones. Por ejemplo, si la Página opciones personalizadas tiene la categoría, mis páginas de opciones y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> es HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, la Página opciones tiene la clave del registro HKEY_LOCAL_MACHINE opción \SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Herramientas/opciones página atributos y diseño  
 El atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> determina la agrupación de las páginas de opciones personalizadas en categorías en el árbol de navegación del cuadro de diálogo **Opciones** . El atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> asocia una página de opciones con el VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Esto declara que mi paquete proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el cuadro de diálogo **Opciones** , las dos páginas de opciones aparecen en la categoría **mis páginas** de opciones como **General** y **personalizada**, respectivamente.  
  
## <a name="option-attributes-and-layout"></a>Atributos y diseño de opciones  
 La interfaz de usuario (UI) que proporciona la página determina el aspecto de las opciones de una página de opciones personalizada. El diseño, el etiquetado y la descripción de las opciones de una página de opciones genérica se determinan mediante los siguientes atributos:  
  
- <xref:System.ComponentModel.CategoryAttribute> determina la categoría de la opción.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> determina el nombre para mostrar de la opción.  
  
- <xref:System.ComponentModel.DescriptionAttribute> determina la descripción de la opción.  
  
  > [!NOTE]
  > Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en el [ejemplo de proyecto administrado](https://msdn.com/vsx).  
  
  Observe el fragmento de código siguiente:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  La opción OptionInteger aparece en la Página opciones como una **opción de entero** en la categoría **mis opciones** . Si se selecciona la opción, la opción Descripción, **mi entero**, aparecerá en el cuadro Descripción.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Obtener acceso a las páginas de opciones desde otro VSPackage  
 Se puede tener acceso mediante programación a un VSPackage que hospede y administre una página de opciones desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente se registra un VSPackage como hospedaje de una página de opciones.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 El siguiente fragmento de código obtiene el valor de OptionInteger de MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Cuando el atributo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> registra una página de opciones, la página se registra bajo la clave AutomationProperties si el argumento de `SupportsAutomation` del atributo es `true`. Automation examina esta entrada del registro para buscar el VSPackage asociado y, a continuación, la automatización accede a la propiedad a través de la página Opciones hospedadas, en este caso, mi página de cuadrícula.  
  
 La ruta de acceso del registro de la propiedad Automation se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra AutomationProperties y la categoría y el nombre de la página de opciones. Por ejemplo, si la página de opciones tiene la categoría mi categoría, el nombre de la página mi cuadrícula y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propiedad Automation tiene la clave del registro HKEY_LOCAL_MACHINE página de cuadrícula de \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My.  
  
> [!NOTE]
> La página de la cuadrícula nombre canónico, mi Category.My, es el valor de la subclave Name de esta clave.
