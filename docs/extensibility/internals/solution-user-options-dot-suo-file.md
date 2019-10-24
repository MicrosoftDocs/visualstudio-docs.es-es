---
title: Opciones de usuario de la solución (. Suo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723814"
---
# <a name="solution-user-options-suo-file"></a>Archivo de opciones de usuario de la solución (.Suo)
El archivo de opciones de usuario de la solución (. suo) contiene opciones de solución por usuario. Este archivo no se debe proteger en el control de código fuente.

 El archivo de opciones de usuario de la solución (. suo) es un archivo de almacenamiento estructurado, o compuesto, almacenado en un formato binario. La información del usuario se guarda en secuencias con el nombre de la secuencia como la clave que se utilizará para identificar la información en el archivo. suo. El archivo de opciones de usuario de la solución se usa para almacenar la configuración de preferencias del usuario y se crea automáticamente cuando Visual Studio guarda una solución.

 Cuando el entorno abre un archivo. suo, enumera todos los VSPackages cargados actualmente. Si un VSPackage implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, el entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> en el VSPackage pidiéndole que cargue todos sus datos del archivo. suo.

 Es responsabilidad del VSPackage saber qué secuencias podría haber escrito en el archivo. suo. Para cada flujo que escribió, el VSPackage vuelve a llamar al entorno a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> para cargar un flujo concreto que se identifica mediante la clave, que es el nombre de la secuencia. Después, el entorno llama de nuevo al VSPackage para leer ese flujo concreto pasando el nombre de la secuencia y un puntero `IStream` al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 En ese momento, se realiza otra llamada a `LoadUserOptions` para ver si hay otra sección del archivo. suo que tenga que leerse. Este proceso continúa hasta que el entorno Lee y procesa todos los flujos de datos en el archivo. suo.

 Cuando la solución se guarda o se cierra, el entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> con un puntero al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. Una `IStream` que contiene la información binaria que se va a guardar se pasa al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, que, a continuación, escribe la información en el archivo. suo y llama de nuevo al método `SaveUserOptions` para ver si hay otra secuencia de información que escribir en el archivo. suo.

 Estos dos métodos, `SaveUserOptions` y `WriteUserOptions`, se llaman de forma recursiva para cada flujo de información que se va a guardar en el archivo. suo, pasando el puntero a `IVsSolutionPersistence`. Se llaman de forma recursiva para permitir la escritura de varias secuencias en el archivo. suo. De este modo, la información de usuario se conserva con la solución y se garantiza que estará ahí la próxima vez que se abra la solución.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluciones](../../extensibility/internals/solutions-overview.md)