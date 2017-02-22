---
title: "Advertencias de interoperabilidad | Microsoft Docs"
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
  - "vs.codeanalysis.Interoperabilityrules"
helpviewer_keywords: 
  - "advertencias de análisis de código administrado, advertencias de interoperabilidad"
  - "advertencias de interoperabilidad"
  - "advertencias, interoperabilidad"
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Advertencias de interoperabilidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de interoperabilidad son compatibles con la interacción con clientes COM.  
  
## En esta sección  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1400: Deben existir puntos de entrada P\/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Un método público o protegido se marca con el atributo System.Runtime.InteropServices.DllImportAttribute.  No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca.|  
|[CA1401: Los elementos P\/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Un método público o protegido en un tipo público tiene el atributo System.Runtime.InteropServices.DllImportAttribute \(también se implementa por la palabra clave Declare en Visual Basic\).  No se deberían exponer estos métodos.|  
|[CA1402: Evite sobrecargas en interfaces visibles para COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre.  Las sobrecargas subsiguientes reciben un nombre único resultante de anexar al nombre un carácter de subrayado \(\_\) y un entero correspondiente al orden de declaración de la sobrecarga.|  
|[CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un tipo de valor Visible a través de COM se marca con el atributo System.Runtime.InteropServices.StructLayoutAttribute establecido en LayoutKind.Auto.  El diseño de estos tipos puede cambiar de una versión a otra de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], lo que interrumpirá a los clientes COM que esperan un diseño concreto.|  
|[CA1404: Llame a GetLastError inmediatamente después de P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Se llama al método Marshal.GetLastWin32Error o al equivalente de la función GetLastError de [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] y la llamada inmediatamente anterior no se realiza a un método de invocación de plataforma.|  
|[CA1405: Los tipos base de tipos visibles para COM deben ser visibles para COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un tipo visible a través de COM se deriva de un tipo no visible a través de COM.|  
|[CA1406: Evite argumentos Int64 para clientes Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits.|  
|[CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM no es compatible con métodos estáticos.|  
|[CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto.  Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz.  De forma predeterminada, si no se especifica el atributo ClassInterfaceAttribute, se utiliza una interfaz solo de envío.|  
|[CA1409: Los tipos visibles COM se deben poder crear](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un tipo de referencia marcado específicamente como visible para COM contiene un constructor parametrizado público pero no contiene un constructor \(sin parámetros\) predeterminado público.  Un tipo sin un constructor predeterminado público no se puede crear mediante clientes COM.|  
|[CA1410: Los métodos de registro COM se deben adjuntar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Un tipo declara un método que se marca utilizando el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> pero no declara ningún método marcado utilizando el atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> o viceversa.|  
|[CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Un método marcado con el atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute o el atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute es visible externamente.|  
|[CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un tipo se marca con el atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute y por lo menos una de las interfaces especificadas no se marca con el atributo System.Runtime.InteropServices.InterfaceTypeAttribute establecido en ComInterfaceType.InterfaceIsIDispatch.|  
|[CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM.  Revise el contenido de los campos para obtener información que no deba exponerse o que tendrá un impacto no deseado sobre la seguridad o el diseño.|  
|[CA1414: Marque los argumentos P\/Invoke booleanos con MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|El tipo de datos Boolean tiene varias representaciones en el código no administrado.|  
|[CA1415: Declare los elementos P\/Invoke correctamente](../code-quality/ca1415-declare-p-invokes-correctly.md)|Esta regla busca declaraciones de método de invocación de plataforma dirigidas a funciones de [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] que tengan un puntero a un parámetro de estructura OVERLAPPED y el parámetro administrado correspondiente no es un puntero para una estructura <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.|