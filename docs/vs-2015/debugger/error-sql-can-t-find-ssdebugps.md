---
title: 'Error: SQL puede&#39;t encuentra SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47e0557e3ad2022250d54b7bd45844825ff79a03
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757464"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Error: SQL puede&#39;t encuentra SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll es el componente de host de depuración de SQL Server.  
  
 Este error aparece cuando se intenta iniciar la depuración e indica que el archivo especificado no está presente en el equipo con [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Las posibles causas son que nunca se ejecutó la instalación de la depuración remota o que este archivo se eliminó de algún modo.  
  
 Hay dos maneras de resolver este error: volviendo a ejecutar el programa de instalación de la depuración remota y copiar el archivo en el [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina.  
  
 Para volver a ejecutar el programa de instalación de la depuración remota, siga las instrucciones de [depuración remota](../debugger/remote-debugging.md).  
  
 Si puede localizar una copia de ssdebugps.dll, puede copiarla en el [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina. Si está, el archivo se encontrará en el directorio \Archivos de programa\Archivos comunes\Microsoft Shared\Depuración de SQL. Puede encontrarlo en otro [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina, o en un equipo que tenga [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] instalado.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Para copiar SSDEBUGPS.dll en el equipo con SQL Server 2005  
  
1.  Copie el archivo en el directorio con el mismo nombre y ruta de acceso en el [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina.  
  
2.  Registrarlo, abra un **símbolo**y ejecute el siguiente comando:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



