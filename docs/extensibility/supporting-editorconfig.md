---
title: Extender el servicio de lenguaje para admitir EditorConfig
description: Obtenga información sobre los cambios que debe realizar para actualizar un servicio de lenguaje para admitir archivos EditorConfig. Reemplace una opción global específica del lenguaje con una opción contextual.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c635df2301822fc1bb982df44912527d53c9ef6
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716112"
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

## <a name="see-also"></a>Consulte también

- [Crear una configuración de editor portable mediante EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)
