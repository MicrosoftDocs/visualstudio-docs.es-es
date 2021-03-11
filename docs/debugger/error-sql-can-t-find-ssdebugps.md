---
description: SSDEBUGPS.dll es el componente de host de depuración de SQL Server.
title: SQL no encuentra SSDEBUGPS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a746759f294a1d8ac6b13350efd56976a1f3ae21
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146761"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL no encuentra SSDEBUGPS

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.

Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.

Hay dos maneras de resolver este error: volver a ejecutar la instalación de la depuración remota o copiar el archivo en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Para volver a ejecutar la instalación de la depuración remota, siga las instrucciones de [Depuración remota](../debugger/remote-debugging.md).

Si puede localizar una copia de ssdebugps.dll, puede copiarla en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Es posible encontrarlo en otro equipo de [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] o en un equipo que tenga instalado Visual Studio 2005.

Para copiar SSDEBUGPS.dll en el equipo con SQL Server 2005:

1. Copie el archivo al directorio con el mismo nombre y ruta de acceso en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Para registrarlo, abra un **Símbolo del sistema** y ejecute el comando siguiente:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
