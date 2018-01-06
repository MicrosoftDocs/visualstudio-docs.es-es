---
title: Utilidad CreateExpInstance | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c1104ebfbd066ad438262fcca0186acfb3854dbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="createexpinstance-utility"></a>Utilidad de CreateExpInstance
Use la utilidad CreateExpInstance para crear, restablecer, o eliminar una instancia experimental de Visual Studio. Puede usar la instancia experimental para depurar y probar las extensiones de Visual Studio sin cambiar el producto subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parámetros  
 / Crear  
 Crea la instancia experimental.  
  
 / Restablecimiento  
 Elimina la instancia experimental y, a continuación, crea una nueva.  
  
 /Clean  
 Elimina la instancia experimental.  
  
 / VSInstance  
 El nombre del directorio que contiene la instancia de Visual Studio base para copiar.  
  
 / /Rootsuffix  
 El sufijo que se anexará al nombre del directorio de la instancia experimental.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se trabaja en una extensión de Visual Studio, puede presionar F5 para abrir la instancia experimental de forma predeterminada e instalar la extensión actual. Si no hay ninguna instancia experimental está disponible, Visual Studio crea uno que tiene la configuración predeterminada.  
  
 La ubicación predeterminada de la instancia experimental depende del número de versión de Visual Studio. Por ejemplo, para Visual Studio 2015, la ubicación es %localappdata%\Microsoft\VisualStudio\14.0Exp\ todos los archivos de la ubicación del directorio se consideran parte de esa instancia. Visual Studio no cargará cualquier instancia experimental adicional a menos que se cambia el nombre del directorio a la ubicación predeterminada.  
  
 Visual Studio no tiene acceso al registro del sistema cuando se abre la instancia experimental. Esto difiere de las versiones anteriores de Visual Studio, que utiliza una versión del subárbol del registro experimental.  
  
 La utilidad CreateExpInstance reemplaza a la utilidad VsRegEx.  
  
 En el ejemplo siguiente se restablece la instancia experimental predeterminada de Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../../extensibility/internals/vspackages.md)