---
title: Novedades del SDK de Visual Studio 2019 Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740399"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novedades del SDK de Visual Studio 2019

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Advertencia de extensiones cargadas automáticamente sincrónicamente

Los usuarios ahora verán una advertencia si alguna de sus extensiones instaladas se carga automáticamente al iniciarse. Puede obtener más información sobre la advertencia en [Extensiones cargadas automáticamente sincrónicamente.](synchronously-autoloaded-extensions.md)

## <a name="single-unified-visual-studio-sdk"></a>SDK único y unificado de Visual Studio

Ahora puede obtener todos los activos del SDK de Visual Studio a través de un único paquete NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Mejoras en el registro del editor

Desde su creación, Visual Studio ha admitido el registro de editor personalizado donde un editor puede declarar su afinidad por extensiones específicas (por ejemplo, .xaml y .rc), o que es adecuado para cualquier extensión (.*). A partir de Visual Studio 2019 versión 16.1, ampliamos la compatibilidad con el registro del editor.

### <a name="filenames"></a>Nombres de archivo

Además de, o en lugar de, registrar la compatibilidad con una extensión de archivo `ProvideEditorFilename` determinada, un editor puede registrar que admite nombres de archivo específicos aplicando el nuevo atributo al paquete del editor.

Por ejemplo, un editor que admita `ProvideEditorExtension` todos los archivos .json aplicaría este atributo a su paquete:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partir de 16.1, si MyEditor solo admite un par de `ProvideEditorFilename` archivos .json conocidos, en su lugar puede aplicar estos atributos a su paquete:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un editor puede registrar uno o varios UIContexts que representan cuando está habilitado. UIContexts se registran aplicando una o `ProvideEditorUIContextAttribute` varias instancias del paquete que registra el editor.

Si un editor ha registrado UIContexts:

- Si al menos uno de sus UIContexts registrados está activo cuando se abre un archivo con la extensión dada, el editor se incluye en la búsqueda del editor.
- Si ninguno de los UIContexts registrados está activo, el editor no se incluye en la búsqueda del editor.

Si un editor no registra ningún UIContexts, siempre se incluye en la búsqueda del editor para esa extensión.

Por ejemplo, si un editor solo está disponible cuando un proyecto de C- está abierto, puede declarar esta afinidad aplicando un `ProvideEditorUIContext` atributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
