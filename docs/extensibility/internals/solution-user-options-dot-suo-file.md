---
title: Opciones de usuario de la solución (. Archivo suo) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bd77c125f6ac7b7efa8d0979658c7933dc1b9ec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937001"
---
# <a name="solution-user-options-suo-file"></a>Archivo de opciones de usuario de la solución (.Suo)
El archivo de opciones (.suo) del usuario de solución contiene opciones de la solución por usuario. Este archivo no debe comprobarse para el control de código fuente.  
  
 El archivo de opciones (.suo) del usuario de solución es un almacenamiento estructurado o compuesto, el archivo almacenado en un formato binario. Guardar información de usuario en secuencias con el nombre de la secuencia que se va a la clave que se usará para identificar la información en el archivo .suo. El archivo de opciones de usuario de solución se usa para almacenar la configuración de preferencias de usuario y se crea automáticamente cuando Visual Studio guarda una solución.  
  
 Cuando el entorno abre un archivo .suo, enumera todos los VSPackages cargados actualmente. Si implementa un paquete VSPackage el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz y, después, en el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> método en el VSPackage que se le pide que cargar todos los datos desde el archivo .suo.  
  
 Es responsabilidad de VSPackage saber lo que transmite por secuencias se hayan podido escribir en el archivo .suo. Para cada secuencia que escribió, VSPackage vuelve al entorno a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> para cargar una secuencia concreta que se identifica mediante la clave, que es el nombre de la secuencia. El entorno, a continuación, devuelva la llamada a VSPackage para leer ese flujo concreto pasando el nombre de la secuencia y un `IStream` puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> método.  
  
 En ese momento, se realiza otra llamada a `LoadUserOptions` para ver si hay otra sección del archivo .suo que tiene que leerse. Este proceso continúa hasta que todas las secuencias de datos en el archivo .suo han leído y procesados por el entorno.  
  
 Cuando la solución se guarda o cierra el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> método. Un `IStream` que contiene la información binaria que se guarde se pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> método, que, a continuación, escribe la información en el archivo .suo y llama el `SaveUserOptions` nuevamente para ver si hay otro flujo de información que se va a escribir en el .suo (método) archivo.  
  
 Estos dos métodos, `SaveUserOptions` y `WriteUserOptions`, se llama de forma recursiva para cada flujo de información se guarde en el archivo .suo, pase el puntero a `IVsSolutionPersistence`. Se denominan de forma recursiva para permitir la escritura de los que el archivo .suo varias secuencias. De esa manera, información de usuario se mantiene con la solución y se garantiza que existe la próxima vez que se abra la solución.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluciones](../../extensibility/internals/solutions.md)