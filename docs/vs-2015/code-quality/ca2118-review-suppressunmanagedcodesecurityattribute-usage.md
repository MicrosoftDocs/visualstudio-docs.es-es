---
title: 'CA2118: Uso de SuppressUnmanagedCodeSecurityAttribute de revisión | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d4cee2d7758f467a13875f89a9534ceb0d883b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904484"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Revisar el uso de SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|Identificador de comprobación|CA2118|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido o el miembro tiene el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> cambia el comportamiento del sistema de seguridad predeterminado por miembros que ejecutan código no administrado mediante la invocación de plataforma o interoperabilidad COM. Generalmente, el sistema realiza un [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) permiso de código no administrado. Esta demanda se produce en tiempo de ejecución para cada invocación del miembro y comprueba cada llamador en la pila de llamadas para el permiso. Cuando el atributo está presente, el sistema realiza un [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) para el permiso: los permisos del llamador inmediato se comprueban cuando el llamador está compilado con JIT.

 Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes. Si coloca el atributo en los miembros públicos que llaman a métodos nativos, los llamadores de la pila de llamadas (que no sea el llamador inmediato) no se necesita permiso de código no administrado para ejecutar código no administrado. Dependiendo de las acciones del miembro público y control de entrada, podrían permitir que a los llamadores no es de confianza a la funcionalidad de acceso restringido normalmente al código de confianza.

 El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] se basa en las comprobaciones de seguridad para impedir que los llamadores obtengan acceso directo al espacio de direcciones del proceso actual. Dado que este atributo omite la seguridad habitual, el código supone una amenaza grave si se puede usar para leer o escribir en la memoria del proceso. Tenga en cuenta que el riesgo no se limita a los métodos que deliberadamente proporcionan acceso a la memoria del proceso; También está presente en cualquier escenario donde código malintencionado puede obtener acceso por ningún medio, por ejemplo, al proporcionar entrada sorprendente, con formato incorrecto o no es válido.

 La directiva de seguridad predeterminada no conceder el permiso de código no administrado a un ensamblado a menos que se está ejecutando desde el equipo local o es un miembro de uno de los siguientes grupos:

-   Mi grupo de código de la zona de equipo

-   Grupo de código de nombre seguro de Microsoft

-   Grupo de código de nombre seguro de ECMA

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Lea detenidamente el código para asegurarse de que este atributo es absolutamente necesario. Si no está familiarizado con la seguridad del código administrado, o no entiende las implicaciones de seguridad del uso de este atributo, quitarlo de su código. Si el atributo es necesario, debe asegurarse de que los llamadores no pueden usar el código de forma malintencionada. Si el código no tiene permiso para ejecutar código no administrado, este atributo no tiene ningún efecto y se debe quitar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no proporciona acceso a operaciones nativas o los recursos que se pueden usar de forma destructiva llamadores.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente infringe la regla.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la `DoWork` método proporciona una ruta de acceso del código accesible públicamente para el método de invocación de plataforma `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el método público `DoDangerousThing` provoca una infracción. Para resolver la infracción, `DoDangerousThing` debe ser privado, y debe ser el acceso a él a través de un método público protegido por una petición de seguridad, como se muestra en el `DoWork` método.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [optimizaciones de seguridad](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [peticiones de vínculos](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



