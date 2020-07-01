---
title: 'CA2006: usar SafeHandle para encapsular recursos nativos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521152"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizar SafeHandle para encapsular recursos nativos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|Identificador de comprobación|CA2006|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 El código administrado utiliza <xref:System.IntPtr> para tener acceso a los recursos nativos.

## <a name="rule-description"></a>Descripción de la regla
 El uso de `IntPtr` en código administrado podría indicar un posible problema de seguridad y confiabilidad. Todos los usos de `IntPtr` deben revisarse para determinar si el uso de <xref:System.Runtime.InteropServices.SafeHandle> , o una tecnología similar, es necesario en su lugar. Se producirán problemas si el `IntPtr` representa algún recurso nativo, como la memoria, un identificador de archivo o un socket, en el que se considera que el código administrado es el propietario. Si el código administrado posee el recurso, también debe liberar los recursos nativos asociados a él, ya que si se produce un error al hacerlo, se produciría una pérdida de recursos.

 En estos escenarios, los problemas de seguridad o confiabilidad también existirán si se permite el acceso multiproceso a `IntPtr` y se proporciona una forma de liberar el recurso representado por el `IntPtr` . Estos problemas implican el reciclaje del `IntPtr` valor en la liberación de recursos, mientras que el uso simultáneo del recurso se realiza en otro subproceso. Esto puede producir condiciones de carrera en las que un subproceso puede leer o escribir datos asociados al recurso equivocado. Por ejemplo, si el tipo almacena un identificador de sistema operativo como `IntPtr` y permite a los usuarios llamar a **Close** y a cualquier otro método que use ese controlador simultáneamente y sin algún tipo de sincronización, el código tiene un problema de reciclaje de identificador.

 Este problema de reciclaje de controladores puede provocar daños en los datos y, con frecuencia, una vulnerabilidad de seguridad. `SafeHandle`y su clase relacionada <xref:System.Runtime.InteropServices.CriticalHandle> proporcionan un mecanismo para encapsular un identificador nativo en un recurso, de modo que se puedan evitar tales problemas de subprocesos. Además, puede usar `SafeHandle` y su clase relacionada `CriticalHandle` para otros problemas de subprocesamiento, por ejemplo, para controlar cuidadosamente la duración de los objetos administrados que contienen una copia del identificador nativo de las llamadas a métodos nativos. En esta situación, a menudo se pueden quitar llamadas a `GC.KeepAlive` . La sobrecarga de rendimiento que en la que se incurre cuando se usa `SafeHandle` y, a un menor grado, `CriticalHandle` , a menudo se puede reducir a través de un cuidadoso diseño.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Convierta el `IntPtr` uso en `SafeHandle` para administrar de forma segura el acceso a los recursos nativos. Vea el <xref:System.Runtime.InteropServices.SafeHandle> tema de referencia para obtener ejemplos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No debe suprimir esta advertencia.

## <a name="see-also"></a>Consulte también
 <xref:System.IDisposable>
