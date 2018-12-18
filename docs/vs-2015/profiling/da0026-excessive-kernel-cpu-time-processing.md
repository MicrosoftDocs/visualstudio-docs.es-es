---
title: 'DA0026: Tiempo de procesamiento excesivo de la CPU de kernel | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2dbf52ab216a2272cb3b6094126a34987588704
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749672"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Tiempo de procesamiento excesivo de la CPU de kernel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | LISTA DE TAREAS |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Método de generación de perfiles | Muestreo |  
| Mensaje | Se midió una cantidad relativamente alta de tiempo de CPU de modo kernel. Considere la posibilidad de investigar el origen con el muestreo de SysCall habilitado. |  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 El tiempo de CPU proporcional que se ejecutó en modo kernel superó la cantidad de tiempo invertido en modo usuario. Considere la posibilidad de volver a generar perfiles y muestrear el número de llamadas del sistema (syscall) para determinar la causa de los tiempos de ejecución elevados del modo kernel.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La proporción relativamente alta de tiempo que la aplicación dedicó a la ejecución del modo kernel merece una mayor investigación. Una aplicación en modo usuario hace una transición al modo kernel para realizar operaciones de E/S, esperar las primitivas de sincronización de subproceso o proceso o realizar llamadas del sistema. Puede investigar los tipos de llamadas del sistema que la aplicación realiza y las funciones que son responsables de dichas llamadas cuando se selecciona la opción para recopilar pilas de llamadas de ejemplo basadas en las llamadas del sistema.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para investigar los tipos de llamadas del sistema que la aplicación realiza, vuelva a ejecutar el perfil y seleccione la opción para recopilar ejemplos basados en las llamadas del sistema. Si está ejecutando las herramientas de generación de perfiles desde el IDE, consulte [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md) para obtener más información. Si está ejecutando las herramientas de generación de perfiles desde la línea de comandos, consulte la sección **Opciones de intervalo de muestreo** del tema [VSPerfCmd](../profiling/vsperfcmd.md) en la referencia de herramientas de la línea de comandos de las herramientas de generación de perfiles.



