---
title: Opciones de usuario de la solución (. Suo) File | Microsoft Docs
description: Obtenga información sobre el archivo de opciones de usuario de la solución (.suo), que contiene opciones de solución por usuario en un archivo de almacenamiento estructurado almacenado en formato binario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899620"
---
# <a name="solution-user-options-suo-file"></a>Archivo de opciones de usuario de la solución (.Suo)
El archivo de opciones de usuario de la solución (.suo) contiene opciones de solución por usuario. Este archivo no debe estar registrado en el control de código fuente.

 El archivo de opciones de usuario de la solución (.suo) es un archivo de almacenamiento estructurado o compuesto almacenado en formato binario. Guarde la información del usuario en secuencias con el nombre de la secuencia como clave que se usará para identificar la información en el archivo .suo. El archivo de opciones de usuario de la solución se usa para almacenar la configuración de preferencias del usuario y se crea automáticamente cuando Visual Studio guarda una solución.

 Cuando el entorno abre un archivo .suo, enumera todos los VSPackages cargados actualmente. Si un VSPackage implementa la interfaz , el entorno llama al método en el VSPackage pidiéndole que cargue todos sus datos desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> archivo .suo.

 Es responsabilidad del VSPackage saber qué secuencias podría haber escrito en el archivo .suo. Para cada secuencia que escribió, vsPackage vuelve a llamar al entorno a través de para cargar una secuencia determinada identificada por la clave, que es el nombre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> de la secuencia. A continuación, el entorno vuelve a llamar al VSPackage para leer esa secuencia determinada pasando el nombre de la secuencia y un `IStream` puntero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método .

 En ese momento, se realiza otra llamada a para ver si hay otra sección del `LoadUserOptions` archivo .suo que se tiene que leer. Este proceso continúa hasta que el entorno ha leído y procesado todos los flujos de datos del archivo .suo.

 Cuando se guarda o cierra la solución, el entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método con un puntero al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> . Una que contiene la información binaria que se va a guardar se pasa al método , que luego escribe la información en el archivo .suo y llama de nuevo al método para ver si hay otra secuencia de información para escribir en el `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> archivo `SaveUserOptions` .suo.

 Estos dos métodos, y , se llaman de forma recursiva para cada flujo de información que se va a guardar en el `SaveUserOptions` `WriteUserOptions` archivo .suo, pasando el puntero a `IVsSolutionPersistence` . Se llaman de forma recursiva para permitir la escritura de varias secuencias en el archivo .suo. De este modo, la información del usuario se conserva con la solución y se garantiza que estará allí la próxima vez que se abra la solución.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluciones](../../extensibility/internals/solutions-overview.md)
