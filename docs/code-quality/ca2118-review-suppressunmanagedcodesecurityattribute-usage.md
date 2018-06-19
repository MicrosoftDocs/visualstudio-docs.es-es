---
title: 'CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3eeff4eca5bcc6d2490fc077501726e3ba7e8de1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917181"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute
|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|Identificador de comprobación|CA2118|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido o el miembro tiene el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> cambia el comportamiento del sistema de seguridad predeterminado por miembros que ejecutan código no administrado mediante la invocación de plataforma o interoperabilidad COM. Por lo general, el sistema hace un [datos y modelado](/dotnet/framework/data/index) permiso de código no administrado. Esta petición se produce en tiempo de ejecución para cada invocación del miembro y comprueba cada llamador en la pila de llamadas para obtener permiso. Cuando el atributo está presente, el sistema realiza una [peticiones de vínculo](/dotnet/framework/misc/link-demands) para el permiso: los permisos del llamador inmediato se comprueban cuando el llamador está compilado JIT.

 Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes. Si coloca el atributo en los miembros públicos que llaman a métodos nativos, los llamadores de la pila de llamadas (que no sea el llamador inmediato) no necesitan permiso de código no administrado para ejecutar código no administrado. Dependiendo de las acciones y el control de entrada al miembro público, podrían permitir a los llamadores no confiables a la funcionalidad de acceso restringido normalmente a código de confianza.

 El [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] se basa en las comprobaciones de seguridad para impedir que los llamadores obtengan acceso directo al espacio de direcciones del proceso actual. Dado que este atributo omite la seguridad habitual, el código supone una amenaza seria si se puede utilizar para leer o escribir en la memoria del proceso. Tenga en cuenta que el riesgo no se limita a los métodos que deliberadamente proporcionan acceso a la memoria del proceso; También está presente en cualquier escenario donde el código malintencionado puede obtener acceso por ningún medio, por ejemplo, proporcionando entrada sorprendente, tiene un formato incorrecto o no es válido.

 La directiva de seguridad predeterminada no concede el permiso de código no administrado a un ensamblado a menos que se está ejecutando desde el equipo local o es un miembro de uno de los siguientes grupos:

-   Mi grupo de código de la zona de equipo

-   Grupo de código de nombre seguro de Microsoft

-   Grupo de código de nombre seguro de ECMA

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise cuidadosamente el código para asegurarse de que este atributo es absolutamente necesario. Si no está familiarizado con la seguridad de código administrado o no entienden las implicaciones de seguridad del uso de este atributo, quítelo desde el código. Si el atributo es necesario, debe asegurarse de que los llamadores no pueden usar el código de forma malintencionada. Si el código no tiene permiso para ejecutar código no administrado, este atributo no tiene ningún efecto y se debería quitar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no proporciona a los llamadores acceso a las operaciones o nativos recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se infringe la regla.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la `DoWork` método proporciona una ruta de acceso de código públicamente accesible para el método de invocación de plataforma `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el método público `DoDangerousThing` provoca una infracción. Para resolver la infracción, `DoDangerousThing` deben realizarse privada y debe ser el acceso a él a través de un método público protegido por una petición de seguridad, como se muestra en el `DoWork` método.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines) [datos y modelado](/dotnet/framework/data/index) [las peticiones de vínculo](/dotnet/framework/misc/link-demands)
