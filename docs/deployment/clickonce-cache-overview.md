---
title: Información general de la memoria caché de ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 323b179a81f9bdd66858c1ff2f96b8ce86b30b10
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865042"
---
# <a name="clickonce-cache-overview"></a>Información general sobre la memoria caché de ClickOnce
Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones, si se instalan localmente u hospedados en línea, se almacenan en el equipo cliente en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicación *caché*. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] caché es una familia de directorios ocultos situados bajo el directorio de configuración Local de la carpeta de Documents and Settings del usuario actual. Esta memoria caché contiene todos los archivos de la aplicación, incluidos los ensamblados, archivos de configuración, aplicación y configuración de usuario y directorio de datos. La memoria caché también es responsable de la migración de directorio de datos de la aplicación a la versión más reciente. Para obtener más información sobre la migración de datos, vea [obtener acceso Local y remota de datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Al proporcionar una única ubicación para el almacenamiento de la aplicación, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tiene sobre la tarea de administrar la instalación física de una aplicación del usuario. La memoria caché también ayuda a aislar las aplicaciones manteniendo los ensamblados y archivos de datos para todas las aplicaciones y sus distintas versiones independientes entre sí. Por ejemplo, cuando actualiza un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, que la versión y sus recursos de datos se proporcionan con sus propios directorios en la memoria caché.  
  
## <a name="cache-storage-quota"></a>Cuota de almacenamiento de caché  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones que se hospedan en línea están restringidas en la cantidad de espacio que pueden ocupar mediante una cuota que limita el tamaño de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] memoria caché. El tamaño de caché se aplica a todas las aplicaciones del usuario en línea; una sola aplicación de confianza parcial, en línea se limita a ocupar la mitad del espacio de cuota. Las aplicaciones instaladas no están limitadas por el tamaño de caché y no cuentan para el límite de caché. Para todas las [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones, la memoria caché se conserva únicamente la versión actual y la versión instalada previamente.  
  
 De forma predeterminada, los equipos cliente tienen 250 MB de almacenamiento en línea [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones. Archivos de datos no cuentan para este límite. Puede ampliar o reducir esta cuota en un equipo cliente en particular cambiando la clave del registro, un administrador del sistema **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**, que es un valor DWORD que expresa el tamaño de caché en kilobytes. Por ejemplo, para reducir el tamaño de caché a 50 MB, cambiaría este valor a 51200.  
  
## <a name="see-also"></a>Vea también  
 [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)