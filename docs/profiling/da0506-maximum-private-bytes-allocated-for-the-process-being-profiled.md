---
title: "DA0506: M&#225;ximo de bytes privados asignados al proceso que se va a perfilar | Microsoft Docs"
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
  - "vs.performance.rules.DA0506"
  - "vs.performance.DA0506"
  - "vs.performance.506"
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0506: M&#225;ximo de bytes privados asignados al proceso que se va a perfilar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0506|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todos|  
|Mensaje|Esta información se recopiló solo con fines informativos.  El contador Process Private Bytes mide la memoria virtual asignada por el proceso del que se está generando el perfil.  El valor indicado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Descripción de la regla  
 Este mensaje indica la cantidad máxima de memoria virtual que el proceso tiene asignada actualmente en bytes \(bytes privados\).  Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden tener acceso los subprocesos que se ejecutan dentro del proceso.  
  
 Para un proceso de 32 bits que se ejecuta en un equipo de 32 bits, el límite superior de la parte privada del espacio de direcciones de proceso es 2 GB.  Utilizando el [\/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) modificador Boot.ini, los procesos de 32 bits pueden adquirir hasta 3 GB de memoria virtual.  Un proceso de 32 bits que se esté ejecutando en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.  
  
 Un proceso de 64 bits que se esté ejecutando en un equipo de 64 bits puede adquirir hasta 8 TB de memoria virtual privada.  
  
 El valor indicado es el máximo de todos los intervalos de medida en los que estaba activo el proceso para el que se generan perfiles.  
  
 Para obtener más información sobre los espacios de direcciones de proceso, vea [Espacio de dirección virtual](http://go.microsoft.com/fwlink/?LinkId=177832) en la documentación sobre administración de memoria de Windows.  
  
## Cómo usar los datos de la regla  
 Utilice el valor indicado para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles.  
  
 Un valor máximo de bytes privados de proceso que se aproxime al límite arquitectónico de crecimiento de un espacio de direcciones de proceso puede dar lugar a excepciones de memoria insuficiente.  Para obtener más información, vea [Problemas de investigación de memoria](http://go.microsoft.com/fwlink/?LinkID=177833) en MSDN Magazine.