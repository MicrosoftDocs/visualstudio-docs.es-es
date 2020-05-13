---
title: Amplíe el servicio de lenguaje para admitir EditorConfig
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
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699581"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Compatibilidad con EditorConfig para su servicio de lenguaje

Los archivos [EditorConfig](https://editorconfig.org/) le permiten describir opciones comunes del editor de texto, como el tamaño de sangría, por proyecto. Para obtener más información sobre la compatibilidad de Visual Studio con los archivos EditorConfig, vea Crear configuración de [editor portátil mediante EditorConfig](../ide/create-portable-custom-editor-options.md).

En la mayoría de los casos, cuando se implementa un servicio de lenguaje de Visual Studio, no es necesario llevar a cabo ninguna tarea adicional para admitir las propiedades universales de EditorConfig. El editor principal detecta automáticamente y lee el archivo .editorconfig cuando los usuarios abren archivos, y establece el búfer de texto y las opciones de visualización adecuados. Sin embargo, para ediciones como pestañas y espacios, algunos servicios de idioma optan por usar una opción de vista de texto contextual adecuada en lugar de usar la configuración global. En estos casos, el servicio de lenguaje debe actualizarse para que admita archivos EditorConfig.

A continuación se muestran los cambios necesarios para actualizar un servicio de lenguaje para admitir archivos EditorConfig, reemplazando una opción _global específica del idioma_ por una opción _contextual:_

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

- [Crear ajustes de editor portátiles con EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Ampliación del editor y los servicios de idiomas](../extensibility/extending-the-editor-and-language-services.md)
