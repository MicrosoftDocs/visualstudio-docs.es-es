---
title: Editor de conjunto de trabajo en la regla de análisis de código | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57d3c21371cc824573e29657d0b41253e556f4c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201137"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Trabajar en el editor de conjuntos de reglas de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor de conjunto de reglas de análisis de código le permite especificar las reglas que se incluyen en un conjunto de reglas personalizado y especificar la acción. También puede especificar la acción que se realizará cuando el análisis de código detecta una infracción de la regla.  
  
|.|DESCRIPCIÓN|  
|------------|-----------------|  
|**Advertencia**|Genera una advertencia en el **lista de errores** ventana.|  
|**Error**|Genera un error en la **lista de errores** ventana.|  
|**None**|Deshabilita la regla.|  
  
 El editor muestra las reglas en una estructura de árbol que agrupa las reglas por una regla de establece el campo especificado. Para agregar o quitar las reglas de un conjunto de reglas, realice uno o varios de los pasos siguientes:  
  
- Active o desactive la casilla de verificación del nodo de grupo para agregar o quitar todas las reglas del grupo. Cuando se selecciona un grupo, todas las reglas se establecen en el **advertencia** acción.  
  
- Haga clic en el **acción** campo de un grupo y, a continuación, especifique la acción que se aplican a todas las reglas del grupo.  
  
- Active o desactive la casilla de verificación de una regla individual. Cuando se selecciona la casilla de verificación para una regla, la regla se establece en la acción de advertencia.  
  
## <a name="rule-set-editor-toolbar"></a>Barra de herramientas del Editor de conjunto de reglas  
 Puede usar la barra de herramientas del editor de conjunto de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula de conjunto de reglas.  
  
 En la tabla siguiente describe los controles de la barra de herramientas del editor de conjunto de reglas.  
  
|ToolBar (control)|DESCRIPCIÓN|  
|---------------------|-----------------|  
|**Expandir todo**|Muestra las reglas en todos los grupos.|  
|**Contraer todo**|Oculta las reglas en todos los grupos.|  
|**Group By**|Especifica el campo por el que las reglas se agrupan. Haga clic en  **\<None >** para mostrar las reglas sin grupos.|  
|**Opciones de columna**|Especifica los campos de la regla para mostrar.|  
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta las reglas que no son del mismo tipo de destino que la solución.|  
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas que tienen asignada la acción de Error.|  
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas que tienen asignadas la acción de advertencia.|  
|**Mostrar reglas que no están habilitadas**|Muestra u oculta las reglas que tienen asignada ninguna acción.|  
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionado.|  
|**Buscar reglas**|Busca todos los valores de campo de la cadena que especifique.|  
  
## <a name="rule-set-fields"></a>Campos del conjunto de reglas  
 Campos muestran información acerca de una regla de establece y puede usarse para ordenar y agrupar la lista de reglas del conjunto de reglas. Para mostrar u ocultar campos, haga clic en **opciones de columna** en la regla establecer la barra de herramientas del editor y, a continuación, active o desactive las casillas de verificación de los campos para mostrar u ocultar.  
  
 En la tabla siguiente se describe los campos de un conjunto de reglas.  
  
|Campo|DESCRIPCIÓN|  
|-----------|-----------------|  
|**ID**|El identificador de la regla.|  
|**Categoría**|Además de su pertenencia a conjuntos de reglas, reglas de análisis de código también se agrupan por categoría. Para obtener más información, consulte [Code Analysis for Managed Code Warnings](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Nombre**|El título de la regla.|  
|**Espacio de nombres**|El espacio de nombres de la regla.|  
|**Tipo de destino**|Indica si la regla es para nativo, administrado o código base de datos.|  
|**Acción**|La acción realizada cuando se infringe la regla en una ejecución de análisis de código.<br /><br /> **Advertencia** -genera una advertencia.<br /><br /> **Error** -genera un error.<br /><br /> **Ninguno** -deshabilita la regla.<br /><br /> Puede editar el campo de acción. El valor None es igual que desmarcar la casilla de verificación de la regla.|  
|**Conjuntos de reglas de origen**|El conjunto de reglas que contiene la regla.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Ordenar y filtrar conjuntos de reglas  
 Desde los encabezados de columna de la cuadrícula de conjunto de reglas, puede ordenar y filtrar las reglas por los valores del campo.  
  
- Para ordenar las listas de conjunto de reglas, haga clic en el encabezado de columna del campo por el que desea ordenar. Si los conjuntos de reglas se agrupan, cada grupo se ordena por separado.  
  
- Para filtrar los conjuntos de reglas por el valor de un campo, haga clic en el botón de filtro en el encabezado de columna del campo por el que desea filtrar. Active las casillas de los valores que desea mostrar y desactive las casillas de los valores que desea ocultar.
