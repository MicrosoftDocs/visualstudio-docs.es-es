---
title: Datos de diagnóstico y registros generados por el sistema
description: Aprenda sobre los registros generados por el sistema de Visual Studio, los tipos de datos que se recopilan y cómo se usan para corregir problemas y mejorar la calidad del producto.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a6df4a90d8ddb31db88bb91ff4e874cadd3c589
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894665"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Registros generados por el sistema recopilados por Visual Studio

Visual Studio recopila registros generados por el sistema para solucionar problemas y mejorar la calidad del producto a través del [Programa para la mejora de la experiencia del usuario de Visual Studio](visual-studio-experience-improvement-program.md). Este artículo proporciona información sobre los tipos de datos que recopilamos y cómo los usamos. También proporciona sugerencias sobre cómo los creadores de extensiones pueden evitar la divulgación involuntaria de información personal o confidencial.

## <a name="types-of-collected-data"></a>Tipos de datos recopilados

Visual Studio recopila registros generados por el sistema en relación con bloqueos, falta de respuesta de la interfaz de usuario y uso elevado de la CPU o la memoria. También recopilamos información sobre los errores producidos durante la instalación del producto o su uso. Los datos recopilados varían en función del error y pueden incluir información de excepciones, seguimientos de la pila y volcados de memoria:

- Para los casos de falta de respuesta y uso elevado de la CPU, se recopilan seguimientos de pila de los subprocesos de Visual Studio pertinentes.

- En los casos donde los seguimientos de la pila de algunos subprocesos no son suficientes para determinar la causa del problema (por ejemplo, bloqueos, falta de respuesta o uso de memoria elevado), recopilamos un *volcado* de memoria. El volcado de memoria representa el estado del proceso en el momento en que se produjo el error.

- En errores inesperados (por ejemplo, una excepción al intentar escribir en un archivo en disco), Microsoft recopila información sobre la excepción. La información incluye el nombre de la excepción, el seguimiento de pila del subproceso donde se produjo la excepción, el mensaje asociado a la excepción y otra información de utilidad relativa a la excepción.

   El siguiente ejemplo de datos recopilados muestra el nombre de una excepción, el seguimiento de la pila y el mensaje de la excepción:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Cómo utilizamos los registros generados por el sistema

El flujo de trabajo que determina la causa del error varía en función del tipo de error y su gravedad.

### <a name="error-classification"></a>Clasificación de errores

Basándose en los registros, los errores se clasifican y contabilizan para priorizar su investigación. Por ejemplo, podemos detectar que el error "System.IO.\__Error.WinIOError" en "System.IO.FileStream.Init" se ha producido 500 veces en la versión \<x> del producto, y tiene la mayor tasa de incidencia en esa versión.

### <a name="work-items-for-tracking"></a>Elementos de trabajo para seguimiento

Los elementos de trabajo de errores individuales y clasificados por orden de prioridad se crean y asignan a los ingenieros para que sean investigados. Por lo general, estos elementos de trabajo contienen la clasificación, la prioridad y la información de diagnóstico relacionada con el tipo de error. Esta información se deriva de los registros generados por el sistema que se recopilan para el error. Por ejemplo, un elemento de trabajo asociado a un bloqueo podría contener el seguimiento de la pila donde se está produciendo el bloqueo.

### <a name="error-investigation"></a>Investigación de errores

Los ingenieros utilizan la información disponible en un elemento de trabajo para determinar la causa principal de un error. En algunos casos, necesitan más información de la que incluye el elemento de trabajo, en cuyo caso consultan el registro original generado por el sistema. Por ejemplo, un ingeniero podría necesitar inspeccionar un volcado de la memoria para determinar por qué se ha producido un bloqueo en el producto.

## <a name="tips-for-extension-authors"></a>Sugerencias para los creadores de extensiones

Para limitar la exposición de información personal, los creadores de extensiones no deben usar información personal u otra información confidencial en los nombres de sus módulos, tipos y métodos. Si un bloqueo u otro error similar se produce con ese código en la pila, esa información se recopila como parte de los registros generados por el sistema.

## <a name="opt-out-of-data-collection"></a>No participar en la recopilación de datos

Dada la finalidad de los datos que recopilamos y las restricciones en cuanto a acceso y retención, se recomienda usar la configuración de privacidad predeterminada de Visual Studio y Windows. No obstante, puede [dejar de participar](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) en el Programa para la mejora de la experiencia de Visual Studio. Para no participar en la recopilación de registros generados por el sistema en todos los programas, consulte [Diagnósticos, comentarios y privacidad en Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Las opciones pueden variar según la versión de Windows que se utilice.

## <a name="see-also"></a>Vea también

- [Programa para la mejora de la experiencia del usuario de Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnósticos, comentarios y privacidad en Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)