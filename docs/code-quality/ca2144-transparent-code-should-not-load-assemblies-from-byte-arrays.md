---
title: 'CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a908b197e05b1795534dd00edc2c1ff9597f2d90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876209"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|Identificador de comprobación|CA2144|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente carga un ensamblado desde una matriz de bytes utilizando uno de los métodos siguientes:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Descripción de la regla
 La revisión de seguridad del código transparente no es tan exhaustiva como la revisión de seguridad del código crítico, porque el código transparente no puede realizar acciones que afectan a la seguridad. Los ensamblados cargados desde una matriz de bytes podrían no distinguirse en el código transparente, y esa matriz de bytes podría contener código importante crítico para la seguridad, que no hace falta auditar. Por lo tanto, el código transparente no debe cargar ensamblados desde una matriz de bytes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que se está cargando el ensamblado con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 La regla se desencadena en el código siguiente porque un método transparente carga un ensamblado desde una matriz de bytes.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]