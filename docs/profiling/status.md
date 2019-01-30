---
title: Status | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49c06b6820de1ef921cd9c10a2a7d0a9c8b46fb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070531"
---
# <a name="status"></a>Estado
La opción **Status** de *VSPerfCmd.exe* muestra información sobre el estado del generador de perfiles y los procesos de los que actualmente se está generando el perfil.  
  
 La opción **Status** debe ser la única especificada en la línea de comandos. El generador de perfiles se debe inicializar con la opción **Start** de *VSPerfCmd.exe* para que se pueda mostrar cualquier estado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="remarks"></a>Comentarios  
 La opción **Status** muestra la siguiente información de estado para el generador de perfiles.  
  
 **Nombre del archivo de salida**  
 La ruta de acceso y el nombre del archivo de datos actual del generador de perfiles.  
  
 **Modo de recopilación**  
 SAMPLE o TRACE  
  
 **Procesos máximos**  
 El número máximo de procesos de los que se puede generar perfiles al mismo tiempo y el número de procesos actualmente activos.  
  
 **Máximo de subprocesos**  
 El número máximo de subprocesos de los que se pueden generar perfiles de una vez.  
  
 **Número de búferes**  
 El número de búferes de memoria dedicados a escribir datos de generación de perfiles.  
  
 **Tamaño de búferes**  
 El tamaño de un búfer de memoria en bytes.  
  
 La opción **Status** muestra la siguiente información de estado para cada proceso del que actualmente se generan perfiles.  
  
 **Process**  
 Nombre del proceso del que se generan perfiles.  
  
 **Identificador del proceso**  
 Identificador del sistema del proceso.  
  
 **Número de subprocesos**  
 Número de subprocesos que se están ejecutando actualmente.  
  
 **Recuento de inicios y paradas**  
 El recuento del generador de perfiles interno principal para controlar la recopilación de datos para este proceso. El recuento debe ser igual a uno para recopilar los datos. El recuento de inicios y paradas se puede manipular con las API del generador de perfiles y las opciones **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** y **ThreadOff** de VSPerfCmd.  
  
 **Recuento de suspensiones y reanudaciones**  
 El recuento del generador de perfiles interno secundario para controlar la recopilación de datos para este proceso. El número debe ser menor o igual que cero para recopilar los datos. El recuento de **suspensiones y reanudaciones** solo se puede manipular con las API del generador de perfiles.  
  
 **Usuarios con derechos de acceso al monitor**  
 Enumera los nombres de los usuarios que tienen acceso al generador de perfiles. Se puede conceder acceso a usuarios adicionales mediante la opción **Admin** de VSPerfCmd.exe  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)