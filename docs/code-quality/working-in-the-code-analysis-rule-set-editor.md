---
title: "Trabajar en el editor de conjuntos de reglas de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.ruleseteditor"
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Trabajar en el editor de conjuntos de reglas de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El editor de conjunto de reglas de análisis de código permite especificar las reglas que se incluyen en un conjunto de reglas personalizado y especificar la acción.  También puede especificar la acción que se llevará a cabo si el análisis de código encuentra una infracción de la regla.  
  
|Acción|Descripción|  
|------------|-----------------|  
|**Warning**|Genera una advertencia en la ventana **Lista de errores**.|  
|**Error**|Genera un error en la ventana **Lista de errores**.|  
|**None**|Deshabilita la regla.|  
  
 El editor muestra las reglas en una estructura de árbol que agrupa las reglas por un campo de conjunto de reglas que se especifica.  Para agregar o quitar reglas de un conjunto de reglas, realice uno o más de los pasos siguientes:  
  
-   Active o desactive la casilla del nodo de grupo para agregar o quitar todas las reglas del grupo.  Al seleccionar un grupo, todas las reglas se establecen en la acción **Warning**.  
  
-   Haga clic en el campo **Acción** de un grupo y, a continuación, especifique la acción que se aplicará a todas las reglas del grupo.  
  
-   Active o desactive la casilla de una regla individual.  Si activa la casilla de una regla, la regla se establece en la acción Warning.  
  
## Barra de herramientas del editor de conjuntos de reglas  
 Puede utilizar la barra de herramientas del editor de conjuntos de reglas para agrupar, filtrar y buscar los datos que aparecen en la cuadrícula del conjunto de reglas.  
  
 En la tabla siguiente se describen los controles de la barra de herramientas del editor de conjuntos de reglas.  
  
|Control de la barra de herramientas|Descripción|  
|-----------------------------------------|-----------------|  
|**Expandir todo**|Muestra las reglas de todos los grupos.|  
|**Contraer todo**|Oculta las reglas de todos los grupos.|  
|**Group By**|Especifica el campo por el que se agrupan las reglas.  Haga clic en **\<Ninguno\>** para mostrar las reglas sin grupos.|  
|**Opciones de columna**|Especifica los campos de regla que se van a mostrar.|  
|**Ocultar reglas que no se aplican a la solución actual**|Muestra u oculta las reglas que no son del mismo tipo de destino que la solución.|  
|**Mostrar reglas que pueden generar errores de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción Error.|  
|**Mostrar reglas que pueden generar advertencias de análisis de código**|Muestra u oculta las reglas a las que se ha asignado la acción Warning.|  
|**Mostrar reglas no habilitadas**|Muestra u oculta las reglas a las que se ha asignado la acción None.|  
|**Agregar o quitar conjuntos de reglas secundarios**|Agrega o quita las reglas de los conjuntos de reglas seleccionados.|  
|**Buscar en las reglas**|Busca la cadena que se especifica en todos los valores de campo.|  
  
## Campos del conjunto de reglas  
 Los campos del conjunto de reglas muestran información sobre un conjunto de reglas y se pueden utilizar para ordenar y agrupar la lista de reglas.  Para mostrar u ocultar campos, haga clic en **Opciones de columna** en la barra de herramientas del editor de conjuntos de reglas y, a continuación, active o desactive las casillas de los campos que desea mostrar u ocultar respectivamente.  
  
 En la siguiente tabla se describen los campos de un conjunto de reglas.  
  
|Campo|Descripción|  
|-----------|-----------------|  
|**ID**|El identificador de la regla.|  
|**Category**|Además de su pertenencia a los conjuntos de reglas, las reglas de análisis de código también se agrupan por categoría.  Para obtener más información, vea [Análisis de código de las advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|El título de la regla.|  
|**Namespace**|El espacio de nombres de la regla.|  
|**Target Type**|Indica si la regla es para código nativo, administrado o de base de datos.|  
|**Action**|La acción que se lleva a cabo cuando se infringe la regla en una ejecución de análisis de código.<br /><br /> **Warning**: genera una advertencia.<br /><br /> **Error**: genera un error.<br /><br /> **None**: deshabilita la regla.<br /><br /> Puede modificar el campo Acción.  El valor None equivale a desactivar la casilla de la regla.|  
|**Source Rule Sets**|El conjunto de reglas que contiene la regla.|  
  
## Ordenar y filtrar conjuntos de reglas  
 Con los encabezados de columna de la cuadrícula de conjuntos de reglas, puede ordenar y filtrar las reglas por los valores del campo.  
  
-   Para ordenar las listas de conjuntos de reglas, haga clic en el encabezado de columna del campo por el que desea ordenar.  Si los conjuntos de reglas están agrupados, cada grupo se ordena individualmente.  
  
-   Para filtrar los conjuntos de reglas por el valor de un campo, haga clic en el botón de filtro del encabezado de columna del campo por el que desea filtrar.  Active las casillas de los valores que desea mostrar y desactive las casillas de los valores que desea ocultar.