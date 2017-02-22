---
title: "DA0503: Promedio de conjuntos de trabajo en bytes para el proceso que se va a perfilar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.503"
  - "vs.performance.DA0503"
  - "vs.performance.rules.DA0503"
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0503: Promedio de conjuntos de trabajo en bytes para el proceso que se va a perfilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0503|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todos|  
|Mensaje|Esta información se recopiló solo con fines informativos.  El contador Process Working Set mide el uso de memoria física que hace el proceso del que se está generando el perfil.  El valor indicado es el promedio calculado de todos los intervalos de medición.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Descripción de la regla  
 Este mensaje indica la cantidad media de memoria física que el proceso está utilizando actualmente en bytes \(el espacio de trabajo\).  El espacio de trabajo de un proceso representa las páginas del espacio de direcciones de proceso que residen actualmente en la memoria física.  
  
 El valor indicado incluye páginas residentes de los segmentos de la memoria compartida a los que el proceso ha hecho referencia.  Las DLL compartidas a las que hace referencia el proceso están incluidas en los segmentos de la memoria compartida que se cuentan.  El valor del espacio de trabajo del proceso puede ser mayor que la cantidad de memoria virtual que el proceso ha asignado debido a los segmentos de la memoria compartida.  
  
 El valor indicado es el promedio de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.  
  
 El tamaño del espacio de trabajo del proceso refleja cuánta memoria virtual está utilizando el proceso de forma activa.  También le afecta la cantidad de memoria física \(o RAM\) disponible para ejecutar la aplicación y la contención de esa memoria física desde otros procesos en ejecución.  Si se restringe la memoria física, el valor del espacio de trabajo del proceso puede variar considerablemente a medida que el sistema operativo intenta equilibrar el uso de memoria entre los procesos activos reduciendo periódicamente las páginas bastante inactivas de los espacios de trabajo del proceso.  
  
 Para obtener más información sobre los espacios de trabajo de procesos, [Espacio de trabajo](http://go.microsoft.com/fwlink/?LinkId=177830) vea en la documentación sobre administración de memoria de Windows de MSDN.  
  
## Cómo usar los datos de la regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles.  
  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque las columnas **Proceso\\Espacio de trabajo** y **Memoria\\Páginas por segundo**.  Compare las dos columnas y determine si hay fases concretas de ejecución de programas que parezcan estar asociadas a una mayor actividad de E\/S de paginación.