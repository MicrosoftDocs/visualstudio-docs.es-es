---
title: Áreas de trabajo y servicios de lenguaje en Visual Studio | Documentos de Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929783"
---
# <a name="workspaces-and-language-services"></a>Áreas de trabajo y servicios de lenguaje

Pueden proporcionar servicios de lenguaje [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) a los usuarios las mismas características de lenguaje enriquecido se utilizan para cuando se trabaja con soluciones y proyectos. Un servicio de lenguaje podría activarse automáticamente según la extensión de archivo o el contenido de un documento abierto, aunque este servicio de lenguaje "archivo dinámico" se limita a resaltado de sintaxis. Se necesita información adicional para proporcionar una experiencia más enriquecida cuando Editar y revisar el código fuente. Cada servicio de lenguaje tiene su propia API para la inicialización con estos datos extra contextuales para un documento. Normalmente, esto se administra mediante un sistema de proyectos, que está estrechamente asociado para el servicio de lenguaje y para el sistema de compilación.

## <a name="initialization"></a>Inicialización

En un [área de trabajo](workspaces.md), servicios de lenguaje se inicializan mediante un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punto de extensión que se especializa solo en ese servicio de lenguaje y no sabe nada de la creación de la compilación. De este modo, un propietario del servicio de lenguaje puede mantener una sola carpeta abierta extensión independientemente de cuántas patrones existe dentro de carpetas y archivos para ejecutar su compilador durante la compilación (por ejemplo MSBuild, archivos MAKE, etcetera.). Cuando se cambian los archivos desde el que se creó un contexto de archivo en disco y se actualiza el contexto del archivo, el proveedor de servicio de lenguaje se notifica el conjunto actualizado de contextos de archivo. El proveedor de servicio de lenguaje, a continuación, puede actualizar su modelo.

Cuando se abre un documento en el editor, Visual Studio sólo considera lenguaje proveedores de servicios que requieren tipos de contexto de archivo para que se puede encontrar un proveedor de contexto de archivo coincidente. A continuación, pasa los contextos de archivo de los proveedores de búsqueda de coincidencias para el proveedor de servicios de idioma seleccionado a través de `ILanguageServiceProvider.InitializeAsync`. Lo que hace el proveedor de servicio de lenguaje con que los datos de contexto de archivo están un detalle de implementación del proveedor del servicio de lenguaje, pero la experiencia de usuario esperado es un servicio de lenguaje enriquecido para el abre el documento.

## <a name="using-ilanguageserviceprovider"></a>Uso de ILanguageServiceProvider

El servicio de lenguaje se notificará cuando se crea un contexto de archivo con un `ContextType` que coincide con uno de los `SupportedContextTypes` valores del servidor idioma de exportación el atributo.

Para admitir un servicio de lenguaje, tendrá una extensión:

- Un único `Guid`. Esto se utilizará para `SupportedContextTypes` argumentos de atributo y en un `FileContext` objeto.
- Contexto del archivo de lenguaje
  - Generador del proveedor
    - `ExportFileContextProviderAttribute` atributo con el anterior se genera de manera única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementación de proveedor `IFileContextProvider.GetContextsForFileAsync`
    - Crear un nuevo `FileContext` con el `contextType` argumento de constructor como el generado de forma única `Guid`
    - Use la `Context` propiedad de la `FileContext` para proporcionar datos adicionales a la `ILanguageServiceProvider`
- servicio de lenguaje
  - Generador del proveedor
    - `ExportLanguageServiceProvider` atributo con el anterior se genera de manera única `Guid` en `SupportedContextTypes`
    - Implementa `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Proveedor
    - Implementa `ILanguageServiceProvider`
    - Use `ILanguageServiceProvider.InitializeAsync` para habilitar los servicios de lenguaje para los argumentos proporcionados cuando se abre un archivo
    - Use `ILanguageServiceProvider.UninitializeAsync` para deshabilitar los servicios de lenguaje para los argumentos proporcionados cuando se cierra un archivo

>[!WARNING]
>El `ILanguageServiceProvider` métodos podrían ser invocados por el área de trabajo en el subproceso principal. Considere la posibilidad de programar el trabajo en un subproceso distinto para evitar la introducción de retrasos de la interfaz de usuario.

## <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

El `Microsoft.VisualStudio.Workspace.*` API no son la única forma de habilitar el servicio de lenguaje en la carpeta abierta. Otra opción es usar un servidor de lenguaje. Para obtener más información, lea sobre la [protocolo del servidor idioma](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces relacionadas

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> se invoca cuando un archivo de coincidencia de tipos de archivo está abierto o cerrado para su edición.

## <a name="next-steps"></a>Pasos siguientes

* [Compilación de área de trabajo](workspace-build.md) -Abrir carpeta es compatible con sistemas como MSBuild y archivos MAKE de compilación.