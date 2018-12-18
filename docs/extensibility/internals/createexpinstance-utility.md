---
title: Utilidad CreateExpInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0f7f52f45023106d3e504258a538823c1c8fbb4
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500662"
---
# <a name="createexpinstance-utility"></a>Utilidad CreateExpInstance
Use la **CreateExpInstance** utilidad para crear, restablecer o eliminar una instancia experimental de Visual Studio. Puede usar la instancia experimental para depurar y probar las extensiones de Visual Studio sin cambiar el producto subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>Parámetros  
 **/ Crear** crea la instancia experimental.  
  
 **O restablecer**  
 Elimina la instancia experimental y, a continuación, crea una nueva.  
  
 **/Clean**  
 Elimina la instancia experimental.  
  
 **/ VSInstance**  
 El nombre del directorio que contiene la instancia de Visual Studio base para copiar.  
  
 **/ RootSuffix**  
 El sufijo para anexar al nombre del directorio de la instancia experimental.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se trabaja en una extensión de Visual Studio, puede presionar F5 para abrir la instancia experimental de forma predeterminada e instalar la extensión actual. Si no está disponible ninguna instancia experimental, Visual Studio crea uno que tiene la configuración predeterminada.  
  
 El número de versión de Visual Studio depende de la ubicación predeterminada de la instancia experimental. Por ejemplo, para Visual Studio 2015, la ubicación es *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Todos los archivos de la ubicación del directorio se consideran parte de esa instancia. No se cargará a cualquier instancia experimental adicional por Visual Studio a menos que se cambia el nombre del directorio a la ubicación predeterminada.  
  
 Visual Studio no tiene acceso al registro del sistema cuando se abre la instancia experimental. Esto difiere de las versiones anteriores de Visual Studio, que usa una versión experimental del subárbol del registro.  
  
 El **CreateExpInstance** utilidad reemplaza el **VsRegEx** utilidad.  
  
 El ejemplo siguiente restablece la instancia experimental de forma predeterminada de Visual Studio:  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../../extensibility/internals/vspackages.md)