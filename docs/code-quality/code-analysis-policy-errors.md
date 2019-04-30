---
title: Errores de las directivas de análisis de código
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 103a48172665875c3615ce57b90dc77beeb6b5c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806308"
---
# <a name="code-analysis-policy-errors"></a>Errores de las directivas de análisis de código

Los errores siguientes se producen si la directiva de análisis de código no se cumple en el momento de la protección:

**La configuración de análisis de código para uno o varios proyectos no es compatible con la directiva de análisis de código.**

Los requisitos de análisis de código la comprobación para el control de código fuente del proyecto no se cumplió para uno o varios proyectos de código. Este error puede deberse a una o más de las condiciones siguientes:

- El análisis de código no está habilitado en la compilación para todos los proyectos de la solución.

- El conjunto para el proyecto en Visual Studio tiene menos restrictivo de reglas locales **acción** establecer que la regla del proyecto, por ejemplo, Establece una regla que se establece en **acción**=**Error** en el servidor tiene su **acción** establecido en **advertencia** o **ninguno** en la regla que se va a ejecutar en Visual Studio).

- El conjunto de reglas especificado en Visual Studio no contienen todas las reglas que se especifican en el conjunto de reglas especificado en la directiva de protección de análisis de código para el proyecto.

**Error de la directiva de análisis de código. Hay errores en el proyecto {0} o la compilación no está actualizada.**

La compilación contiene errores o éstos se corrigieron pero no se realizó el análisis de código después de la corrección.

**Error al proteger. La directiva de análisis de código requiere que proteja mediante Visual Studio con una solución abierta.**

La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.

**No todos los archivos de la verificación pendiente están dentro de la solución actualmente abierta.**

La directiva de análisis de código requiere que todos los archivos que se están protegiendo estén en la solución actualmente abierta. Este error se produce cuando hay una solución abierta pero algunos archivos de la vista "inserción en el repositorio pendiente" no forman parte de la solución actualmente abierta. Para corregir este error, abra la solución que contiene el archivo que se va a proteger.

**La versión de '{0}' no es correcto. Es el nombre seguro especificado en la directiva '{1}'.**

Este error se aplica a los proyectos de .NET. Un archivo .dll de regla requerido por la directiva de análisis de código existe en el equipo local, pero la versión/clave pública no coincide. Para corregir este error, el creador de la directiva debe actualizar los archivos.dll en *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules del\\*  directorio en su equipo.

**'{0}' especificado en la directiva de ensamblado no existe.**

Este error se aplica a los proyectos de .NET. Una regla requerida por la directiva de análisis de código no tiene el archivo dll correspondiente instalado en el equipo cliente. Para corregir este error, el creador de la directiva debe actualizar el archivo dll en *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules del\\*  directorio en su equipo.

**Proyecto {0} configuración de las reglas no está en conformidad con la directiva de análisis de código.**

Este error se aplica a los proyectos de .NET. La configuración de las reglas de código administrado no es tan estricta como exige la directiva. Para corregir este error, la configuración del cliente debe ser igual o más estricta que el requisito de la directiva del servidor.

**Análisis de código no está habilitado en la configuración activa. Cambiar al configuración {0} y compile el proyecto {1} antes de la protección.**

En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configuración activa no tiene el análisis de código habilitado, pero hay al menos un análisis de código habilitado.

**Debe habilitar el análisis de código para los binarios administrados en el proyecto {0} propiedades y las compilación antes de la protección.**

Este error se aplica a las aplicaciones de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.

**Debe habilitar el análisis de código en el proyecto {0} propiedades y las compilación antes de la protección.**

Este error se aplica a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos y proyectos web. La directiva exige realizar el análisis del código administrado, pero no está habilitado en el proyecto actual en el cliente.

**Debe habilitar el análisis de código de C o C++ en el proyecto {0} propiedades y las compilación antes de la protección.**

Este error se aplica a los proyectos no administrados. La directiva de análisis de código requiere análisis de código para C/C++, pero no está habilitada en el proyecto actual en el cliente.

## <a name="see-also"></a>Vea también

- [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)