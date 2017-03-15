---
title: "DA0505: Promedio de bytes privados asignados al proceso que se va a perfilar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0505"
  - "vs.performance.rules.DA0505"
  - "vs.performance.505"
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DA0505: Promedio de bytes privados asignados al proceso que se va a perfilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0505|  
|Categoría|Administración de recursos|  
|Método de generación de perfiles|Todos|  
|Mensaje|Esta información se recopiló solo con fines informativos.  El contador Process Private Bytes mide la memoria virtual asignada por el proceso del que se está generando el perfil.  El valor indicado es el promedio calculado de todos los intervalos de medición.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Descripción de la regla  
 Este mensaje indica la cantidad media de memoria virtual que el proceso tiene asignada actualmente en bytes \(bytes privados\).  Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden tener acceso los subprocesos que se ejecutan dentro del proceso.  
  
 Para un proceso de 32 bits que se ejecuta en un equipo de 32 bits, el límite superior de la parte privada del espacio de direcciones de proceso es 2 GB.  Utilizando el [\/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) modificador Boot.ini, los procesos de 32 bits pueden adquirir hasta 3 GB de memoria virtual.  Un proceso de 32 bits que se esté ejecutando en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.  
  
 Un proceso de 64 bits que se esté ejecutando en un equipo de 64 bits puede adquirir hasta 8 TB de memoria virtual privada.  
  
 El valor indicado es el promedio de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.  
  
 Para obtener más información sobre los espacios de direcciones de proceso, vea [Espacio de dirección virtual](http://go.microsoft.com/fwlink/?LinkId=177832) en la documentación sobre administración de memoria de Windows.  
  
## Cómo usar los datos de la regla  
 Utilice el valor indicado para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles.