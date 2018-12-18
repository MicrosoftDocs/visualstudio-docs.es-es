---
title: 'Error: Ejecución de Transact-SQL finalizó sin depuración | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2018
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
ms.openlocfilehash: 0efb83f6b6cbebc255f6f47c30e3934d74de7870
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349012"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Error: La ejecución de Transact-SQL finalizó sin depuración

Este error se produce cuando está intentando depurar un procedimiento SQLCLR o Transact-SQL y el depurador no recibe mensajes de depuración del servidor SQL Server.  
  
Este problema podría ser debido a problemas de red o a problemas en el servidor SQL Server, pero la causa más probable es un problema de permisos.  
  
Existen dos cuentas:  
  
- La cuenta de la aplicación es la cuenta de usuario con la que se ejecuta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- La cuenta de conexión es la identidad que se utiliza para realizar la conexión a SQL Server. Esta cuenta no es necesariamente el mismo que la identidad que se ejecuta Visual Studio como si la conexión utiliza autenticación de SQL.  
  
  Depuración de SQL requiere que la cuenta de la aplicación debe coincidir con la cuenta de conexión o ser un administrador del sistema.  
  
  Si usa un nombre de cuenta SQL como administrador del sistema, la cuenta de la aplicación debe configurarse en SQL Server como un administrador del sistema. De forma predeterminada, los administradores en el equipo que se ejecuta SQL server en son administradores del sistema de SQL Server.  
  
  Para corregir este error, es posible que necesite:  
  
  - Comprobar la configuración de los permisos. Para obtener más información, consulte [Cómo: establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Asegurarse de que la depuración de SQL esté correctamente configurada.  
  
  - Consultar al administrador de bases de datos o de la red.  
  
## <a name="see-also"></a>Vea también

- [Configurar la depuración de SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Cómo: establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)