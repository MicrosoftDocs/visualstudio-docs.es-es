---
title: 'Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84326c5c1beb91269a5f097c8c5d7cb8782a7a56
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600147"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug

El procedimiento almacenado sp_enable_sql_debug no se pudo ejecutar en el servidor. Esto se puede producir por:

- Un problema de conexión. Necesita tener una conexión estable al servidor.

- Faltan permisos necesarios en el servidor. Para depurar en SQL Server 2005, la cuenta que ejecuta Visual Studio y la cuenta empleada para conectar a SQL Server tienen que ser miembros del rol sysadmin. La cuenta empleada para conectar a SQL Server es la cuenta de usuario de Windows (si se utiliza la Autenticación de Windows) o una cuenta con id. de usuario y contraseña (si se utiliza la Autenticación SQL).

Para obtener más información, vea [Cómo: Establecer permisos de depuración para SQL Server](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Vea también

- [Cómo: Establecer permisos de depuración para SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Configuración de la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))