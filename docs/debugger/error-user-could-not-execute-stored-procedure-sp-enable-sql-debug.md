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
ms.openlocfilehash: c1da494b5bb8c168775e2183f41113f00d021792
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460070"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug

El procedimiento almacenado sp_enable_sql_debug no se pudo ejecutar en el servidor. Esto se puede producir por:

- Un problema de conexión. Necesita tener una conexión estable al servidor.

- Faltan permisos necesarios en el servidor. Para depurar en SQL Server 2005, la cuenta que ejecuta Visual Studio y la cuenta empleada para conectar a SQL Server tienen que ser miembros del rol sysadmin. La cuenta empleada para conectar a SQL Server es la cuenta de usuario de Windows (si se utiliza la Autenticación de Windows) o una cuenta con id. de usuario y contraseña (si se utiliza la Autenticación SQL).

Para obtener más información, vea [Cómo: Establecer permisos de depuración para SQL Server](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Vea también

- [Cómo: Establecer permisos de depuración para SQL Server](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuración de la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))