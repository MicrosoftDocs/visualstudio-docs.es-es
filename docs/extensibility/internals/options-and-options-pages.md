---
title: Páginas de opciones y opciones | Microsoft Docs
description: Obtenga información sobre la compatibilidad con las páginas de opciones, que le permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea05e894c0bfca077f1256c35e6fbe5c58bc91ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899893"
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
Al **hacer clic en** Opciones en el **menú** Herramientas, se abre el **cuadro de** diálogo Opciones . Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol del panel de navegación incluye categorías de opciones y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.

## <a name="support-for-options-pages"></a>Compatibilidad con páginas de opciones
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para crear páginas de opciones y categorías de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.

 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas a un usuario en una cuadrícula genérica de propiedades. Para personalizar este comportamiento, invalide varios métodos de la página para crear una página de opciones personalizada que tenga su propia interfaz de usuario (UI). Para obtener más información, vea [Crear una página de opciones](../../extensibility/creating-an-options-page.md).

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa , que proporciona persistencia para las páginas de opciones y también para la configuración de <xref:Microsoft.VisualStudio.Shell.IProfileManager> usuario. Las implementaciones predeterminadas de los métodos y conservan los cambios de propiedad en una sección de usuario del Registro si la propiedad se puede convertir a y <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> desde una cadena.

## <a name="options-page-registry-path"></a>Ruta de acceso del Registro de la página Opciones
 De forma predeterminada, la ruta de acceso del Registro de las propiedades administradas por una página de opciones se determina mediante la combinación de , la palabra DialogPage y el nombre de tipo de la <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> clase de página options. Por ejemplo, una clase de página de opciones se puede definir de la siguiente manera.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 Si se ha HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, los pares de nombre de propiedad y valor <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> son subclaves de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 La ruta de acceso del Registro de la propia página de opciones se determina mediante la combinación de , la palabra ToolsOptionsPages y la categoría y el nombre de la página <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> de opciones. Por ejemplo, si la página Opciones personalizadas tiene la categoría Mis páginas de opciones y es HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la página de opciones tiene la clave del <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> Registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atributos y diseño de la página Herramientas/Opciones
 El atributo determina la agrupación de páginas de opciones personalizadas <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> en categorías en el árbol de navegación del cuadro de **diálogo** Opciones. El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones con el VSPackage que proporciona la interfaz . Observe el fragmento de código siguiente:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Esto declara que MyPackage proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el **cuadro de** diálogo Opciones, ambas páginas de opciones aparecen en la categoría Mis páginas **de** opciones como **General** y **Personalizado,** respectivamente.

## <a name="option-attributes-and-layout"></a>Atributos y diseño de la opción
 La interfaz de usuario (UI) que proporciona la página determina la apariencia de las opciones en una página de opciones personalizada. El diseño, el etiquetado y la descripción de las opciones de una página de opciones genéricas se determinan mediante los atributos siguientes:

- <xref:System.ComponentModel.CategoryAttribute> determina la categoría de la opción.

- <xref:System.ComponentModel.DisplayNameAttribute> determina el nombre para mostrar de la opción.

- <xref:System.ComponentModel.DescriptionAttribute> determina la descripción de la opción.

  > [!NOTE]
  > Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en el [ejemplo de proyecto administrado](/azure/devops/integrate/index).

  Observe el fragmento de código siguiente:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  La opción OptionInteger aparece en la página de opciones como **Opción de entero** en la categoría **Mis** opciones. Si la opción está seleccionada, la descripción, **Mi opción de entero**, aparece en el cuadro de descripción.

## <a name="accessing-options-pages-from-another-vspackage"></a>Acceso a páginas de opciones desde otro VSPackage
 Se puede acceder mediante programación a un VSPackage que hospeda y administra una página de opciones desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente, un VSPackage se registra como hospedaje de una página de opciones.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 El fragmento de código siguiente obtiene el valor de OptionInteger de MyOptionPage:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Cuando el atributo registra una página de opciones, la página se registra en la clave AutomationProperties si el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> argumento del atributo es `SupportsAutomation` `true` . Automation examina esta entrada del Registro para buscar el VSPackage asociado y, a continuación, la automatización accede a la propiedad a través de la página de opciones hospedadas, en este caso, Mi página de cuadrícula.

 La ruta de acceso del Registro de la propiedad de automatización se determina mediante la combinación de , la palabra AutomationProperties y la categoría y el nombre de la página <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> de opciones. Por ejemplo, si la página de opciones tiene la categoría Mi categoría, el nombre mi página de cuadrícula y , HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propiedad de automatización tiene la clave del <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> Registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> El nombre canónico, My Category.My Grid Page, es el valor de la subclave Name de esta clave.
