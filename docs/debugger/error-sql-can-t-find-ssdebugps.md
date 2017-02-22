---
title: "Error: SQL no encuentra SSDEBUGPS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_cant_find_ssdebugps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: SQL no encuentra SSDEBUGPS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.  
  
 Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.  
  
 Hay dos maneras de resolver este error: volver a ejecutar la instalación de la depuración remota o copiar el archivo en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  
  
 Para volver a ejecutar la instalación de la depuración remota, siga las instrucciones de [Depuración remota](../debugger/remote-debugging.md).  
  
 Si puede localizar una copia de ssdebugps.dll, puede copiarla en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  Si está, el archivo se encontrará en el directorio \\Archivos de programa\\Archivos comunes\\Microsoft Shared\\Depuración de SQL.  Es posible encontrarlo en otro equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] o en un equipo que tenga instalado [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Para copiar SSDEBUGPS.dll en el equipo con SQL Server 2005  
  
1.  Copie el archivo al directorio con el mismo nombre y ruta de acceso en el equipo con [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].  
  
2.  Para registrarlo, abra un **Símbolo del sistema** y ejecute el comando siguiente:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```