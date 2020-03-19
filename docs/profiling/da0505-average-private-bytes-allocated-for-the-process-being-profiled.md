---
title: 'DA0505: Promedio de bytes privados asignados al proceso que se va a perfilar | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b905b0de69110f5f7cd684deb6fe6c5955bb4b0c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777408"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Promedio de bytes privados asignados al proceso que se va a perfilar

|||
|-|-|
|Identificador de regla|DA0505|
|Categoría|Administración de recursos|
|Método de generación de perfiles|Todas|
|Mensaje|Esta información se recopiló únicamente con fines informativos. El contador de bytes privados del proceso mide la memoria virtual asignada por el proceso del que está generando perfiles. El valor notificado es el promedio calculado de todos los intervalos de medición.|
|Tipo de regla|Información|

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Este mensaje indica la cantidad media de memoria virtual que el proceso ha asignado actualmente en bytes (bytes privados). Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden acceder los subprocesos que se ejecutan dentro del proceso.

 Para los procesos de 32 bits que se ejecutan en un equipo de 32 bits, el límite superior de la parte privada del espacio de direcciones de proceso es de 2 GB. Mediante el modificador [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini, los procesos de 32 bits pueden adquirir hasta 3 GB de memoria virtual. Un proceso de 32 bits que se ejecuta en un equipo de 64 bits puede adquirir hasta 4 GB de memoria virtual privada.

 Un proceso de 64 bits que se ejecuta en un equipo de 64 bits puede adquirir hasta 8 TB de memoria virtual privada.

 El valor notificado es el promedio de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil.

 Para obtener más información sobre los espacios de direcciones de proceso, consulte [Espacio de direcciones virtuales](/windows/win32/memory/virtual-address-space) en la documentación de administración de memoria de Windows de MSDN.

## <a name="how-to-use-rule-data"></a>Cómo usar los datos de la regla
 Utilice el valor notificado para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles diferentes.
