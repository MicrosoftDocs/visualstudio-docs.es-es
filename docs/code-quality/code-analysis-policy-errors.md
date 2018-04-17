---
title: Errores de directiva de análisis de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f9c46dae012a35dcb616366682aeffd584da70a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="code-analysis-policy-errors"></a>Errores de las directivas de análisis de código
Los errores siguientes se producen si la directiva de análisis de código no se cumple en el momento de la inserción en el repositorio:  
  
 **La configuración de análisis de código para uno o más proyectos no es compatible con la directiva de análisis de código.**  
  
 La comprobación de los requisitos de análisis de código para el control de código fuente de proyecto de equipo no se cumplió para uno o varios proyectos de código. Este error puede deberse a una o más de las condiciones siguientes:  
  
1.  El análisis de código no está habilitado en la compilación para todos los proyectos de la solución.  
  
2.  El conjunto para el proyecto en Visual Studio tiene menos restrictivo de reglas local **acción** configuración de la regla de proyecto de equipo, por ejemplo, Establece una regla que se establece en **acción**=**Error**  en el servidor tenga su **acción** establecido en **advertencia** o **ninguno** en el conjunto que se va a ejecutar en Visual Studio de reglas).  
  
3.  El conjunto de reglas especificado en Visual Studio no contiene todas las reglas incluidas en el conjunto de reglas especificado en la directiva de inserción en el repositorio de análisis de código del proyecto de equipo.  
  
 **Error en la directiva de análisis de código. Hay errores en el proyecto {0} o la compilación no está actualizada.**  
  
 La compilación contiene errores o éstos se corrigieron pero no se realizó el análisis de código después de la corrección.  
  
 **En el repositorio no se pudo. La directiva de análisis de código requiere que proteja mediante Visual Studio con una solución abierta.**  
  
 La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.  
  
 **No todos los archivos en el repositorio pendiente están dentro de la solución actualmente abierta.**  
  
 La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Este error se produce cuando hay una solución abierta pero algunos archivos de la vista "inserción en el repositorio pendiente" no forman parte de la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.  
  
 **La versión de '{0}' no es correcta. El nombre seguro especificado en la directiva es '{1}'.**  
  
 Este error se aplica a los proyectos de .NET. Un archivo .dll de regla requerido por la directiva de análisis de código existe en el equipo local, pero la versión/clave pública no coincide. Para corregir este error, el creador de la directiva debe actualizar los archivos .dll en *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules del\\*  directorio en su equipo.  
  
 **el ensamblado '{0}' especificado en la directiva no existe.**  
  
 Este error se aplica a los proyectos de .NET. Una regla requerida por la directiva de análisis de código no tiene el archivo dll correspondiente instalado en el equipo cliente. Para corregir este error, el creador de la directiva debe actualizar el archivo dll en *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules del\\*  directorio en su equipo.  
  
 **Configuración de regla de {0} de proyecto no está de acuerdo con la directiva de análisis de código.**  
  
 Este error se aplica a los proyectos de .NET. La configuración de las reglas de código administrado no es tan estricta como exige la directiva. Para corregir este error, la configuración del cliente debe ser igual o más estricta que el requisito de la directiva del servidor.  
  
 **Análisis de código no está habilitado en la configuración activa. Cambie a la configuración {0} y compilar el proyecto {1} antes de la protección.**  
  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configuración activa no tiene el análisis de código habilitado, pero hay al menos un análisis de código habilitado.  
  
 **Debe habilitar el análisis de código para los binarios administrados en las propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a las aplicaciones de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.  
  
 **Debe habilitar el análisis de código en Propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a proyectos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y proyectos web. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.  
  
 **Debe habilitar análisis de código de C/C ++ en Propiedades del proyecto {0} y compilar antes de la protección.**  
  
 Este error se aplica a los proyectos no administrados. La directiva de análisis de código requiere análisis de código para C/C++, pero no está habilitada en el proyecto actual en el cliente.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)