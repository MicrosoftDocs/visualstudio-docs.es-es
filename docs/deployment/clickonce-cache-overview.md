---
title: "Información general de la memoria caché de ClickOnce | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1aa73140760f161971f30e4232658b18453f233f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-cache-overview"></a>Información general sobre la memoria caché de ClickOnce
Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones, si están instalados de forma local u hospedados en línea, se almacenan en el equipo cliente en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicación *caché*. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] caché es una familia de directorios ocultos situados bajo el directorio de configuración Local de la carpeta de Documents and Settings del usuario actual. Esta memoria caché contiene todos los archivos de la aplicación, incluidos los ensamblados, archivos de configuración, aplicación y configuración de usuario y directorio de datos. La memoria caché también es responsable de la migración de directorio de datos de la aplicación a la versión más reciente. Para obtener más información acerca de la migración de datos, vea [obtener acceso Local y remoto datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Al proporcionar una única ubicación de almacenamiento para la aplicación, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] asume la tarea de administrar la instalación física de una aplicación del usuario. La memoria caché también ayuda a aislar las aplicaciones manteniendo los ensamblados y archivos de datos para todas las aplicaciones y sus distintas versiones, separados entre sí. Por ejemplo, cuando se actualiza un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, que la versión y sus recursos de datos se proporcionan con sus propios directorios en la memoria caché.  
  
## <a name="cache-storage-quota"></a>Cuota de almacenamiento de caché  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]las aplicaciones que se hospedan en línea están restringidas en la cantidad de espacio que pueden ocupar mediante una cuota que limita el tamaño de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] memoria caché. El tamaño de caché se aplica a todas las aplicaciones del usuario en línea; una única aplicación de confianza parcial, en línea está limitada a ocupar la mitad del espacio de cuota. No están limitadas por el tamaño de caché y no cuentan para el límite del caché de las aplicaciones instaladas. Para todas las [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones, la memoria caché se conserva únicamente la versión actual y la versión instalada previamente.  
  
 De forma predeterminada, los equipos cliente que tengan 250 MB de almacenamiento para conexión [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones. Archivos de datos no cuentan para este límite. Un administrador del sistema puede ampliar o reducir esta cuota en un equipo cliente en particular cambiando la clave del registro, HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, que es un valor DWORD expresa el tamaño de caché en kilobytes. Por ejemplo, para reducir el tamaño de caché a 50 MB, debería cambiar este valor a 51200.  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)