---
title: 'Error: SQL Can &#39; t Find SSDEBUGPS | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0e45c70d8186a178bafe6544bf83dcec1ed35d9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL Can &#39; t Find SSDEBUGPS
SSDEBUGPS.dll es el componente de host de depuración de SQL Server.  
  
 Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.  
  
 Hay dos maneras de resolver este error: volver a ejecutar el programa de instalación de depuración remota y copiar el archivo en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.  
  
 Para volver a ejecutar el programa de instalación de la depuración remota, siga las instrucciones de [depuración remota](../debugger/remote-debugging.md).  
  
 Si puede localizar una copia de ssdebugps.dll, puede copiarlo en el [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Puede encontrarlo en otro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] equipo, o en un equipo que tenga [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] instalado.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Para copiar SSDEBUGPS.dll en el equipo con SQL Server 2005  
  
1.  Copie el archivo en el directorio con el mismo nombre y ruta de acceso en la [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.  
  
2.  Registrar abriendo un **símbolo**y ejecute el siguiente comando:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```