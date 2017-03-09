---
title: "CA2103: Revisar la seguridad imperativa | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103: Revisar la seguridad imperativa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|Identificador de comprobación|CA2103|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa.  
  
## Descripción de la regla  
 La seguridad imperativa utiliza objetos administrados para especificar permisos y acciones de seguridad durante la ejecución del código, en comparación con la seguridad declarativa que utiliza los atributos para almacenar permisos y acciones en metadatos.  La seguridad imperativa es muy flexible porque se puede establecer el estado de un objeto de permiso y seleccionar las acciones de seguridad utilizando la información que no está disponible hasta el tiempo de ejecución.  La desventaja de esta flexibilidad es que se corre el riesgo de que la información en tiempo de ejecución que utiliza para determinar el estado de un permiso se modifique si la acción se lleva a cabo.  
  
 Utilice la seguridad declarativa siempre que sea posible.  Las solicitudes declarativas son más fáciles de entender.  
  
## Cómo corregir infracciones  
 Revise las solicitudes de seguridad imperativa para asegurase de que el estado del permiso no depende de la información que se modifica siempre que se esté utilizando el permiso.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el permiso no depende de los datos que cambian.  Sin embargo, es mejor cambiar la demanda imperativa por su equivalente declarativa.  
  
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)