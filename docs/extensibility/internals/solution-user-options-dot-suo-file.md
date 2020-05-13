---
title: Opciones de usuario de la solución (. Archivo de Suo) Microsoft Docs
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
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705314"
---
# <a name="solution-user-options-suo-file"></a>Archivo de opciones de usuario de la solución (.Suo)
El archivo de opciones de usuario de la solución (.suo) contiene opciones de solución por usuario. Este archivo no se debe proteger en el control de código fuente.

 El archivo de opciones de usuario de la solución (.suo) es un archivo de almacenamiento estructurado o compuesto almacenado en formato binario. Guardar información de usuario en secuencias con el nombre de la secuencia es la clave que se usará para identificar la información en el archivo .suo. El archivo de opciones de usuario de la solución se usa para almacenar la configuración de preferencias del usuario y se crea automáticamente cuando Visual Studio guarda una solución.

 Cuando el entorno abre un archivo .suo, enumera todos los VSPackages cargados actualmente. Si un VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> implementa la interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> el entorno llama al método en el VSPackage pidiéndole que cargue todos sus datos desde el archivo .suo.

 Es responsabilidad del VSPackage saber qué secuencias podría haber escrito en el archivo .suo. Para cada secuencia que escribió, el VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> llama al entorno a través de para cargar una secuencia determinada que se identifica mediante la clave, que es el nombre de la secuencia. A continuación, el entorno vuelve a llamar al VSPackage para `IStream` leer esa secuencia concreta pasando el nombre de la secuencia y un puntero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método.

 En ese momento, se `LoadUserOptions` realiza otra llamada para ver si hay otra sección del archivo .suo que se debe leer. Este proceso continúa hasta que el entorno ha leído y procesado todas las secuencias de datos del archivo .suo.

 Cuando se guarda o cierra la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> solución, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> entorno llama al método con un puntero al método. Un `IStream` que contiene la información binaria <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> que se va a guardar se pasa al `SaveUserOptions` método, que luego escribe la información en el archivo .suo y llama al método de nuevo para ver si hay otra secuencia de información para escribir en el archivo .suo.

 Estos dos `SaveUserOptions` métodos, y `WriteUserOptions`, se llaman recursivamente para cada secuencia de información que `IVsSolutionPersistence`se va a guardar en el archivo .suo, pasando el puntero a . Se llaman recursivamente para permitir la escritura de varias secuencias en el archivo .suo. De este modo, la información del usuario se conserva con la solución y se garantiza que estará allí la próxima vez que se abra la solución.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Soluciones](../../extensibility/internals/solutions-overview.md)
