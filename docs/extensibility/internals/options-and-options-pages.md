---
title: Opciones y páginas de opciones | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c336503b80e2af34ac58c7debde16895d7f2585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314850"
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
Al hacer clic en **opciones** en el **herramientas** menú se abre el **opciones** cuadro de diálogo. Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol en el panel de navegación incluye las categorías de opciones, y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas le permiten cambiar los valores de las opciones que determinan el estado de un paquete VSPackage.

## <a name="support-for-options-pages"></a>Compatibilidad con páginas de opciones
 El <xref:Microsoft.VisualStudio.Shell.Package> proporciona compatibilidad para crear categorías de las opciones y páginas de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.

 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas para un usuario en una cuadrícula de propiedades genérica. Puede personalizar este comportamiento invalidando los métodos distintos en la página para crear una página de opciones personalizada que tiene su propia interfaz de usuario (UI). Para obtener más información, consulte [creación de una página de opciones](../../extensibility/creating-an-options-page.md).

 El <xref:Microsoft.VisualStudio.Shell.DialogPage> la clase implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que ofrece persistencia para las páginas de opciones y también para la configuración de usuario. Las implementaciones predeterminadas de la <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> métodos conservan los cambios de propiedad en una sección de usuario del registro si la propiedad se puede convertir a y desde una cadena.

## <a name="options-page-registry-path"></a>Ruta de acceso del registro de página de opciones
 De forma predeterminada, la ruta de acceso del registro de las propiedades que administra una página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra DialogPage y el nombre de tipo de la clase de página de opciones. Por ejemplo, una clase de página de opciones puede definirse como sigue.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Si la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> es HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, entonces los pares de nombre y valor de propiedad son las subclaves de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.

 La ruta de acceso del registro de la propia página de opciones se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra, ToolsOptionsPages y opciones de la página de categoría y el nombre. Por ejemplo, si la página de opciones personalizada tiene la categoría, My las páginas de opciones y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> es HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la página de opciones tiene la clave del registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\ToolsOptionsPages\My opción Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atributos de página y el diseño de herramientas/opciones
 El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina la agrupación de páginas de opciones personalizadas en las categorías en el árbol de navegación de la **opciones** cuadro de diálogo. El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones de VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Esto declara que MyPackage proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el **opciones** cuadro de diálogo, las páginas de opciones aparecen en la **Mis páginas de opciones** categoría como **General** y **personalizado**, respectivamente.

## <a name="option-attributes-and-layout"></a>Atributos de la opción y el diseño
 La interfaz de usuario (UI) que proporciona la página determina la apariencia de las opciones en una página de opciones personalizadas. El diseño, el etiquetado y la descripción de las opciones en una página genérica de opciones se determinan mediante los siguientes atributos:

- <xref:System.ComponentModel.CategoryAttribute> Determina la categoría de la opción.

- <xref:System.ComponentModel.DisplayNameAttribute> Determina el nombre para mostrar de la opción.

- <xref:System.ComponentModel.DescriptionAttribute> Determina la descripción de la opción.

  > [!NOTE]
  > Atributos equivalentes, SRCategory, LocDisplayName y SRDescription, use los recursos de cadena para la localización y se definen en el [proyecto administrado de ejemplo](http://go.microsoft.com/fwlink/?LinkId=122774).

  Observe el fragmento de código siguiente:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  La opción OptionInteger aparece en la página de opciones como **opción entero** en el **Mis opciones** categoría. Si se selecciona la opción, la descripción, **mi opción entero**, aparece en el cuadro de descripción.

## <a name="accessing-options-pages-from-another-vspackage"></a>Acceso a las páginas de opciones desde otro VSPackage
 Un VSPackage que hospeda y administra una página de opciones puede tener acceso mediante programación desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente, un VSPackage está registrado como una página de opciones de hospedaje.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 El fragmento de código siguiente obtiene el valor de OptionInteger de MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Cuando el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo registra una página de opciones, la página se registra en la clave AutomationProperties si el `SupportsAutomation` argumento del atributo es `true`. Automatización examina esta entrada del registro para buscar el VSPackage asociado y automatización, a continuación, se tiene acceso a la propiedad a través de la página de opciones hospedado, en este caso, mi página de cuadrícula.

 La ruta de acceso del registro de la propiedad de automatización se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la palabra AutomationProperties y las opciones de página de categoría y el nombre. Por ejemplo, si la página de opciones tiene la categoría de My Category, el nombre de mi página de cuadrícula y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propiedad de automatización tiene la clave del registro, HKEY_LOCAL_MACHINE\SOFTWARE\ Página de cuadrícula de Microsoft\VisualStudio\8.0Exp\AutomationProperties\My categoría\Mi.

> [!NOTE]
> El nombre canónico, mi página de cuadrícula Category.My, es el valor de la subclave de nombre de esta clave.