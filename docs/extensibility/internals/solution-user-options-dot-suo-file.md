---
title: "Opciones de usuario de soluci&#243;n (. Archivo suo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".suo (archivos), VSPackages"
  - "suo (archivos), VSPackages"
  - "soluciones, .suo (archivos)"
  - "soluciones, opciones de usuario"
  - "archivo de opciones (.suo) de usuario de solución"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Opciones de usuario de soluci&#243;n (. Archivo suo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El archivo de opciones \(.suo\) de usuario de solución contiene opciones de solución de cada usuario. Este archivo no debe comprobarse control de código fuente.  
  
 El archivo de opciones \(.suo\) de usuario de solución es un almacenamiento estructurado o compuesto, el archivo almacenado en un formato binario. Guarda la información de usuario en secuencias con el nombre de la secuencia que se va a la clave que se utilizará para identificar la información en el archivo .suo. El archivo de opciones de usuario de solución se usa para almacenar la configuración de preferencias de usuario y se crea automáticamente cuando Visual Studio guarda una solución.  
  
 Cuando el entorno abre un archivo .suo, enumera todos los VSPackages cargados actualmente. Si implementa un VSPackage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz y, a continuación, el entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> método VSPackage solicitando para cargar todos los datos desde el archivo .suo.  
  
 Es responsabilidad del VSPackage saber lo que transmite podría haber escrito en el archivo .suo. Para cada secuencia que escribió, VSPackage llama de nuevo en el entorno a través de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> para cargar una secuencia concreta identificada por la clave, que es el nombre de la secuencia. El entorno, a continuación, vuelve a llamar a VSPackage leer esa secuencia concreta pasando el nombre de la secuencia y un `IStream` puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> \(método\).  
  
 En ese momento, se realiza otra llamada a `LoadUserOptions` para ver si hay otra sección del archivo .suo que debe leerse. Este proceso continúa hasta que todas las secuencias de datos en el archivo .suo han leído y procesado por el entorno.  
  
 Cuando la solución se guarda o cierra el entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> método con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> \(método\). Un `IStream` que contiene la información binaria que se guarde se pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> método, que, a continuación, escribe la información en el archivo .suo y llama el `SaveUserOptions` método nuevo para ver si hay otro flujo de información se escribirá en el archivo .suo.  
  
 Estos dos métodos, `SaveUserOptions` y `WriteUserOptions`, se llama de forma recursiva para cada flujo de información se guarde en el archivo .suo, pasando el puntero a `IVsSolutionPersistence`. Se denominan de forma recursiva para permitir la escritura de varias secuencias en el archivo .suo. De esa manera, la información del usuario se mantiene con la solución y se garantiza que existe la próxima vez que se abra la solución.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluciones](../../extensibility/internals/solutions.md)