---
title: 'CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 837abb051467135b6332b53b2c59e5016d3adff6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233061"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|Identificador de comprobación|CA2100|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método establece la <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> propiedad mediante una cadena que se genera a partir de un argumento de cadena para el método.

## <a name="rule-description"></a>Descripción de la regla

Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario. Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL. En un ataque por inyección de SQL, un usuario malintencionado proporciona datos que alteran el diseño de una consulta en un intento de dañar u obtener acceso no autorizado a la base de datos subyacente. Entre las técnicas típicas se incluye la inserción de una comilla simple o un apóstrofo, que es el delimitador de cadena literal de SQL. dos guiones, lo que significa un comentario SQL; y un punto y coma, que indica que sigue un nuevo comando. Si los datos proporcionados por el usuario deben formar parte de la consulta, use uno de los siguientes, enumerados en orden de efectividad, para reducir el riesgo de ataque.

- Usar un procedimiento almacenado.

- Use una cadena de comandos parametrizada.

- Valide la entrada del usuario para el tipo y el contenido antes de generar la cadena de comando.

Los siguientes tipos .net implementan <xref:System.Data.IDbCommand.CommandText%2A> la propiedad o proporcionan constructores que establecen la propiedad mediante un argumento de cadena.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> y <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> y <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> y <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> y <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Tenga en cuenta que esta regla se infringe cuando el método ToString de un tipo se usa explícita o implícitamente para construir la cadena de consulta. A continuación se muestra un ejemplo.

```csharp
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

La regla se infringe porque un usuario malintencionado puede invalidar el método ToString ().

La regla también se infringe cuando se utiliza ToString implícitamente.

```csharp
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use una consulta con parámetros.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el texto del comando no contiene ninguna entrada de usuario.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un `UnsafeQuery`método,, que infringe la regla y un método `SaferQuery`,, que cumple la regla mediante una cadena de comandos parametrizada.

[!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
[!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
[!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Vea también

- [Información general sobre seguridad](/dotnet/framework/data/adonet/security-overview)