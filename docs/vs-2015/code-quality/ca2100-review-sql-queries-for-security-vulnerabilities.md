---
title: 'CA2100: Revisar consultas SQL para las vulnerabilidades de seguridad | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 75a95e5972b26632a1cfbfce1242e49c38c9e27b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683035"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

  La siguiente [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] tipos implementan la <xref:System.Data.IDbCommand.CommandText%2A> propiedad o proporcionar constructores que establecen la propiedad mediante un argumento de cadena.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> y <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> y <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> y <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.Data.SqlServerCe.SqlCeCommand](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) and  [System.Data.SqlServerCe.SqlCeDataAdapter](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el texto del comando no contiene ninguna entrada del usuario.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `UnsafeQuery`, que infringe la regla y un método, `SaferQuery`, que cumple la regla mediante el uso de una cadena de comandos con parámetros.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Vea también
 [Información general sobre seguridad](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
