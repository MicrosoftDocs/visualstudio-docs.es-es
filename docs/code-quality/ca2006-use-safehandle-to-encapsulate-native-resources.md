---
title: 'CA2006: Utilizar SafeHandle para encapsular recursos nativos | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d70c453e502dd0a7f4eda2e9247dbc3ec3229ebe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizar SafeHandle para encapsular recursos nativos
|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|Identificador de comprobación|CA2006|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 El código administrado utiliza <xref:System.IntPtr> para tener acceso a recursos nativos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El uso de `IntPtr` en código administrado podría indicar un posible problema de seguridad y confiabilidad. Todos los usos de `IntPtr` se deben revisar para determinar si el uso de un <xref:System.Runtime.InteropServices.SafeHandle> , o una tecnología similar, es necesario en su lugar. Problemas si la `IntPtr` representa algún recurso nativo, como la memoria, un identificador de archivo o un socket, que el código administrado se considera que posea. Si el código administrado posee el recurso, deben liberar los recursos nativos asociados con él, porque un error al hacerlo provocaría la pérdida de recursos.  
  
 En estos escenarios, problemas de seguridad ni confiabilidad también existirá si se permite el acceso multiproceso a la `IntPtr` y una manera de liberar el recurso representado por el `IntPtr` se proporciona. Estos problemas incluyen el reciclaje del `IntPtr` valor al liberar el recurso mientras se realiza un uso simultáneo del recurso en otro subproceso. Esto puede producir condiciones de carrera en un subproceso puede leer o escribir los datos que está asociados al recurso incorrecto. Por ejemplo, si el tipo almacena un identificador del sistema operativo como un `IntPtr` y permite a los usuarios llamar a ambos **cerrar** y cualquier otro método que utiliza ese controlador simultáneamente y sin algún tipo de sincronización, el código tiene un identificador de reciclaje problema.  
  
 Este identificador de reciclaje de problema puede provocar daños en los datos y, con frecuencia, una vulnerabilidad de seguridad. `SafeHandle`y su clase secundaria relacionada <xref:System.Runtime.InteropServices.CriticalHandle> proporcionan un mecanismo para encapsular un identificador nativo a un recurso para que se pueden evitar estos problemas de subprocesamiento. Además, puede usar `SafeHandle` y su clase secundaria relacionada `CriticalHandle` para otros problemas de subprocesamiento, por ejemplo, para controlar la duración de objetos administrados que contienen una copia del identificador nativo sobre las llamadas a métodos nativos. En esta situación, a menudo puede quitar las llamadas a `GC.KeepAlive`. El rendimiento es posible sobrecarga se producen cuando se usa `SafeHandle` y, en menor grado, `CriticalHandle`, con frecuencia puede reducirse mediante un diseño cuidadoso.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Convertir `IntPtr` uso con respecto a `SafeHandle` para administrar el acceso a los recursos nativos de forma segura. Vea el <xref:System.Runtime.InteropServices.SafeHandle> tema de referencia para obtener ejemplos.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No se debe suprimir esta advertencia.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IDisposable>