---
title: 'Error: SQL puede&#39;t encuentra SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058261"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL puede&#39;t encuentra SSDEBUGPS

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.

Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.

Hay dos maneras de resolver este error: volviendo a ejecutar el programa de instalación de la depuración remota y copiar el archivo en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.

Para volver a ejecutar el programa de instalación de la depuración remota, siga las instrucciones de [depuración remota](../debugger/remote-debugging.md).

Si puede localizar una copia de ssdebugps.dll, puede copiarla en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Puede encontrarlo en otro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina, o en un equipo que tiene instalado Visual Studio 2005.

Para copiar SSDEBUGPS.dll en el equipo de SQL Server 2005:

1. Copie el archivo en el directorio con el mismo nombre y ruta de acceso en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.

2. Registrarlo, abra un **símbolo**y ejecute el siguiente comando:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
