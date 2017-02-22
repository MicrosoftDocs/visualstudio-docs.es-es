---
title: "CA2006: Utilizar SafeHandle para encapsular recursos nativos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2006: Utilizar SafeHandle para encapsular recursos nativos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|Identificador de comprobación|CA2006|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 El código administrado utiliza <xref:System.IntPtr> para tener acceso a los recursos nativos.  
  
## Descripción de la regla  
 El uso de `IntPtr` en código administrado podría indicar un posible problema para la seguridad y la confiabilidad.  Todos los usos de `IntPtr` se deben revisar para determinar se necesita utilizar en su lugar <xref:System.Runtime.InteropServices.SafeHandle> o una tecnología similar.  Se producirá un problema si `IntPtr` representa algún recurso nativo, como memoria, un identificador de archivos o un socket que el código administrado considere de su propiedad.  Si el código administrado posee el recurso, también debe liberar los recursos nativos asociados a él, porque si no lo hace se produciría la pérdida de recursos.  
  
 En estos casos, además existirán problemas de seguridad o confiabilidad si se permite el acceso multithreading a `IntPtr` y se proporciona una manera de liberar el recurso representado por `IntPtr`.  Estos problemas implican el reciclaje del valor `IntPtr` al liberar el recurso mientras en otro subproceso se está utilizando el mismo recurso simultáneamente.  Esto puede producir condiciones de carrera en las que un subproceso puede leer o escribir datos que están asociados al recurso equivocado.  Por ejemplo, si el tipo almacena un identificador OS como `IntPtr` y permite a los usuarios llamar a **Close** y a cualquier otro método que utilice simultáneamente este indicador, y sin que exista algún tipo de sincronización, el código sufrirá un problema de reciclaje de indicadores.  
  
 Este problema de reciclado de identificadores puede producir daños en los datos y, con frecuencia, una vulnerabilidad de seguridad.  Su clase `T:System.Runtime.InteropServices.CriticalHandle` y la clase del mismo nivel [SafeHandle](assetId:///SafeHandle?qualifyHint=False&autoUpgrade=True) proporcionan un mecanismo para encapsular un controlador nativo a un recurso para que se puedan evitar tales problemas del subprocesamiento.  Además, puede utilizar `SafeHandle` y su clase secundaria relacionada `CriticalHandle` para otros problemas con subprocesos, por ejemplo, para controlar la duración de los objetos administrados que contienen una copia del indicador nativo sobre las llamadas a los métodos nativos.  En esta situación, con frecuencia se puede quitar las llamadas a `GC.KeepAlive`.  La sobrecarga de rendimiento causada al utilizar `SafeHandle` y, en menor grado, `CriticalHandle`, se puede reducir con frecuencia a través de un diseño cuidadoso.  
  
## Cómo corregir infracciones  
 Convierta el uso de `IntPtr` en `SafeHandle` para administrar sin ningún riesgo el acceso a los recursos nativos.  Vea el tema de referencia de <xref:System.Runtime.InteropServices.SafeHandle> para obtener ejemplos.  
  
## Cuándo suprimir advertencias  
 Esta advertencia no se debe suprimir.  
  
## Vea también  
 <xref:System.IDisposable>