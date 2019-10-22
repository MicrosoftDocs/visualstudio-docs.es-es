---
title: 'CA2118: revisar el uso de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb7404d9add159f182ae44b22444dded1aafca20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658640"
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
 Un tipo o miembro público o protegido tiene el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> cambia el comportamiento del sistema de seguridad predeterminado para los miembros que ejecutan código no administrado mediante la interoperabilidad COM o la invocación de plataforma. Por lo general, el sistema crea un [modelo de datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) para el permiso de código no administrado. Esta petición se produce en tiempo de ejecución para cada invocación del miembro y comprueba cada llamador de la pila de llamadas para obtener el permiso. Cuando el atributo está presente, el sistema realiza una [petición de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) para el permiso: se comprueban los permisos del llamador inmediato cuando el autor de la llamada se COMPILA por JIT.

 Este atributo se utiliza principalmente para aumentar el rendimiento; sin embargo, las mejoras de rendimiento suponen riesgos de seguridad importantes. Si coloca el atributo en miembros públicos que llaman a métodos nativos, los llamadores de la pila de llamadas (que no sea el llamador inmediato) no necesitan el permiso de código no administrado para ejecutar código no administrado. En función de las acciones del miembro público y el control de entradas, podría permitir que los autores de llamadas no confiables accedan a la funcionalidad normalmente restringida a código de confianza.

 El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] se basa en las comprobaciones de seguridad para evitar que los llamadores obtengan acceso directo al espacio de direcciones del proceso actual. Dado que este atributo omite la seguridad normal, el código supone una amenaza seria si se puede usar para leer o escribir en la memoria del proceso. Tenga en cuenta que el riesgo no se limita a los métodos que proporcionan intencionadamente el acceso a la memoria de proceso; también está presente en cualquier escenario en el que el código malintencionado pueda obtener acceso por cualquier medio, por ejemplo, proporcionando una entrada sorprendente, con formato incorrecto o no válida.

 La Directiva de seguridad predeterminada no concede el permiso de código no administrado a un ensamblado a menos que se ejecute desde el equipo local o sea miembro de uno de los siguientes grupos:

- Grupo de código de zona Mi PC

- Grupo de código de nombre seguro de Microsoft

- Grupo de códigos de nombre seguro de ECMA

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise detenidamente el código para asegurarse de que este atributo es absolutamente necesario. Si no está familiarizado con la seguridad del código administrado o no entiende las implicaciones de seguridad de utilizar este atributo, quítelo del código. Si el atributo es obligatorio, debe asegurarse de que los llamadores no puedan usar el código de forma malintencionada. Si el código no tiene permiso para ejecutar código no administrado, este atributo no tiene ningún efecto y debe quitarse.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que el código no proporciona a los llamadores acceso a las operaciones o recursos nativos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se infringe la regla.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el método `DoWork` proporciona una ruta de acceso del código accesible públicamente al método de invocación de plataforma `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el método público `DoDangerousThing` produce una infracción. Para resolver la infracción, `DoDangerousThing` debe hacerse privado y el acceso a él debe realizarse a través de un método público protegido por una demanda de seguridad, como se muestra en el método `DoWork`.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [optimizaciones de seguridad](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [de datos y de modelos peticiones de](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [vínculos](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
