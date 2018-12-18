---
title: 'DA0506: Máximo de bytes privados asignados al proceso que se va a perfilar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d91dfa40136479d41d685f85012c3914c71be85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930861"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Máximo de bytes privados asignados al proceso que se va a perfilar

|||  
|-|-|  
|Identificador de regla|DA0506|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todas|  
|Mensaje|Esta información se recopiló únicamente con fines informativos. El contador de bytes privados del proceso mide la memoria virtual asignada por el proceso del que está generando perfiles. El valor notificado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Información|  

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  

## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica la cantidad máxima de memoria virtual que el proceso ha asignado actualmente en bytes (bytes privados). Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden acceder los subprocesos que se ejecutan dentro del proceso.  

 Para los procesos de 32 bits que se ejecutan en un equipo de 32 bits, el límite superior de la parte privada del espacio de direcciones de proceso es de 2 GB. Mediante el modificador [/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini, los procesos de 32 bits pueden adquirir hasta 3 GB de memoria virtual. Un proceso de 32 bits que se ejecuta en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.  

 Un proceso de 64 bits que se ejecuta en un equipo de 64 bits puede adquirir hasta 8 TB de memoria virtual privada.  

 El valor notificado es el máximo de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil.  

 Para obtener más información sobre los espacios de direcciones de proceso, consulte [Espacio de direcciones virtuales](http://go.microsoft.com/fwlink/?LinkId=177832) en la documentación de administración de memoria de Windows de MSDN.  

## <a name="how-to-use-rule-data"></a>Cómo usar los datos de la regla  
 Utilice el valor notificado para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles diferentes.  

 Se pueden producir excepciones de memoria agotada si un valor máximo de bytes privados del proceso se aproxima al límite de la arquitectura establecido para el crecimiento máximo de un espacio de direcciones de proceso. Para obtener más información, consulte [Investigar los problemas de memoria](http://go.microsoft.com/fwlink/?LinkID=177833) en MSDN Magazine.