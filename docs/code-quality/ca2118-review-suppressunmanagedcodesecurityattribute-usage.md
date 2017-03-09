---
title: "CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|Identificador de comprobación|CA2118|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público, protegido ó miembro tiene el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> cambia el comportamiento del sistema de seguridad predeterminado por miembros que ejecutan código no administrado utilizando la interoperabilidad COM o la invocación de plataforma.  Generalmente, el sistema realiza [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) para el permiso del código no administrado.  Esta solicitud se produce en tiempo de ejecución para cada invocación del miembro y comprueba los permisos de cada llamador de la pila de llamadas.  Cuando el atributo está presente, el sistema realiza un [Link Demands](../Topic/Link%20Demands.md) para el permiso: los permisos del llamador inmediato se comprueban cuando el llamador está compilado como JIT.  
  
 Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes.  Si coloca el atributo en los miembros públicos que llaman a los métodos nativos, los llamadores de la pila de llamadas \(que no sean inmediatos\) no necesitan permiso del código no administrado para ejecutarlo.  Dependiendo de las acciones del miembro público y el control de entrada, podría permitir a los llamadores poco fiables tener acceso a la funcionalidad restringida al código de confianza de forma normal.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] confía en las comprobaciones de seguridad para evitar que los llamadores obtengan acceso directo al espacio de direcciones del proceso actual.  Puesto que este atributo omite la seguridad habitual, el código supone una seria amenaza si se puede utilizar para leer o escribir en la memoria del proceso.  Tenga en cuenta que el riesgo no está limitado a los métodos que deliberadamente proporcionan acceso a la memoria del proceso; también está presente en cualquier escenario donde el código malintencionado puede obtener acceso de cualquier forma, por ejemplo proporcionando una entrada de datos no válida, por sorpresa y mal formada.  
  
 La directiva de seguridad predeterminada no concede el permiso para el código no administrado para un ensamblado a menos que se ejecute desde un equipo local o sea un miembro de uno de los siguientes grupos:  
  
-   Grupo de código de zona de Mi PC  
  
-   Grupo de código de nombre seguro de Microsoft  
  
-   Grupo de código de nombre seguro de ECMA  
  
## Cómo corregir infracciones  
 Revise su código cuidadosamente para garantizar que este atributo es absolutamente necesario.  Si no está familiarizado con la seguridad del código administrado o no entiende las implicaciones de seguridad del uso de este atributo, quítelo del código.  Si el atributo no es necesario, debe garantizar que los llamadores no pueden utilizar su código malintencionadamente.  Si su código no tiene el permiso para ejecutar el código no administrado, este atributo no tiene ningún efecto y se debería quitar.  
  
## Cuándo suprimir advertencias  
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que el código no proporcione a sus llamadores acceso a las operaciones o recursos nativos que se puedan usar de forma destructiva.  
  
## Ejemplo  
 El ejemplo siguiente infringe la regla.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Ejemplo  
 En el ejemplo siguiente, el método `DoWork` proporciona una ruta de acceso a código públicamente accesible al método `FormatHardDisk` de invocación de plataforma.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Ejemplo  
 En el ejemplo siguiente, el método `DoDangerousThing` público provoca una infracción.  Para corregir esta infracción, `DoDangerousThing` debe ser privado y se debe obtener acceso a él a través de un método público protegido por una solicitud de seguridad tal como muestra el método `DoWork`.  
  
 [!code-cs[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## Vea también  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/es-es/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Link Demands](../Topic/Link%20Demands.md)