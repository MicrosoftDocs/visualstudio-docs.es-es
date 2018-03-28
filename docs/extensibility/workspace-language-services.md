---
title: Áreas de trabajo y servicios de lenguaje en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 59cf2936311bb94c2db1ada6a7a3d5ccf994f027
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces-and-language-services"></a>Áreas de trabajo y servicios de lenguaje

Pueden proporcionar servicios de lenguaje [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) a los usuarios las mismas características de lenguaje enriquecido se utilizan para cuando se trabaja con soluciones y proyectos. Un servicio de lenguaje podría activarse automáticamente según la extensión de archivo o el contenido de un documento abierto, aunque este servicio de lenguaje de "archivo no estricta" se limita a resaltado de sintaxis. Se requiere información adicional para proporcionar una experiencia más enriquecida cuando edición/revisión de código fuente. Cada servicio de lenguaje tiene su propia API para la inicialización con estos datos extra contextuales para un documento. Normalmente esto se administra mediante un sistema de proyectos, que está asociado estrechamente con el servicio de lenguaje y para el sistema de compilación.

## <a name="initialization"></a>Inicialización

En un [área de trabajo](workspaces.md), servicios de lenguaje se inicializan mediante un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> los puntos de extensión que se especializa solo en ese servicio de lenguaje y no sabe nada de la creación de la compilación. De este modo, un propietario del servicio de lenguaje puede mantener una sola carpeta abierta extensión independientemente de cuántos patrones existe dentro de las carpetas y archivos para ejecutar su compilador durante una compilación (por ejemplo MSBuild, MAKE (archivos), etcetera). Cuando se cambian los archivos desde el que se creó un contexto de archivo en disco y se actualiza el contexto de archivo, el proveedor de servicios de lenguaje se notifica el conjunto de contextos de archivo actualizado. El proveedor de servicios de lenguaje, a continuación, puede actualizar su modelo.

Cuando se abre un documento en el editor, Visual Studio sólo considera lenguaje proveedores de servicios que requieren tipos de contexto de archivo para el que se puede encontrar un proveedor de contexto de archivo coincidente. A continuación, pasa los contextos de archivo desde el proveedor o proveedores de búsqueda de coincidencias para el proveedor de servicios de idioma seleccionado a través de `ILangaugeServiceProvider.InitializeAsync`. Lo que hace el proveedor de servicios de lenguaje con que los datos de contexto de archivo están un detalle de implementación del proveedor de servicios de lenguaje, pero la experiencia del usuario esperado es un servicio de lenguaje más enriquecido para abre el documento.

## <a name="using-ilanguageserviceprovider"></a>Using ILanguageServiceProvider

El servicio de lenguaje se notificará cuando se crea un contexto de archivo con un `ContextType` que coincide con uno de los `SupportedContextTypes` valores del servidor idioma exportación (atributo).

Para admitir un servicio de lenguaje, necesitará una extensión:

- Un único `Guid`. Esto se usará para `SupportedContextTypes` argumentos de atributo y en un `FileContext` objeto.
- Contexto del archivo de lenguaje
  - Generador del proveedor
    - `ExportFileContextProviderAttribute` atributo con los pasos anteriores generado de forma única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementación del proveedor de `IFileContextProvider.GetContextsForFileAsync`
    - Crear un nuevo `FileContext` con el `contextType` argumentos de constructor como el generado de forma única `Guid`
    - Use la `Context` propiedad de la `FileContext` para proporcionar datos adicionales a la `ILanguageServiceProvider`
- Servicio de lenguaje
  - Generador del proveedor
    - `ExportLanguageServiceProvider` atributo con los pasos anteriores generado de forma única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Proveedor
    - Implementa `ILanguageServiceProvider`
    - Use `ILanguageServiceProvider.InitializeAsync` para habilitar los servicios de lenguaje para los argumentos proporcionados cuando se abre un archivo
    - Use `ILanguageServiceProvider.UninitializeAsync` para deshabilitar servicios de lenguaje para los argumentos proporcionados cuando se cierra un archivo

>[!WARNING]
>El `ILanguageServiceProvider` el área de trabajo en el subproceso principal pueden invocar métodos. Considere la posibilidad de programar trabajo en un subproceso distinto a evitar la introducción de retrasos de la interfaz de usuario.

## <a name="language-server-protocol"></a>Protocolo de servidor de idioma

El `Microsoft.VisualStudio.Workspace.*` API no están la única forma de habilitar el servicio de lenguaje en la carpeta abierta. Otra opción es usar un servidor de idioma. Para obtener más información, lea acerca de la [protocolo del servidor idioma](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> se invoca cuando un archivo de coincidencia de tipos de archivo está abierto o cerrado para su edición.

## <a name="next-steps"></a>Pasos siguientes

* [Compilación de área de trabajo](workspace-build.md) -Abrir carpeta admite crear sistemas como MSBuild y MAKE (archivos). 