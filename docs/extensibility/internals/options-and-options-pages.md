---
title: Opciones y páginas de opciones | Microsoft Docs
description: Obtenga información sobre la compatibilidad con las páginas de opciones, que permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 32bcb32c4fc80a5806c9007c3119a2ba3de62427
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214517"
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
Al hacer clic en **Opciones** en el menú **herramientas** , se abre el cuadro de diálogo **Opciones** . Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol del panel de navegación incluye las categorías de opciones, y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.

## <a name="support-for-options-pages"></a>Compatibilidad con páginas de opciones
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para crear páginas de opciones y categorías de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.

 La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> ofrece sus propiedades públicas a un usuario en una cuadrícula genérica de propiedades. Puede personalizar este comportamiento invalidando varios métodos en la página para crear una página de opciones personalizada que tenga su propia interfaz de usuario (IU). Para obtener más información, consulte [crear una página de opciones](../../extensibility/creating-an-options-page.md).

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> , que proporciona persistencia para las páginas de opciones y también para la configuración de usuario. Las implementaciones predeterminadas de los <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> métodos y conservan los cambios de propiedad en una sección de usuario del registro si la propiedad se puede convertir a y desde una cadena.

## <a name="options-page-registry-path"></a>Página de opciones ruta de acceso del registro
 De forma predeterminada, la ruta de acceso del registro de las propiedades administradas por una página de opciones se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , la palabra DialogPage y el nombre de tipo de la clase de página de opciones. Por ejemplo, una clase de página de opciones podría definirse como se indica a continuación.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 Si <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> se HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, los pares de nombre y valor de propiedad son subclaves de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 La ruta de acceso del registro de la página de opciones se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , la palabra ToolsOptionsPages y la categoría y el nombre de la página de opciones. Por ejemplo, si la Página opciones personalizadas tiene la categoría, mis páginas de opciones y <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> es HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la Página opciones tiene la clave del registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Herramientas/opciones página atributos y diseño
 El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina la agrupación de las páginas de opciones personalizadas en categorías en el árbol de navegación del cuadro de diálogo **Opciones** . El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones al VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Esto declara que mi paquete proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el cuadro de diálogo **Opciones** , las dos páginas de opciones aparecen en la categoría **mis páginas** de opciones como **General** y **personalizada**, respectivamente.

## <a name="option-attributes-and-layout"></a>Atributos y diseño de opciones
 La interfaz de usuario (UI) que proporciona la página determina el aspecto de las opciones de una página de opciones personalizada. El diseño, el etiquetado y la descripción de las opciones de una página de opciones genérica se determinan mediante los siguientes atributos:

- <xref:System.ComponentModel.CategoryAttribute> determina la categoría de la opción.

- <xref:System.ComponentModel.DisplayNameAttribute> determina el nombre para mostrar de la opción.

- <xref:System.ComponentModel.DescriptionAttribute> determina la descripción de la opción.

  > [!NOTE]
  > Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en el [ejemplo de proyecto administrado](/azure/devops/integrate/index).

  Observe el fragmento de código siguiente:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  La opción OptionInteger aparece en la Página opciones como una **opción de entero** en la categoría **mis opciones** . Si se selecciona la opción, la opción Descripción, **mi entero**, aparecerá en el cuadro Descripción.

## <a name="accessing-options-pages-from-another-vspackage"></a>Obtener acceso a las páginas de opciones desde otro VSPackage
 Se puede tener acceso mediante programación a un VSPackage que hospede y administre una página de opciones desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente se registra un VSPackage como hospedaje de una página de opciones.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 El siguiente fragmento de código obtiene el valor de OptionInteger de MyOptionPage:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Cuando el <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo registra una página de opciones, la página se registra bajo la clave AutomationProperties si el `SupportsAutomation` argumento del atributo es `true` . Automation examina esta entrada del registro para buscar el VSPackage asociado y, a continuación, la automatización accede a la propiedad a través de la página Opciones hospedadas, en este caso, mi página de cuadrícula.

 La ruta de acceso del registro de la propiedad Automation se determina mediante la combinación de <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , la palabra, AutomationProperties y la categoría y el nombre de la página de opciones. Por ejemplo, si la Página opciones tiene la categoría mi categoría, el nombre de la página mi cuadrícula y el <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la propiedad Automation tiene la clave del registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> La página de la cuadrícula nombre canónico, mi Category.My, es el valor de la subclave Name de esta clave.
