---
title: Novedades de Visual Studio 2019 SDK | Microsoft Docs
description: Visual Studio SDK las características nuevas y actualizadas de Visual Studio 2019, incluidas las mejoras de registro del editor.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05e6fccf3b45c8ab6fa1386c848d6ee33094e2d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877616"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novedades del SDK de Visual Studio 2019

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>ADVERTENCIA de extensiones autocargadas de forma sincrónica

Ahora los usuarios verán una advertencia si alguna de las extensiones instaladas se cargan de forma sincrónica en el inicio. Puede obtener más información sobre la advertencia en [extensiones cargadas](synchronously-autoloaded-extensions.md)automáticamente de forma sincrónica.

## <a name="single-unified-visual-studio-sdk"></a>SDK de Visual Studio unificado y único

Ahora puede obtener todos los recursos del SDK de Visual Studio a través de un único paquete NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Mejoras en el registro del editor

Desde su creación, Visual Studio ha admitido el registro del editor personalizado en el que un editor puede declarar su afinidad para extensiones específicas (por ejemplo,. XAML y. RC), o bien que es adecuado para cualquier extensión (. *). A partir de la versión 16,1 de Visual Studio 2019, ampliamos la compatibilidad con el registro del editor.

### <a name="filenames"></a>Nombres de archivo

Además de, o en lugar de, registrar la compatibilidad con una extensión de archivo determinada, un editor puede registrar que admite nombres de archivo específicos aplicando el nuevo `ProvideEditorFilename` atributo al paquete del editor.

Por ejemplo, un editor que admita todos los archivos. JSON aplicaría este `ProvideEditorExtension` atributo a su paquete:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partir de 16,1, si el administrador de cambios solo admite un par de archivos. JSON conocidos, en su lugar puede aplicar estos `ProvideEditorFilename` atributos a su paquete:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un editor puede registrar uno o más UIContexts que representan cuando está habilitado. UIContexts se registran aplicando una o más instancias de `ProvideEditorUIContextAttribute` al paquete que registra el editor.

Si un editor ha registrado UIContexts:

- Si al menos uno de sus UIContexts registrados está activo cuando se abre un archivo con la extensión especificada, el editor se incluye en la búsqueda del editor.
- Si ninguno de los UIContexts registrados está activo, el editor no se incluye en la búsqueda del editor.

Si un editor no registra ningún UIContexts, siempre se incluye en la búsqueda del editor de esa extensión.

Por ejemplo, si un editor solo está disponible cuando se abre un proyecto de C#, puede declarar esta afinidad aplicando un `ProvideEditorUIContext` atributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
