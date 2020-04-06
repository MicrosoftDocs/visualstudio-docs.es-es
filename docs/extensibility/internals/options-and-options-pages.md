---
title: Páginas de Opciones y Opciones (Opciones y Opciones) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706834"
---
# <a name="options-and-options-pages"></a>Opciones y páginas de opciones
Al hacer clic en **Opciones** en el menú **Herramientas,** se abre el cuadro de diálogo **Opciones.** Las opciones de este cuadro de diálogo se conocen colectivamente como páginas de opciones. El control de árbol del panel de navegación incluye categorías de opciones y cada categoría tiene páginas de opciones. Al seleccionar una página, sus opciones aparecen en el panel derecho. Estas páginas permiten cambiar los valores de las opciones que determinan el estado de un VSPackage.

## <a name="support-for-options-pages"></a>Soporte para páginas de opciones
 La <xref:Microsoft.VisualStudio.Shell.Package> clase proporciona compatibilidad para crear páginas de opciones y categorías de opciones. La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase implementa una página de opciones.

 La implementación <xref:Microsoft.VisualStudio.Shell.DialogPage> predeterminada de ofrece sus propiedades públicas a un usuario en una cuadrícula genérica de propiedades. Puede personalizar este comportamiento reemplazando varios métodos en la página para crear una página de opciones personalizadas que tenga su propia interfaz de usuario (UI). Para obtener más información, consulte [Creación de una página](../../extensibility/creating-an-options-page.md)de opciones .

 La <xref:Microsoft.VisualStudio.Shell.DialogPage> clase <xref:Microsoft.VisualStudio.Shell.IProfileManager>implementa , que proporciona persistencia para las páginas de opciones y también para la configuración de usuario. Las implementaciones predeterminadas de los <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> métodos y <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> conservan los cambios de propiedad en una sección de usuario del registro si la propiedad se puede convertir a y desde una cadena.

## <a name="options-page-registry-path"></a>Ruta del registro de la página de opciones
 De forma predeterminada, la ruta de acceso del Registro <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>de las propiedades administradas por una página de opciones se determina combinando , la palabra DialogPage y el nombre de tipo de la clase de página de opciones. Por ejemplo, una clase de página de opciones podría definirse de la siguiente manera.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Si <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> el es HKEY_CURRENT_USER, Software, Microsoft, VisualStudio, 8.0Exp, los pares de nombre de propiedad y valor son subclaves de HKEY_CURRENT_USER, Software, Microsoft, VisualStudio, 8.0Exp, DialogPage, Company.OptionsPage.OptionsPageGeneral.

 La ruta de acceso del Registro <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>de la propia página de opciones se determina combinando , la palabra, ToolsOptionsPages, y la categoría de página de opciones y el nombre. Por ejemplo, si la página Opciones personalizadas tiene <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> la categoría Mis páginas de opciones y está HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 8.0Exp, la página de opciones tiene la clave del Registro, HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 8.0Exp, ToolsOptionsPages, Mis páginas de opciones y Personalizada.

## <a name="toolsoptions-page-attributes-and-layout"></a>Atributos y diseño de página De herramientas/opciones
 El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo determina la agrupación de páginas de opciones personalizadas en categorías en el árbol de navegación del cuadro de diálogo **Opciones.** El <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> atributo asocia una página de opciones con el VSPackage que proporciona la interfaz. Observe el fragmento de código siguiente:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Esto declara que MyPackage proporciona dos páginas de opciones, OptionsPageGeneral y OptionsPageCustom. En el cuadro de diálogo **Opciones,** ambas páginas de opciones aparecen en la categoría **Mis páginas** de opciones como **General** y **Personalizado**, respectivamente.

## <a name="option-attributes-and-layout"></a>Atributos de opción y diseño
 La interfaz de usuario (UI) que proporciona la página determina la apariencia de las opciones en una página de opciones personalizadas. El diseño, el etiquetado y la descripción de las opciones de una página de opciones genéricas están determinados por los siguientes atributos:

- <xref:System.ComponentModel.CategoryAttribute>determina la categoría de la opción.

- <xref:System.ComponentModel.DisplayNameAttribute>determina el nombre para mostrar de la opción.

- <xref:System.ComponentModel.DescriptionAttribute>determina la descripción de la opción.

  > [!NOTE]
  > Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en el ejemplo de [proyecto administrado.](/azure/devops/integrate/index)

  Observe el fragmento de código siguiente:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  La opción OptionInteger aparece en la página de opciones como **Opción entero** en la categoría **Mis opciones.** Si la opción está seleccionada, la descripción, **Mi opción de entero**, aparece en el cuadro de descripción.

## <a name="accessing-options-pages-from-another-vspackage"></a>Acceso a las páginas de opciones desde otro VSPackage
 Un VSPackage que hospeda y administra una página de opciones se puede tener acceso mediante programación desde otro VSPackage mediante el modelo de automatización. Por ejemplo, en el código siguiente se registra un VSPackage como hospedaje de una página de opciones.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 El siguiente fragmento de código obtiene el valor de OptionInteger de MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Cuando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> el atributo registra una página de opciones, la página `SupportsAutomation` se registra `true`en la clave AutomationProperties si el argumento del atributo es . Automatización examina esta entrada del Registro para buscar el VSPackage asociado y, a continuación, la automatización tiene acceso a la propiedad a través de la página de opciones hospedadas, en este caso, Mi página de cuadrícula.

 La ruta de acceso del Registro <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>de la propiedad de automatización se determina combinando , la palabra, AutomationProperties y la categoría y el nombre de la página de opciones. Por ejemplo, si la página de opciones tiene la categoría <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>Mi categoría, el nombre de mi página de cuadrícula y , HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 8.0Exp, la propiedad de automatización tiene la clave del Registro, HKEY_LOCAL_MACHINE, software, Microsoft, VisualStudio, 8.0Exp, AutomationProperties, mi categoría, mi página de cuadrícula.

> [!NOTE]
> El nombre canónico, Mi Category.My página de cuadrícula, es el valor de la subclave Nombre de esta clave.
