---
title: 'CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 092ac7599b0cfb715019a6a9894d845dc47747fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959062"
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
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> cambia el comportamiento del sistema de seguridad predeterminado por miembros que ejecutan código no administrado mediante la invocación de plataforma o interoperabilidad COM. Generalmente, el sistema realiza un [datos y modelado](/dotnet/framework/data/index) permiso de código no administrado. Esta demanda se produce en tiempo de ejecución para cada invocación del miembro y comprueba cada llamador en la pila de llamadas para el permiso. Cuando el atributo está presente, el sistema realiza un [peticiones de vínculo](/dotnet/framework/misc/link-demands) para el permiso: los permisos del llamador inmediato se comprueban cuando el llamador está compilado con JIT.

 Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes. Si coloca el atributo en los miembros públicos que llaman a métodos nativos, los llamadores de la pila de llamadas (que no sea el llamador inmediato) no se necesita permiso de código no administrado para ejecutar código no administrado. Dependiendo de las acciones del miembro público y control de entrada, podrían permitir que a los llamadores no es de confianza a la funcionalidad de acceso restringido normalmente al código de confianza.

 .NET Framework se basa en las comprobaciones de seguridad para impedir que los llamadores obtengan acceso directo al espacio de direcciones del proceso actual. Dado que este atributo omite la seguridad habitual, el código supone una amenaza grave si se puede usar para leer o escribir en la memoria del proceso. Tenga en cuenta que el riesgo no se limita a los métodos que deliberadamente proporcionan acceso a la memoria del proceso; También está presente en cualquier escenario donde código malintencionado puede obtener acceso por ningún medio, por ejemplo, al proporcionar entrada sorprendente, con formato incorrecto o no es válido.

 La directiva de seguridad predeterminada no conceder el permiso de código no administrado a un ensamblado a menos que se está ejecutando desde el equipo local o es un miembro de uno de los siguientes grupos:

- Mi grupo de código de la zona de equipo

- Grupo de código de nombre seguro de Microsoft

- Grupo de código de nombre seguro de ECMA

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Lea detenidamente el código para asegurarse de que este atributo es absolutamente necesario. Si no está familiarizado con la seguridad del código administrado, o no entiende las implicaciones de seguridad del uso de este atributo, quitarlo de su código. Si el atributo es necesario, debe asegurarse de que los llamadores no pueden usar el código de forma malintencionada. Si el código no tiene permiso para ejecutar código no administrado, este atributo no tiene ningún efecto y se debe quitar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no proporciona acceso a operaciones nativas o los recursos que se pueden usar de forma destructiva llamadores.

## <a name="example-1"></a>Ejemplo 1
 El ejemplo siguiente infringe la regla.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Ejemplo 2
 En el ejemplo siguiente, la `DoWork` método proporciona una ruta de acceso del código accesible públicamente para el método de invocación de plataforma `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Ejemplo 3
 En el ejemplo siguiente, el método público `DoDangerousThing` provoca una infracción. Para resolver la infracción, `DoDangerousThing` debe ser privado, y debe ser el acceso a él a través de un método público protegido por una petición de seguridad, como se muestra en el `DoWork` método.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Datos y modelado](/dotnet/framework/data/index)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)