---
title: "DA0504: Conjunto de trabajo m&#225;ximo en bytes para el proceso que se va a perfilar | Microsoft Docs"
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
  - "vs.performance.DA0504"
  - "vs.performance.504"
  - "vs.performance.rules.DA0504"
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0504: Conjunto de trabajo m&#225;ximo en bytes para el proceso que se va a perfilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0504|  
|Categoría|Administración de recursos|  
|Método de generación de perfiles|Todos|  
|Mensaje|Esta información se recopiló solo con fines informativos.  El contador Process Working Set mide el uso de memoria física que hace el proceso del que se está generando el perfil.  El valor indicado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Descripción de la regla  
 Este mensaje indica la cantidad máxima de memoria física que el proceso está utilizando actualmente en bytes.  El espacio de trabajo de un proceso representa las páginas del espacio de direcciones de proceso que residen actualmente en la memoria física.  Esta regla indica el valor máximo del espacio de trabajo de un proceso mientras la generación de perfiles estaba activa.  
  
 El valor indicado incluye páginas residentes de los segmentos de la memoria compartida a los que el proceso ha hecho referencia.  Las DLL compartidas a las que hace referencia el proceso están incluidas en los segmentos de la memoria compartida que se cuentan.  El valor del espacio de trabajo del proceso puede ser mayor que la cantidad de memoria virtual que el proceso ha asignado debido a los segmentos de la memoria compartida.  
  
 El tamaño del espacio de trabajo del proceso refleja cuánta memoria virtual está utilizando el proceso de forma activa.  También le afecta la cantidad de memoria física \(o RAM\) disponible para ejecutar la aplicación y la contención de esa memoria física desde otros procesos en ejecución.  Para obtener más información sobre los espacios de trabajo de procesos, [Espacio de trabajo](http://go.microsoft.com/fwlink/?LinkId=177830) vea en la documentación sobre administración de memoria de Windows de MSDN.  
  
## Cómo usar los datos de la regla  
 La regla solamente recopila y notifica estos datos sobre la medición de la utilidad de supervisión de rendimiento de Windows con fines informativos.  Utilice los datos para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de prueba.  
  
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la [Vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque las columnas de los contadores **Proceso\\Espacio de trabajo** y **Memoria\\Páginas por segundo**.  A continuación, busque el valor máximo de **Proceso\\Espacio de trabajo** y compárelo con el valor de **Memoria\\Páginas por segundo**.  A menudo, el espacio de trabajo máximo está asociado con un intervalo en el que se registra un descenso de la actividad de E\/S de paginación si la máquina tiene restricciones de memoria.