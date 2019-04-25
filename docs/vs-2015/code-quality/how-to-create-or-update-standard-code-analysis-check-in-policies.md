---
title: Procedimiento Crear o actualizar directivas de protección de análisis de código estándar | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 766ecde2da88c2a666470c790f6399cce198b2a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053161"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedimiento Crear o actualizar directivas de protección de análisis de código estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede requerir que el análisis de código se ejecute en todos los proyectos de código en un proyecto de equipo mediante el uso de la directiva de protección de análisis de código. Necesidad de análisis de código puede mejorar la calidad del código que está protegido en la base de código.  
  
> [!NOTE]
>  Esta característica está disponible solo si usa Team Foundation Server.  
  
 Directivas de protección de análisis de código se establecen en la configuración del proyecto de equipo y se aplican a cada proyecto de código en el proyecto de equipo. Ejecuciones de análisis de código se configuran para los proyectos de código en el archivo de proyecto (xxproj) para el proyecto de código. Ejecuciones de análisis de código se realizan en el equipo local. Cuando se habilita una directiva de protección de análisis de código, se deben compilar los archivos en un proyecto de código que se comprueben después de su última modificación y que ejecute un análisis de código contiene, como mínimo, las reglas de la configuración del proyecto de equipo deben realizarse en el equipo donde c se han realizado cambios pendientes.  
  
- Para código administrado, establezca la directiva de protección especificando un *conjunto de reglas* que contiene un subconjunto de las reglas de análisis de código.  
  
- Para el código de C o C++, la directiva de protección requiere que se ejecuten todas las reglas de análisis de código. Puede agregar directivas de preprocesador para deshabilitar reglas específicas para los proyectos de código individuales en el proyecto de equipo.  
  
  Después de especificar una directiva de protección para el código administrado, los miembros del equipo pueden sincronizar su configuración de análisis de código para proyectos de código para la configuración de directivas de proyecto de equipo.  
  
### <a name="to-open-the-check-in-policy-editor"></a>Para abrir el editor de directivas de protección  
  
1. En Team Explorer, haga clic en el nombre del proyecto de equipo, seleccione **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.  
  
2. En el **Control de código fuente** cuadro de diálogo, seleccione el **directiva de protección** ficha.  
  
3. Realice una de las siguientes acciones:  
  
    - Haga clic en **agregar** para crear una nueva directiva de protección.  
  
    - Haga doble clic en las existentes **análisis de código** de elemento en el **tipo de directiva** lista para cambiar la directiva.  
  
### <a name="to-set-policy-options"></a>Para establecer las opciones de directiva  
  
- Active o desactive las siguientes opciones:  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |**Exigir la protección para que solo contenga los archivos que forman parte de la solución actual.**|Puede ejecutar análisis de código solo en los archivos especificados en los archivos de configuración de solución y proyecto. Esta directiva garantiza que se analiza todo el código que forma parte de una solución.|  
    |**Aplicar análisis de código de C/C ++ (/analyze)**|Requiere que todos los proyectos de C o C++ se compilan con la / analyze para ejecutar el análisis de código antes de que se pueden comprobar la opción del compilador.|  
    |**Aplicar análisis de código para código administrado**|Requiere que todos los proyectos administrados, ejecutan análisis de código y compilación antes de que puedan protegerse.|  
  
- 
  
### <a name="to-specify-a-managed-rule-set"></a>Para especificar un conjunto de reglas administrado  
  
- Desde el **ejecutar este conjunto de reglas** enumerar, use uno de los métodos siguientes:  
  
    - Seleccione un conjunto de reglas estándar de Microsoft.  
  
    - Para seleccionar un conjunto de reglas personalizado, haga clic en  **\<Seleccionar conjunto de reglas de Control de código fuente... >** y, a continuación, escriba la ruta de acceso de control de versiones de la regla especificada en el Explorador de control de código fuente. La sintaxis de una ruta de acceso de control de versiones es:  
  
    - **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    - Para obtener más información sobre cómo crear e implementar una regla de directiva de protección personalizadas conjunto, consulte [personalizado para implementar directivas de protección para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
