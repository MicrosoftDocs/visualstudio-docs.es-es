---
title: "Errores de las directivas de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyfailures"
helpviewer_keywords: 
  - "errores de directivas, análisis de código"
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Errores de las directivas de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los errores siguientes se producen si la directiva de análisis de código no se cumple en el momento de la protección:  
  
 **La configuración de análisis de código de uno o varios proyectos no es compatible con la directiva de análisis de código.**  
  
 La comprobación de los requisitos de análisis de código para el control de código fuente de proyecto de equipo no se cumplió para uno o varios proyectos de código.  Este error puede deberse a una o más de las condiciones siguientes:  
  
1.  El análisis de código no está habilitado en la compilación para todos los proyectos de la solución.  
  
2.  El conjunto de reglas local para el proyecto en Visual Studio tiene un valor de **Acción** menos restrictivo que el conjunto de reglas de proyecto de equipo, por ejemplo, una regla que se establece en **Acción**\=**Error** en el servidor tiene su **Acción** establecida en **Advertencia** o **Ninguno** en el conjunto de reglas que se ejecuta en Visual Studio.  
  
3.  El conjunto de reglas especificado en Visual Studio no contiene todas las reglas incluidas en el conjunto de reglas especificado en la directiva de protección de análisis de código del proyecto de equipo.  
  
 **Se produjo un error en la directiva de análisis de código.  Hay errores en el proyecto {0} o la compilación no está actualizada.**  
  
 La compilación contiene errores o éstos se corrigieron pero no se realizó el análisis de código después de la corrección.  
  
 **Se produjo un error en la protección.  Según la directiva de análisis de código, debe proteger los archivos mediante Visual Studio con una solución abierta.**  
  
 La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta.  Para corregir este error, abra la solución que contiene el archivo que se va a proteger.  
  
 **No todos los archivos de la protección pendiente están dentro de la solución actualmente abierta.**  
  
 La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta.  Este error se produce cuando hay una solución abierta pero algunos archivos de la vista "protección pendiente" no forman parte de la solución actualmente abierta.  Para corregir este error, abra la solución que contiene el archivo que se va a proteger.  
  
 **La versión de "{0}" no es correcta.  El nombre seguro especificado en la directiva es "{1}".**  
  
 Este error se aplica a los proyectos de .NET.  Un archivo .dll de regla requerido por la directiva de análisis de código existe en el equipo local, pero la versión\/clave pública no coincide.  Para corregir este error, el creador de la directiva debe actualizar los archivos.dll en el directorio *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* del equipo.  
  
 **El ensamblado "{0}" especificado en la directiva no existe.**  
  
 Este error se aplica a los proyectos de .NET.  Una regla requerida por la directiva de análisis de código no tiene el archivo dll correspondiente instalado en el equipo cliente.  Para corregir este error, el creador de la directiva debe actualizar el archivo dll en el directorio *C:\\Program Files\\Microsoft Visual Studio 8\\Team Tools\\Static Analysis Tools\\FxCop\\Rules\\* del equipo.  
  
 **La configuración de la regla {0} del proyecto no cumple la directiva de análisis de código.**  
  
 Este error se aplica a los proyectos de .NET.  La configuración de las reglas de código administrado no es tan estricta como exige la directiva.  Para corregir este error, la configuración del cliente debe ser igual o más estricta que el requisito de la directiva del servidor.  
  
 **El análisis de código no está habilitado en la configuración activa.  Cambie a la configuración {0} y compile el proyecto {1} antes de la protección.**  
  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configuración activa no tiene el análisis de código habilitado, pero hay al menos un análisis de código habilitado.  
  
 **Debe habilitar el análisis de código para los binarios administrados en las propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a las aplicaciones de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.  
  
 **Debe habilitar el análisis de código en las propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a proyectos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y proyectos web.  La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.  
  
 **Debe habilitar el análisis de código de C\/C\+\+ en las propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a los proyectos no administrados.  La directiva de análisis de código requiere análisis de código para C\/C\+\+, pero no está habilitada en el proyecto actual en el cliente.  
  
## Vea también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)