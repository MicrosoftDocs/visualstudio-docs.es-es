---
title: Extender el servicio de lenguaje para admitir EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 663a87ba15121896edcb4c049e7adc6b5c38492a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983099"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Compatibilidad con EditorConfig para el servicio de lenguaje

Los archivos [EditorConfig](https://editorconfig.org/) permiten describir opciones comunes del editor de texto, como el tamaño de la sangría, en cada proyecto. Para obtener más información sobre la compatibilidad de Visual Studio con los archivos EditorConfig, vea [crear una configuración de editor portátil con EditorConfig](../ide/create-portable-custom-editor-options.md).

En la mayoría de los casos, cuando se implementa un servicio de lenguaje de Visual Studio, no es necesario llevar a cabo ninguna tarea adicional para admitir las propiedades universales de EditorConfig. El editor principal detecta automáticamente y lee el archivo .editorconfig cuando los usuarios abren archivos, y establece el búfer de texto y las opciones de visualización adecuados. Sin embargo, en el caso de las ediciones, como tabulaciones y espacios, algunos servicios de lenguaje optan por usar una opción de vista de texto contextual adecuada en lugar de usar la configuración global. En estos casos, el servicio de lenguaje debe actualizarse para que admita archivos EditorConfig.

A continuación se indican los cambios necesarios para actualizar un servicio de lenguaje para admitir archivos EditorConfig, reemplazando una opción global _específica del lenguaje_ con una opción _contextual_ :

## <a name="indent-style"></a>Estilo de sangría

Opciones específicas del lenguaje | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Tamaño de sangría

Opciones específicas del lenguaje | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tamaño de tabulación

Opciones específicas del lenguaje | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Vea también

- [Crear una configuración de editor portable mediante EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)