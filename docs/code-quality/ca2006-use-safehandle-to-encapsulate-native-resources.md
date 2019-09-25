---
title: 'CA2006: Utilizar SafeHandle para encapsular recursos nativos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233099"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizar SafeHandle para encapsular recursos nativos

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|Identificador de comprobación|CA2006|
|Categoría|Microsoft.Reliability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

El código administrado <xref:System.IntPtr> utiliza para tener acceso a los recursos nativos.

## <a name="rule-description"></a>Descripción de la regla

El uso `IntPtr` de en código administrado podría indicar un posible problema de seguridad y confiabilidad. Todos los usos `IntPtr` de deben revisarse para determinar si el uso <xref:System.Runtime.InteropServices.SafeHandle> de, o una tecnología similar, es necesario en su lugar. Se producirán problemas si `IntPtr` el representa algún recurso nativo, como la memoria, un identificador de archivo o un socket, en el que se considera que el código administrado es el propietario. Si el código administrado posee el recurso, también debe liberar los recursos nativos asociados a él, ya que si se produce un error al hacerlo, se produciría una pérdida de recursos.

En estos escenarios, los problemas de seguridad o confiabilidad también existirán si se permite el `IntPtr` acceso multiproceso a y se proporciona una forma de liberar el recurso representado por el. `IntPtr` Estos problemas implican el reciclaje `IntPtr` del valor en la liberación de recursos, mientras que el uso simultáneo del recurso se realiza en otro subproceso. Esto puede producir condiciones de carrera en las que un subproceso puede leer o escribir datos asociados al recurso equivocado. Por ejemplo, si el tipo almacena un identificador de sistema operativo `IntPtr` como y permite a los usuarios llamar a **Close** y a cualquier otro método que use ese controlador simultáneamente y sin algún tipo de sincronización, el código tiene un problema de reciclaje de identificador.

Este problema de reciclaje de controladores puede provocar daños en los datos y, con frecuencia, una vulnerabilidad de seguridad. `SafeHandle`y su clase <xref:System.Runtime.InteropServices.CriticalHandle> relacionada proporcionan un mecanismo para encapsular un identificador nativo en un recurso, de modo que se puedan evitar tales problemas de subprocesos. Además, puede usar `SafeHandle` y su clase `CriticalHandle` relacionada para otros problemas de subprocesamiento, por ejemplo, para controlar cuidadosamente la duración de los objetos administrados que contienen una copia del identificador nativo de las llamadas a métodos nativos. En esta situación, a menudo se pueden quitar llamadas `GC.KeepAlive`a. La sobrecarga de rendimiento que se produce al usar `SafeHandle` y, en menor medida, `CriticalHandle`, se puede reducir con frecuencia a través de un diseño cuidadoso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Convierta `IntPtr` el `SafeHandle` uso en para administrar de forma segura el acceso a los recursos nativos. Vea el <xref:System.Runtime.InteropServices.SafeHandle> artículo de referencia para obtener ejemplos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No se debe suprimir esta advertencia.

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable>