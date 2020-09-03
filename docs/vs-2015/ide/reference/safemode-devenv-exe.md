---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665509"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en modo seguro, cargando solo el entorno y los servicios predeterminados.

## <a name="syntax"></a>Sintaxis

```
devenv /SafeMode
```

## <a name="remarks"></a>Observaciones
 Este modificador evita que se carguen todos los VSPackages de terceros cuando se inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], lo que garantiza una ejecución estable.

## <a name="description"></a>Descripción
 En el ejemplo siguiente, se inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en modo seguro.

## <a name="code"></a>Código

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Consulte también
 [Modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md)
