---
title: Información general sobre caché ClickOnce | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7abeeec4a640119e3089c795ac529a10f8dc09
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182630"
---
# <a name="clickonce-cache-overview"></a>Información general sobre la memoria caché de ClickOnce
Todas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones, tanto si están instaladas localmente como si están hospedadas en línea, se almacenan en el equipo cliente en una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *caché*de la aplicación. Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] memoria caché es una familia de directorios ocultos en el directorio de configuración local de la carpeta Documents and Settings del usuario actual. Esta memoria caché contiene todos los archivos de la aplicación, incluidos los ensamblados, los archivos de configuración, la aplicación y la configuración de usuario, y el directorio de datos. La caché también es responsable de migrar el directorio de datos de la aplicación a la versión más reciente. Para obtener más información sobre la migración de datos, vea [acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Al proporcionar una ubicación única para el almacenamiento de la aplicación, se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lleva a cabo la tarea de administrar la instalación física de una aplicación del usuario. La memoria caché también ayuda a aislar las aplicaciones manteniendo los ensamblados y los archivos de datos de todas las aplicaciones y sus versiones distintas separadas entre sí. Por ejemplo, al actualizar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, esa versión y sus recursos de datos se suministran con sus propios directorios en la memoria caché.

## <a name="cache-storage-quota"></a>Almacenamiento en caché de la cuota de almacenamiento
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]las aplicaciones hospedadas en línea están restringidas en la cantidad de espacio que pueden ocupar una cuota que restringe el tamaño de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] memoria caché. El tamaño de la memoria caché se aplica a todas las aplicaciones en línea del usuario. una única aplicación en línea de confianza parcial se limita a ocupar la mitad del espacio de la cuota. Las aplicaciones instaladas no están limitadas por el tamaño de la memoria caché y no cuentan para el límite de caché. Para todas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones, la memoria caché conserva solo la versión actual y la versión instalada previamente.

 De forma predeterminada, los equipos cliente tienen 250 MB de almacenamiento para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones en línea. Los archivos de datos no cuentan para este límite. Un administrador del sistema puede ampliar o reducir esta cuota en un equipo cliente determinado cambiando la clave del registro, **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment\onlineappquotainkb**, que es un valor DWORD que expresa el tamaño de la caché en kilobytes. Por ejemplo, para reducir el tamaño de la memoria caché a 50 MB, debe cambiar este valor a 51200.

## <a name="see-also"></a>Consulta también
- [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)