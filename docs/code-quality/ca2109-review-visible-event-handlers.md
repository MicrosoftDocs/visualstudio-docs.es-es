---
title: "CA2109: Revisar los controladores de eventos visibles | Microsoft Docs"
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
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2109: Revisar los controladores de eventos visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|Identificador de comprobación|CA2109|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Se detectó un método de control de eventos público o protegido.  
  
## Descripción de la regla  
 Un método de control de eventos visible externamente presenta un problema de seguridad que necesita revisión.  
  
 No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario.  Un controlador de eventos, un tipo de delgado, que invoca al método expuesto puede agregarse a cualquier evento siempre que las firmas del controlador y del evento coincidan.  Los eventos pueden provocarse de forma potencial por cualquier código y con frecuencia por el código del sistema de plena confianza como respuesta a acciones de usuario como hacer clic en un botón.  Al agregar una comprobación de seguridad a un método de control de eventos no se evita que el código registre un controlador de eventos que invoca al método.  
  
 Una solicitud no puede proteger de forma fiable un método invocado por un controlador de eventos.  Las solicitudes de seguridad ayudan a proteger el código de los llamadores que no son de confianza examinando los llamadores en la pila de llamadas.  El código que agrega un controlador de eventos a un evento no está presente necesariamente en la pila de llamadas cuando los métodos de control de eventos se ejecutan.  Por consiguiente, la pila de llamadas sólo podría tener llamadores de plena confianza al invocar el método de control de eventos.  Esto permite que las solicitudes efectuadas por el método de control de eventos se realicen correctamente.  Además, se puede declarar el permiso solicitado cuando se invoque el método.  Por estas razones, el riesgo de no corregir una infracción de esta regla sólo se puede declarar después de revisar el método de control de eventos.  Cuando revise el código, tenga en cuenta los problemas siguientes:  
  
-   Si el controlador de eventos realiza cualquier operación peligrosa o explotable, como declarar los permisos o suprimir el permiso del código no administrado.  
  
-   Cuáles son las amenazas de seguridad que tienen como origen o destino el código que provocan que el código puede ejecutarse en cualquier momento únicamente con llamadores de plena confianza de la pila.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, revise el método y evalúe lo siguiente:  
  
-   Si se puede establecer como no público un método de control de eventos.  
  
-   Si se puede mover toda la funcionalidad peligrosa fuera del controlador de eventos.  
  
-   Si se impone una solicitud de seguridad, cómo se puede obtener esto de otro modo.  
  
## Cuándo suprimir advertencias  
 Únicamente debe suprimir una advertencia de esta regla después de revisar cuidadosamente la seguridad y comprobar que el código no constituye una amenaza.  
  
## Ejemplo  
 El código siguiente muestra un método de control de eventos que puede ser utilizarse incorrectamente por código malintencionado.  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## Vea también  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/es-es/324c14f8-54ff-494d-9fd1-bfd20962c8ba)