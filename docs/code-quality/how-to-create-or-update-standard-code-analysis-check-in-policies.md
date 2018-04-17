---
title: 'Cómo: crear o actualizar directivas de protección de análisis de código estándar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9d6a28c5dd0ae8d72f11c76d33ff15268d4dda4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Cómo: Crear o actualizar directivas de inserción en el repositorio de análisis de código estándar

Puede requerir que el análisis de código se ejecute en todos los proyectos de código en un proyecto de equipo mediante el uso de la directiva de protección de análisis de código. Necesidad de análisis de código puede mejorar la calidad del código que está protegido en la base de código.

> [!NOTE]
> Esta característica solo está disponible si usas Team Foundation Server.

Directivas de protección de análisis de código se establecen en la configuración del proyecto de equipo y se aplican a cada proyecto de código del proyecto de equipo. Series de análisis de código se configuran para los proyectos de código en el archivo de proyecto (xxproj) para el proyecto de código. Series de análisis de código se realizan en el equipo local. Cuando se habilita una directiva de protección de análisis de código, archivos de un proyecto de código que se pueda protegerse deben compilarse después de su última modificación y que ejecute un análisis de código contiene, como mínimo, las reglas de la configuración del proyecto de equipo deben realizarse en el equipo donde la c se han realizado cambios.

- Para código administrado, establezca la directiva de protección especificando un *conjunto de reglas* que contiene un subconjunto de las reglas de análisis de código.

- Para el código de C o C++, la directiva de protección requiere que todas las reglas de análisis de código se ejecute. Puede agregar directivas de preprocesador para deshabilitar reglas específicas para los proyectos de código individuales en el proyecto de equipo.

Después de especificar una directiva de protección para el código administrado, los miembros del equipo pueden sincronizar su configuración de análisis de código para los proyectos de código para la configuración de directiva del proyecto de equipo.

### <a name="to-open-the-check-in-policy-editor"></a>Para abrir el editor de directiva de protección

1. En Team Explorer, haga clic en el nombre del proyecto de equipo, seleccione **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.

1. En el **Control de código fuente** cuadro de diálogo, seleccione la **directiva de protección** ficha.

1. Realice una de las siguientes acciones:

    - Haga clic en **agregar** para crear una nueva directiva en el repositorio.

    - Haga doble clic en las existentes **análisis de código** de elemento en el **tipo de directiva** lista para cambiar la directiva.

### <a name="to-set-policy-options"></a>Para establecer las opciones de directiva

Active o desactive las siguientes opciones:

    |Opción|Descripción|  
    |------------|-----------------|  
    |**Aplicar en el repositorio para que sólo contenga los archivos que forman parte de la solución actual.**|Análisis de código puede ejecutar solo en los archivos especificados en archivos de configuración de soluciones y proyectos. Esta directiva garantiza que se analiza todo el código que forma parte de una solución.|  
    |**Exigir análisis de código de C/C ++ (/analyze)**|Requiere que todos los proyectos de C o C++ se generan con el / analyze para ejecutar el análisis de código antes de que se pueden comprobar la opción del compilador.|  
    |**Exigir análisis de código para código administrado**|Requiere que todos los proyectos administrados, ejecutan análisis de código y compilación antes de protegerlos.|

### <a name="to-specify-a-managed-rule-set"></a>Para especificar un conjunto de reglas administradas

- Desde el **ejecutar este conjunto de reglas** lista, use uno de los métodos siguientes:

    - Seleccione un conjunto de reglas estándar de Microsoft.

    - Para seleccionar un conjunto de reglas personalizado, haga clic en  **\<Seleccionar conjunto de reglas de Control de código fuente... >**y, a continuación, escriba la ruta de acceso de control de versiones de la regla especificada en el Explorador de control de código fuente. La sintaxis de una ruta de acceso de control de versiones es:

    - **$/** `TeamProjectName` **/** `VersionControlPath`

    - Para obtener más información acerca de cómo crear e implementar una regla de directiva de protección personalizadas conjuntos, vea [personalizado para implementar directivas de protección para código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vea también

[Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)