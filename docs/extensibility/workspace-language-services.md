---
title: Áreas de trabajo y servicios de lenguaje en Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo los servicios de lenguaje pueden proporcionar a los usuarios de la carpeta abierta las mismas características de lenguaje enriquecidas que se usan al trabajar con soluciones y proyectos.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 815cfb9e17fed38b519719010acd997f7fdc5242
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877044"
---
# <a name="workspaces-and-language-services"></a>Áreas de trabajo y servicios de lenguaje

Los servicios de lenguaje pueden proporcionar a los usuarios de la [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) las mismas características de lenguaje enriquecidas que se usan al trabajar con soluciones y proyectos. Un servicio de lenguaje se puede activar automáticamente en función de la extensión de archivo o el contenido de un documento abierto, aunque este servicio de lenguaje "archivo dinámico" se limita al resaltado de sintaxis. Se necesita información adicional para proporcionar una experiencia más completa al editar o revisar el código fuente. Cada servicio de lenguaje tiene su propia API para la inicialización con estos datos contextuales adicionales para un documento. Normalmente, se administra mediante un sistema de proyectos, que está estrechamente acoplado al servicio de lenguaje y al sistema de compilación.

## <a name="initialization"></a>Inicialización

En un [área de trabajo](workspaces.md), los servicios de lenguaje se inicializan mediante un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punto de extensión que se especializa solo en ese servicio de lenguaje y no sabe nada de la creación de la compilación. De esta manera, un propietario del servicio de lenguaje puede mantener una única extensión de carpeta abierta independientemente del número de patrones existentes en las carpetas y los archivos para ejecutar el compilador durante una compilación (por ejemplo, MSBuild, archivos make, etc.). Cuando se cambian los archivos de los que se creó un contexto de archivo en el disco y se actualiza el contexto del archivo, se notifica al proveedor de servicios de lenguaje el conjunto actualizado de contextos de archivo. Después, el proveedor de servicios de lenguaje puede actualizar su modelo.

Cuando se abre un documento en el editor, Visual Studio solo considera los proveedores de servicios de lenguaje que requieren tipos de contexto de archivo para los que se puede encontrar un proveedor de contexto de archivo coincidente. A continuación, pasa los contextos de archivo de los proveedores coincidentes al proveedor de servicios de lenguaje seleccionado a través de `ILanguageServiceProvider.InitializeAsync` . Lo que hace el proveedor de servicios de lenguaje con los datos de contexto de archivo es un detalle de implementación del proveedor de servicios de lenguaje, pero la experiencia del usuario esperada es un servicio de lenguaje más completo para ese documento abierto.

## <a name="using-ilanguageserviceprovider"></a>Usar ILanguageServiceProvider

El servicio de lenguaje recibirá una notificación cuando se cree un contexto de archivo con un `ContextType` que coincida con uno de los `SupportedContextTypes` valores del atributo de exportación del servidor de idioma.

Para admitir un servicio de lenguaje, se necesitará una extensión:

- Un único `Guid` . Se utilizará para los `SupportedContextTypes` argumentos de atributo y en un `FileContext` objeto.
- Contexto de archivo de lenguaje
  - Generador de proveedores
    - `ExportFileContextProviderAttribute` atributo con el anterior generado de forma única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementación del proveedor de `IFileContextProvider.GetContextsForFileAsync`
    - Construya un nuevo `FileContext` con el `contextType` argumento del constructor como el único generado `Guid`
    - Utilice la `Context` propiedad de `FileContext` para proporcionar datos adicionales al `ILanguageServiceProvider`
- Servicio de lenguaje
  - Generador de proveedores
    - `ExportLanguageServiceProvider` atributo con el anterior generado de forma única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Proveedor
    - Implementa `ILanguageServiceProvider`
    - Use `ILanguageServiceProvider.InitializeAsync` para habilitar los servicios de lenguaje para los argumentos proporcionados al abrir un archivo.
    - Usar `ILanguageServiceProvider.UninitializeAsync` para deshabilitar los servicios de lenguaje para los argumentos proporcionados cuando se cierra un archivo

>[!WARNING]
>El `ILanguageServiceProvider` área de trabajo puede invocar los métodos en el subproceso principal. Considere la posibilidad de programar trabajo en un subproceso diferente para evitar la introducción de retrasos en la interfaz de usuario.

## <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

Las `Microsoft.VisualStudio.Workspace.*` API no son la única forma de habilitar el servicio de lenguaje en Open folder. Otra opción es usar un servidor de idioma. Para obtener más información, consulte el [Protocolo del servidor de lenguaje](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> se invoca cuando se abre o se cierra un archivo de tipos de archivo coincidentes para su edición.

## <a name="next-steps"></a>Pasos siguientes

* [Compilación de área de trabajo](workspace-build.md) : la carpeta Open admite sistemas de compilación como MSBuild y archivos make.