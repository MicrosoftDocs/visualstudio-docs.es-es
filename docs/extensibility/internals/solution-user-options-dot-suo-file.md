---
title: Opciones de usuario de la solución (. Suo) | Microsoft Docs
description: Obtenga información sobre el archivo de opciones de usuario de la solución (. suo), que contiene opciones de solución por usuario en un archivo de almacenamiento estructurado almacenado en formato binario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b2a5386e8329bb3ca51ca88a2449e223bb8d73d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876759"
---
# <a name="solution-user-options-suo-file"></a>Archivo de opciones de usuario de la solución (.Suo)
El archivo de opciones de usuario de la solución (. suo) contiene opciones de solución por usuario. Este archivo no se debe proteger en el control de código fuente.

 El archivo de opciones de usuario de la solución (. suo) es un archivo de almacenamiento estructurado, o compuesto, almacenado en un formato binario. La información del usuario se guarda en secuencias con el nombre de la secuencia como la clave que se utilizará para identificar la información en el archivo. suo. El archivo de opciones de usuario de la solución se usa para almacenar la configuración de preferencias del usuario y se crea automáticamente cuando Visual Studio guarda una solución.

 Cuando el entorno abre un archivo. suo, enumera todos los VSPackages cargados actualmente. Si un VSPackage implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz, el entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> método en el VSPackage pidiéndole que cargue todos sus datos del archivo. suo.

 Es responsabilidad del VSPackage saber qué secuencias podría haber escrito en el archivo. suo. Para cada flujo que escribió, el VSPackage vuelve a llamar al entorno a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> de para cargar un flujo concreto que se identifica mediante la clave, que es el nombre de la secuencia. Después, el entorno llama de nuevo al VSPackage para leer ese flujo concreto pasando el nombre de la secuencia y un `IStream` puntero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método.

 En ese momento, se realiza otra llamada a `LoadUserOptions` para ver si hay otra sección del archivo. suo que debe leerse. Este proceso continúa hasta que el entorno Lee y procesa todos los flujos de datos en el archivo. suo.

 Cuando la solución se guarda o se cierra, el entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método con un puntero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> método. Un `IStream` que contiene la información binaria que se va a guardar se pasa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> método, que, a continuación, escribe la información en el archivo. suo y llama de `SaveUserOptions` nuevo al método para ver si hay otro flujo de información que escribir en el archivo. suo.

 Estos dos métodos, `SaveUserOptions` y `WriteUserOptions` , se llaman de forma recursiva para cada flujo de información que se va a guardar en el archivo. suo, pasando el puntero a `IVsSolutionPersistence` . Se llaman de forma recursiva para permitir la escritura de varias secuencias en el archivo. suo. De este modo, la información de usuario se conserva con la solución y se garantiza que estará ahí la próxima vez que se abra la solución.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluciones](../../extensibility/internals/solutions-overview.md)
