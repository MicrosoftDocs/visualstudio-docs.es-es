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
ms.openlocfilehash: 5387ce65532cb532192191bd67f29cc7af6e28c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545298"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|Identificador de comprobación|CA2100|
|Categoría|Microsoft.Security|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método establece el <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> propiedad mediante el uso de una cadena que se crea a partir de un argumento de cadena al método.

## <a name="rule-description"></a>Descripción de la regla

Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario. Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL. En un ataque de inyección de código SQL, un usuario malintencionado proporciona la entrada que modifica el diseño de una consulta en un intento de dañar o obtener acceso no autorizado a la base de datos subyacente. Las técnicas típicas incluyen la inserción de una comilla o un apóstrofo, que es el delimitador de literal de cadena SQL; dos guiones, lo que significa un comentario SQL; y un punto y coma, que indica que sigue un nuevo comando. Si la entrada del usuario debe formar parte de la consulta, use uno de los siguientes, se muestran en orden de eficacia, para reducir el riesgo de ataque.

- Usar un procedimiento almacenado.

- Utilice una cadena de comandos con parámetros.

- Validar la entrada del usuario para el tipo y el contenido antes de compilar la cadena de comandos.

Los siguientes tipos de .NET Framework implementan la <xref:System.Data.IDbCommand.CommandText%2A> propiedad o proporcionar constructores que establecen la propiedad mediante un argumento de cadena.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> y <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> y <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> y <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> y <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Tenga en cuenta que se infringe esta regla cuando se usa el método ToString de un tipo de forma explícita o implícita para construir la cadena de consulta. A continuación se muestra un ejemplo.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Dado que un usuario malintencionado puede invalidar el método ToString(), se infringe la regla.

 También se infringe la regla cuando se utiliza ToString de forma implícita.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, utilice una consulta parametrizada.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el texto del comando no contiene ninguna entrada del usuario.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `UnsafeQuery`, que infringe la regla y un método, `SaferQuery`, que cumple la regla mediante el uso de una cadena de comandos con parámetros.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Vea también
 [Información general sobre seguridad](/dotnet/framework/data/adonet/security-overview)