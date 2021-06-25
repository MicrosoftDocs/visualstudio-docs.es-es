---
title: CreateExpInstance Utility | Microsoft Docs
description: Obtenga información sobre la utilidad CreateExpInstance que le permite crear, restablecer o eliminar una instancia experimental de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898141"
---
# <a name="createexpinstance-utility"></a>Utilidad CreateExpInstance
Use la **utilidad CreateExpInstance** para crear, restablecer o eliminar una instancia experimental de Visual Studio. Puede usar la instancia experimental para depurar y probar Visual Studio extensiones sin cambiar el producto subyacente.

## <a name="syntax"></a>Sintaxis

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parámetros
 **/Create** Crea la instancia experimental.

 **/Reset** Elimina la instancia experimental y, a continuación, crea una nueva.

 **/Clean** Elimina la instancia experimental.

 **/VSInstance** Nombre del directorio que contiene la base Visual Studio que se copiará.

 **/RootSuffix** Sufijo que se anexará al nombre del directorio de instancia experimental.

## <a name="remarks"></a>Observaciones
 Cuando trabaje en una extensión Visual Studio, puede presionar F5 para abrir la instancia experimental predeterminada e instalar la extensión actual. Si no hay ninguna instancia experimental disponible, Visual Studio crea una que tiene la configuración predeterminada.

 La ubicación predeterminada de la instancia experimental depende del número Visual Studio versión. Por ejemplo, para Visual Studio 2015, la ubicación es *%localappdata%\Microsoft\VisualStudio\14.0Exp \\*. Todos los archivos de la ubicación del directorio se consideran parte de esa instancia. Las instancias experimentales adicionales no se cargarán mediante Visual Studio a menos que el nombre del directorio cambie a la ubicación predeterminada.

 Visual Studio no tiene acceso al registro del sistema cuando abre la instancia experimental. Esto difiere de las versiones anteriores de Visual Studio, que usaban una versión experimental del subárbol del Registro.

 La **utilidad CreateExpInstance** reemplaza a la **utilidad VsRegEx.**

 En el ejemplo siguiente se restablece la instancia experimental predeterminada de Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Consulta también
- [VSPackages](../../extensibility/internals/vspackages.md)
