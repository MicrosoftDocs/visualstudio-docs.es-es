---
title: "Opciones de usuario de la solución (. Archivo suo) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71f3e14c6a8c87290de2a6204fa28f99a8cabe8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="solution-user-options-suo-file"></a>Opciones de usuario de la solución (. Archivo suo)
El archivo de opciones (.suo) de usuario de solución contiene opciones de la solución por usuario. Este archivo no debe comprobarse para control de código fuente.  
  
 El archivo de opciones (.suo) de usuario de solución es un almacenamiento estructurado o compuesta, el archivo almacenado en un formato binario. Guardar información de usuario en secuencias con el nombre de la secuencia que se va a la clave que se usará para identificar la información en el archivo .suo. El archivo de opciones de usuario de solución se usa para almacenar la configuración de preferencias de usuario y se crea automáticamente cuando Visual Studio guarda una solución.  
  
 Cuando el entorno abre un archivo .suo, enumera todos los VSPackages cargados actualmente. Si implementa un paquete VSPackage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz y, a continuación, el entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> método en el VSPackage solicitando a cargar todos los datos desde el archivo .suo.  
  
 Es responsabilidad del VSPackage saber lo que se transmita por secuencias se hayan podido escribir en el archivo .suo. Para cada flujo que escribió, el VSPackage llama de nuevo en el entorno a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> para cargar una secuencia concreta identificada por la clave, que es el nombre de la secuencia. El entorno, a continuación, vuelve a llamar a VSPackage para leer esa secuencia concreta pasando el nombre de la secuencia y un `IStream` puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método.  
  
 En ese momento, se realiza otra llamada a `LoadUserOptions` para ver si hay otra sección del archivo .suo que debe leerse. Este proceso continúa hasta que todas las secuencias de datos en el archivo .suo han leído y procesados por el entorno.  
  
 Cuando la solución está guardada o cerrada, el entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> método. Un `IStream` que contiene la información binaria que se guarde se pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> método, que, a continuación, escribe la información en el archivo .suo y llama el `SaveUserOptions` método nuevo para ver si hay otro flujo de información que se va a escribir en el .suo archivo.  
  
 Estos dos métodos, `SaveUserOptions` y `WriteUserOptions`, se llama de forma recursiva para cada flujo de información que se guardará en el archivo .suo, pasando el puntero a `IVsSolutionPersistence`. Se les llama para permitir la escritura de varias secuencias en el archivo .suo de forma recursiva. De esa manera, información del usuario se mantiene con la solución y se garantiza que no existe la próxima vez que se abre la solución.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluciones](../../extensibility/internals/solutions.md)