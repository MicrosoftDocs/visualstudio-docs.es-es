---
title: 'DA0504: Espacio de trabajo máximo en bytes para el proceso del que se está generando el perfil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ced6956a41281b56a2c9c3495e7ac6af88417f7e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963884"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Espacio de trabajo máximo en bytes para el proceso del que se está generando el perfil

|||  
|-|-|  
|Identificador de regla|DA0504|  
|Categoría|Administración de recursos|  
|Método de generación de perfiles|Todas|  
|Mensaje|Esta información se recopiló únicamente con fines informativos. El contador del espacio de trabajo del proceso mide el uso de memoria física que hace el proceso del que está generando perfiles. El valor notificado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Información|  

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  

## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica la cantidad máxima de memoria física, en bytes, que el proceso está utilizando actualmente. El espacio de trabajo del proceso representa las páginas del espacio de direcciones de proceso que residen actualmente en la memoria física. Esta regla notifica el valor máximo para el espacio de trabajo del proceso mientras estaba activa la generación de perfiles.  

 El valor notificado incluye páginas residentes de los segmentos de memoria compartida a las que el proceso ha hecho referencia. Los archivos DLL compartidos a los que el proceso hace referencia se incluyen en los segmentos de memoria compartida que se cuentan. El valor del espacio de trabajo del proceso puede ser mayor que la cantidad de memoria virtual que el proceso ha asignado debido a los segmentos de memoria compartida.  

 El tamaño del espacio de trabajo del proceso refleja cuánta memoria virtual está usando activamente el proceso. También se ve afectado por la cantidad de memoria física (o RAM) disponible para ejecutar la aplicación y la contención para esa memoria física de otros procesos en ejecución. Para obtener más información sobre los espacios de trabajo del proceso, consulte [Espacio de trabajo](http://go.microsoft.com/fwlink/?LinkId=177830) en la documentación de administración de memoria de Windows de MSDN.  

## <a name="how-to-use-rule-data"></a>Cómo utilizar datos de regla  
 La regla recopila estos datos de medición de la utilidad de supervisión de rendimiento de Windows y los notifica únicamente con fines informativos. Utilícelos para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de prueba diferentes.  

 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque las columnas del contador **Process\Working Set** y **Memory\Pages/sec**. A continuación, busque el valor máximo de **Process\Working Set** y compárelo con el valor de **Memory\Pages/sec**. Con frecuencia, el espacio de trabajo máximo está asociado a un intervalo en que hay una disminución de la actividad de E/S de paginación, especialmente si el equipo tiene restricciones de memoria.