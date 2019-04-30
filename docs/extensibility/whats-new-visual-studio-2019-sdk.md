---
title: Novedades en el SDK de Visual Studio 2019 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30ab0004a492316ff9cbe11016e24b1a28dadf16
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444894"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novedades del SDK de Visual Studio 2019

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio de 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Sincrónicamente autocargado extensiones de advertencia

Los usuarios verán ahora una advertencia si alguno de sus extensiones instaladas sincrónicamente autocargado durante el inicio. Puede aprender más sobre la advertencia [sincrónicamente autocargado extensiones](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Única y unificada SDK de Visual Studio

Ahora puede obtener todos los recursos del SDK de Visual Studio a través de un único paquete NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Mejoras en el registro del Editor

Desde su creación, Visual Studio admite el registro del editor personalizado donde un editor puede declarar su afinidad para extensiones específicas (por ejemplo, .xaml y .rc), o que es adecuado para cualquier extensión (. *). A partir de Visual Studio 2019 versión 16.1, se puede ampliar la compatibilidad para el registro del editor.

### <a name="filenames"></a>Nombres de archivo

Además, o bien, en lugar de, registrar la compatibilidad para una extensión de archivo determinado, un editor puede registrar que admite nombres de archivo específico mediante la aplicación de la nueva `ProvideEditorFilename` al paquete del editor de atributos.

Por ejemplo, un editor que admite todos los archivos .json se aplicaría esta `ProvideEditorExtension` a su paquete de atributo:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partir 16.1, si MyEditor solo admite un par de archivos .json conocido, lo puede en su lugar aplicarlas `ProvideEditorFilename` atributos a su paquete:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un editor puede registrar uno o varios UIContexts que representan cuando está habilitada. Se registran UIContexts aplicando una o varias instancias de `ProvideEditorUIContextAttribute` al paquete que se registra en el editor.

Si un editor tiene UIContexts registrados:

- Si al menos uno de sus UIContexts registrado está activo cuando se abre un archivo con la extensión especificada, el editor se incluye en la búsqueda del editor.
- Si ninguno de los UIContexts registrado está activo, el editor no está incluido en la búsqueda del editor.

Si un editor no registra ningún UIContexts, siempre se incluye en la búsqueda del editor de esa extensión.

Por ejemplo, si un editor solo está disponible cuando un C# proyecto está abierto, puede declarar esta afinidad aplicando un `ProvideEditorUIContext` atributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
