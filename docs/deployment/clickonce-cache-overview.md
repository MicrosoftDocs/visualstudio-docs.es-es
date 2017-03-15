---
title: "Informaci&#243;n general sobre la memoria cach&#233; de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones ClickOnce, caché"
  - "implementación ClickOnce, caché"
  - "aplicaciones Windows, implementación ClickOnce"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Informaci&#243;n general sobre la memoria cach&#233; de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Todas las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], tanto si se instalan localmente como si se hospedan en línea, se almacenan en el equipo cliente, en una *memoria caché* de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Una memoria caché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es una familia de directorios ocultos situados bajo el directorio Configuración local de la carpeta Documents and Settings del usuario actual.  Esta memoria caché contiene todos los archivos de la aplicación, incluidos los ensamblados, archivos de configuración, configuración de la aplicación y del usuario y directorio de datos.  La memoria caché también es responsable de la migración del directorio de datos de la aplicación a la versión más reciente.  Para obtener más información sobre la migración de datos, vea [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Si se proporciona una ubicación única para el almacenamiento de la aplicación, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] asume por el usuario la tarea de administrar la instalación física de la aplicación.  La caché también ayuda a aislar las aplicaciones manteniendo los ensamblados y archivos de datos de todas las aplicaciones, así como sus distintas versiones, separados entre sí.  Por ejemplo, cuando se actualiza una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], esa versión y sus recursos de datos se proporcionan con sus propios directorios en la memoria caché.  
  
## Cuota de almacenamiento de la memoria caché  
 Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que se hospedan en línea tienen restringido el espacio que pueden ocupar mediante una cuota que limita el tamaño de la memoria caché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  El tamaño de caché se aplica a todas las aplicaciones en línea del usuario; una aplicación en línea de confianza parcial sólo puede ocupar la mitad del espacio de la cuota.  Las aplicaciones instaladas no están limitadas por el tamaño de caché y no cuentan para el límite de la caché.  Para todas las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la memoria caché guarda únicamente la versión actual y la versión previamente instalada.  
  
 De manera predeterminada, los equipos cliente disponen de 250 MB de almacenamiento para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en línea.  Los archivos de datos no cuentan con respecto a este límite.  Un administrador del sistema puede aumentar o reducir esta cuota en un equipo de cliente en particular cambiando la clave del Registro, HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB, que es un valor DWORD que expresa el tamaño de la memoria caché en kilobytes.  Por ejemplo, para reducir el tamaño de caché a 50 MB, debe cambiar este valor a 51200.  
  
## Vea también  
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)