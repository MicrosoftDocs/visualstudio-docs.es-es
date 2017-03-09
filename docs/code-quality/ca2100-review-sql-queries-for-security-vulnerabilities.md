---
title: "CA2100: Revisar las consultas SQL en busca de vulnerabilidades de seguridad | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: Revisar las consultas SQL en busca de vulnerabilidades de seguridad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|Identificador de comprobación|CA2100|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método establece la propiedad <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> utilizando una cadena que se compila partiendo de un argumento de cadena al método.  
  
## Descripción de la regla  
 Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario.  Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL.  En un ataque de inserción de SQL, un usuario malintencionado proporciona datos que alteran el diseño de una consulta, a fin de intentar deteriorar la base de datos subyacente u obtener acceso a ella.  Entre las técnicas más usadas se encuentra la inserción de una sola comilla o un solo apóstrofe, que es el delimitador de cadena literal de SQL; dos guiones, que significan un comentario de SQL; o un signo de punto y coma, que indica que lo que sigue es un nuevo comando.  Si es imprescindible que el usuario introduzca datos en la consulta, utilice uno de los siguientes métodos, que se enumeran por orden de eficacia, para reducir el riesgo de ataques.  
  
-   Utilice un procedimiento almacenado.  
  
-   Utilice una cadena de comandos parametrizada.  
  
-   Valide el tipo y el contenido de los datos proporcionados por el usuario antes de compilar la cadena de comandos.  
  
 Los tipos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] siguientes implementan la propiedad <xref:System.Data.IDbCommand.CommandText%2A> o proporcionan constructores que establecen la propiedad mediante un argumento de cadena.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> y <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> y <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> y <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) y [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> y <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 Observe que esta regla se infringe si el método ToString de un tipo se utiliza explícita o implícitamente para construir la cadena de consulta.  A continuación, se muestra un ejemplo.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 La regla se infringe porque un usuario malintencionado puede invalidar el método ToString\(\).  
  
 La regla también se infringe si ToString se utiliza implícitamente.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice una consulta parametrizada.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el texto del comando no contiene ningún dato proporcionado por el usuario.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método, `UnsafeQuery`, que infringe la regla y otro, `SaferQuery`, que la cumple utilizando una cadena de comandos parametrizada.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## Vea también  
 [Información general de seguridad](../Topic/Security%20Overview2.md)