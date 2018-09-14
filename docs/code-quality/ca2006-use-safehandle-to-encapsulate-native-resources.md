---
title: 'CA2006: Utilizar SafeHandle para encapsular recursos nativos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: b039dc1331ae3f8a47468289611e5bb9be32134d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549370"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizar SafeHandle para encapsular recursos nativos
|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|Identificador de comprobación|CA2006|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 El código administrado utiliza <xref:System.IntPtr> para tener acceso a los recursos nativos.

## <a name="rule-description"></a>Descripción de la regla
 El uso de `IntPtr` en código administrado podría indicar un posible problema de seguridad y confiabilidad. Todos los usos de `IntPtr` se deben revisar para determinar si el uso de un <xref:System.Runtime.InteropServices.SafeHandle> , o una tecnología similar, se requiere en su lugar. Se producirán problemas si el `IntPtr` representa algún recurso nativo, como memoria, un identificador de archivo o un socket, que el código administrado se considera como propietaria. Si el código administrado es propietario del recurso, también debe liberar los recursos nativos asociados con él, porque un error al hacerlo provocaría la pérdida de recursos.

 En estos escenarios, los problemas de seguridad ni confiabilidad también existirá si se permite el acceso multiproceso para el `IntPtr` y una manera de liberar el recurso representado por el `IntPtr` se proporciona. Estos problemas incluyen el reciclaje de los `IntPtr` valor al liberar el recurso mientras se realiza un uso simultáneo del recurso en otro subproceso. Esto puede producir las condiciones de carrera, donde un subproceso puede leer o escribir datos que está asociados a un recurso incorrecto. Por ejemplo, si el tipo almacena un identificador del sistema operativo como un `IntPtr` y permite a los usuarios llamar a ambos **cerrar** y cualquier otro método que utiliza ese controlador al mismo tiempo y sin algún tipo de sincronización, el código tiene un reciclado. problema.

 Este problema de reciclado puede provocar daños en los datos y, a menudo, una vulnerabilidad de seguridad. `SafeHandle` y su clase relacionado <xref:System.Runtime.InteropServices.CriticalHandle> proporcionan un mecanismo para encapsular un identificador nativo a un recurso para que se pueden evitar estos problemas de subprocesamiento. Además, puede usar `SafeHandle` y su clase relacionado `CriticalHandle` para otros problemas de subprocesamiento, por ejemplo, para controlar la duración de objetos administrados que contienen una copia del identificador nativo a través de las llamadas a métodos nativos. En esta situación, a menudo, puede eliminar las llamadas a `GC.KeepAlive`. La sobrecarga de rendimiento que se produzcan cuando usas `SafeHandle` y, en menor grado, `CriticalHandle`, con frecuencia se puede reducir a través de un diseño cuidadoso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Convertir `IntPtr` uso a `SafeHandle` para administrar de forma segura el acceso a los recursos nativos. Consulte la <xref:System.Runtime.InteropServices.SafeHandle> artículo de referencia para obtener ejemplos.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima esta advertencia.

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable>