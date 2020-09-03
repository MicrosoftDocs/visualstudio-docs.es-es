---
title: Utilidad CreateExpInstance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709241"
---
# <a name="createexpinstance-utility"></a>Utilidad CreateExpInstance
Use la utilidad **CreateExpInstance** para crear, restablecer o eliminar una instancia experimental de Visual Studio. Puede usar la instancia experimental para depurar y probar las extensiones de Visual Studio sin cambiar el producto subyacente.

## <a name="syntax"></a>Sintaxis

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parámetros
 **/Create** Crea la instancia experimental.

 **/RESET** Elimina la instancia experimental y, a continuación, crea una nueva.

 **/Clean** Elimina la instancia experimental.

 **/VSInstance** Nombre del directorio que contiene la instancia base de Visual Studio que se va a copiar.

 **/RootSuffix** Sufijo que se va a anexar al nombre del directorio de la instancia experimental.

## <a name="remarks"></a>Observaciones
 Cuando trabaje en una extensión de Visual Studio, puede presionar F5 para abrir la instancia experimental predeterminada e instalar la extensión actual. Si no hay ninguna instancia experimental disponible, Visual Studio crea una que tiene la configuración predeterminada.

 La ubicación predeterminada de la instancia experimental depende del número de versión de Visual Studio. Por ejemplo, para Visual Studio 2015, la ubicación es *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\ *. Todos los archivos de la ubicación del directorio se consideran parte de esa instancia. Visual Studio no cargará ninguna instancia experimental adicional a menos que el nombre del directorio se cambie a la ubicación predeterminada.

 Visual Studio no tiene acceso al registro del sistema cuando abre la instancia experimental. Esto difiere de las versiones anteriores de Visual Studio, que usaban una versión experimental del subárbol del registro.

 La utilidad **CreateExpInstance** reemplaza a la utilidad **VsRegEx** .

 En el ejemplo siguiente se restablece la instancia experimental predeterminada de Visual Studio:

 **CreateExpInstance.exe/RESET/VSInstance = 14.0/RootSuffix = exp**

## <a name="see-also"></a>Vea también
- [VSPackages](../../extensibility/internals/vspackages.md)
