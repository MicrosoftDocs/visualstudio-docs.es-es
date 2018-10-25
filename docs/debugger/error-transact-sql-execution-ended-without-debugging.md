---
title: 'Error: Ejecución de Transact-SQL finalizó sin depuración | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
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
ms.openlocfilehash: 1bc4de5e9ef0830f69b60d773a59411c4b691454
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894760"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Error: La ejecución de Transact-SQL finalizó sin depuración
Este error se produce cuando se intenta depurar un procedimiento Transact-SQL o SQLCLR, y el depurador no recibe mensajes de depuración desde SQL Server.  
  
 Esto podría deberse a problemas de red o a problemas en SQL Server, pero la causa más probable es un problema de permisos.  
  
 Existen dos cuentas:  
  
- La cuenta de la aplicación es la cuenta de usuario con la que se ejecuta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- La cuenta de conexión es la identidad que se utiliza para realizar la conexión a SQL Server. No es necesariamente igual a la identidad con la que se ejecuta Visual Studio si la conexión utiliza la autenticación de SQL.  
  
  La depuración de SQL requiere que la cuenta de la aplicación coincida con la cuenta de conexión o que sea de administración del sistema.  
  
  Si se utiliza un inicio de sesión de SQL como administrador del sistema, la cuenta de la aplicación debe configurarse en SQL Server como sysadmin. De manera predeterminada, los administradores en el equipo donde se ejecuta SQL Server son administradores del sistema de SQL Server.  
  
  Para corregir este error, es posible que necesite:  
  
- Comprobar la configuración de los permisos. Para obtener más información, consulte [Cómo: establecer permisos de SQL Server para la depuración](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Asegurarse de que la depuración de SQL esté correctamente configurada.  
  
- Consultar al administrador de bases de datos o de la red.  
  
## <a name="see-also"></a>Vea también  
 [Configurar la depuración de SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [Cómo: establecer permisos de SQL Server para la depuración](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)