---
title: "C&#243;mo: Crear un informe de comparaci&#243;n del generador de perfiles desde un s&#237;mbolo del sistema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Crear un informe de comparaci&#243;n del generador de perfiles desde un s&#237;mbolo del sistema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede generar un informe de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que compare los datos de rendimiento de dos archivos de datos de generación de perfiles \(.VSP o .VSPS\).  El informe muestra las diferencias, las regresiones de rendimiento y las mejoras producidas de una sesión de generación de perfiles a otra.  Los valores del informe presentan las diferencias, o cambios, con respecto a la línea base del primer archivo que se especifica.  Esta diferencia se calcula determinando la variación entre el valor anterior, el valor de línea base, y el valor de resultado del nuevo análisis.  Las comparaciones de datos del generador de perfiles pueden estar basadas en funciones del código, módulos de la aplicación, líneas, punteros de instrucción \(IP\) y tipos.  
  
 Para enumerar los identificadores de las categorías y campos de comparación, escriba la línea de comandos siguiente:  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 Utilice la siguiente sintaxis para crear el informe de comparación:  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 Puede agregar opciones de la tabla siguiente a la línea de comandos de **VSPerfReport \/diff** .  
  
|Opción|Descripción|  
|------------|-----------------|  
|**DiffThreshold:**\[*Value*\]|La diferencia no se tiene en cuenta si se sitúa por debajo de este porcentaje de valor de umbral.  Asimismo, no aparecerán los nuevos datos con valores situados por debajo de este umbral.|  
|**DiffTable:** *TableName*|Use esta tabla para comparar archivos.  De forma predeterminada se utiliza la tabla de funciones.  Especifique el identificador que se muestra en **VSPerfReport \/querydifftables**.|  
|**DiffColumn:** *ColumnName*|Use esta columna para comparar valores.  De forma predeterminada, se utiliza la columna de porcentaje de ejemplos exclusivos.  Especifique el identificador que se muestra en **VSPerfReport \/querydifftables**.|