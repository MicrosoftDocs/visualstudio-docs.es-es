---
title: 'Error: Ejecución de Transact-SQL finalizó sin depuración | Microsoft Docs'
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
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b67900f02a81a6a28279268c3fe6fa067bcdaedc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787645"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Error: La ejecución de Transact-SQL finalizó sin depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error se produce cuando se intenta depurar un procedimiento Transact-SQL o SQLCLR, y el depurador no recibe mensajes de depuración desde SQL Server.  
  
 Esto podría deberse a problemas de red o a problemas en SQL Server, pero la causa más probable es un problema de permisos.  
  
 Existen dos cuentas:  
  
- La cuenta de la aplicación es la cuenta de usuario con la que se ejecuta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- La cuenta de conexión es la identidad que se utiliza para realizar la conexión a SQL Server. No es necesariamente igual a la identidad con la que se ejecuta Visual Studio si la conexión utiliza la autenticación de SQL.  
  
  La depuración de SQL requiere que la cuenta de la aplicación coincida con la cuenta de conexión o que sea de administración del sistema.  
  
  Si se utiliza un inicio de sesión de SQL como administrador del sistema, la cuenta de la aplicación debe configurarse en SQL Server como sysadmin. De manera predeterminada, los administradores en el equipo donde se ejecuta SQL Server son administradores del sistema de SQL Server.  
  
  Para corregir este error, es posible que necesite:  
  
- Comprobar la configuración de los permisos. Para obtener más información, consulte [Cómo: establecer permisos de SQL Server para la depuración](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Asegurarse de que la depuración de SQL esté correctamente configurada.  
  
- Consultar al administrador de bases de datos o de la red.  
  
## <a name="see-also"></a>Vea también  
 [Configurar la depuración de SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Cómo: establecer permisos de SQL Server para la depuración](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



