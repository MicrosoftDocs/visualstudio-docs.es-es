---
title: 'Error: SQL puede&#39;t encuentra SSDEBUGPS | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 038b448c0ecd0b19afd7671a381eb68c9ba8cbbe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854118"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL puede&#39;t encuentra SSDEBUGPS

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.

Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.

Hay dos maneras de resolver este error: volver a ejecutar la instalación de la depuración remota o copiar el archivo en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Para volver a ejecutar el programa de instalación de la depuración remota, siga las instrucciones de [depuración remota](../debugger/remote-debugging.md).

Si puede localizar una copia de ssdebugps.dll, puede copiarla en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Puede encontrarlo en otro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina, o en un equipo que tiene instalado Visual Studio 2005.

Para copiar SSDEBUGPS.dll en el equipo con SQL Server 2005:

1. Copie el archivo al directorio con el mismo nombre y ruta de acceso en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Para registrarlo, abra un **Símbolo del sistema** y ejecute el comando siguiente:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
