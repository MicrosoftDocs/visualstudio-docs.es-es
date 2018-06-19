---
title: 'Error: SQL puede&#39;t encuentra SSDEBUGPS | Documentos de Microsoft'
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
ms.openlocfilehash: f263d76667eb197d85a99ba06a45fc08e2f4d0d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472843"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL puede&#39;t encuentra SSDEBUGPS

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.

Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.

Hay dos maneras de resolver este error: volver a ejecutar el programa de instalación de depuración remota y copiar el archivo en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.

Para volver a ejecutar el programa de instalación de la depuración remota, siga las instrucciones de [depuración remota](../debugger/remote-debugging.md).

Si puede localizar una copia de ssdebugps.dll, puede copiarlo en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Puede encontrarlo en otro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] equipo, o en un equipo que tenga instalado Visual Studio 2005.

Para copiar SSDEBUGPS.dll en el equipo de SQL Server 2005:

1. Copie el archivo en el directorio con el mismo nombre y ruta de acceso en la [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.

2. Registrar abriendo un **símbolo**y ejecute el siguiente comando:

    ```
    regsrv32 ssdebugps.dll
    ```