---
title: Extender un servicio de lenguaje para admitir EditorConfig en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2aa80903b3e5ea2723ec576fa463161b8d003c93
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Compatibilidad con EditorConfig para el servicio de lenguaje

[EditorConfig](http://editorconfig.org/) archivos permiten describir opciones comunes de editor de texto, como el tamaño de sangría, en forma de cada proyecto. Para más información sobre la compatibilidad con Visual Studio EditorConfig archivos, consulte [crear una configuración de editor portátil mediante EditorConfig](../ide/create-portable-custom-editor-options.md).

En la mayoría de los casos, cuando se implementa un servicio de lenguaje de Visual Studio, no es necesario llevar a cabo ninguna tarea adicional para admitir las propiedades universales de EditorConfig. El editor principal detecta automáticamente y lee el archivo .editorconfig cuando los usuarios abren archivos, y establece el búfer de texto y las opciones de visualización adecuados. Sin embargo, edición, como tabulaciones y espacios, algunos servicios de lenguaje optar por usar una opción de vista de texto contextual adecuado en lugar de usar la configuración global. En estos casos, el servicio de lenguaje debe actualizarse para que admita archivos EditorConfig.

Siguientes son los cambios que son necesarios para actualizar un servicio de lenguaje para admitir archivos EditorConfig, reemplazando global _específica del lenguaje_ opción con un _contextual_ opción:

## <a name="indent-style"></a>Estilo de sangría

Opciones específicas del idioma | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Tamaño de sangría

Opciones específicas del idioma | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tamaño de tabulación

Opciones específicas del idioma | Opciones contextuales
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Vea también

[Crear una configuración de editor portátil mediante EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Ampliar los servicios de editor y el idioma](../extensibility/extending-the-editor-and-language-services.md)