---
title: advertencias de interoperabilidad
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aac5d5759920fa1b0e51c403e7199f6b0cc39d2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="interoperability-warnings"></a>advertencias de interoperabilidad
Advertencias de interoperabilidad admiten la interacción con los clientes COM.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Un método público o protegido se marca con el atributo System.Runtime.InteropServices.DllImportAttribute. No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca.|
|[CA1401: P/Invoke no deben estar visible](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Un método público o protegido en un tipo público tiene el atributo System.Runtime.InteropServices.DllImportAttribute (también se implementa por la palabra clave Declare en Visual Basic). No se deberían exponer estos métodos.|
|[CA1402: Evite sobrecargas en interfaces visibles para COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre. Las sobrecargas subsiguientes reciben un nombre único resultante de anexar al nombre un carácter de subrayado (_) y un entero correspondiente al orden de declaración de la sobrecarga.|
|[CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un tipo de valor Visible a través de COM se marca con el atributo System.Runtime.InteropServices.StructLayoutAttribute establecido en LayoutKind.Auto. El diseño de estos tipos puede cambiar de una versión a otra de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], lo que interrumpirá a los clientes COM que esperan un diseño concreto.|
|[CA1404: Llame a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Se realiza una llamada al método Marshal.GetLastWin32Error o al equivalente [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] función GetLastError y la llamada inmediatamente anterior no es una plataforma de invocación de método.|
|[CA1405: Los tipos base de tipos visibles para COM deben ser visibles para COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un tipo visible a través de COM se deriva de un tipo no visible a través de COM.|
|[CA1406: Evite argumentos Int64 para clientes Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits.|
|[CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM no es compatible con métodos estáticos.|
|[CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si no se especifica el atributo ClassInterfaceAttribute, se utiliza una interfaz solo de envío.|
|[CA1409: Los tipos visibles COM se deben poder crear](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un tipo de referencia marcado específicamente como visible para COM contiene un constructor parametrizado público pero no contiene un constructor (sin parámetros) predeterminado público. Un tipo sin un constructor predeterminado público no se puede crear mediante clientes COM.|
|[CA1410: Los métodos de registro COM se deben asociar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Un tipo declara un método que está marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo pero no declara un método que está marcado con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, o viceversa.|
|[CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Un método que está marcado con el atributo System.Runtime.InteropServices.ComRegisterFunctionAttribute o el atributo System.Runtime.InteropServices.ComUnregisterFunctionAttribute es visible externamente.|
|[CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un tipo se marca con el atributo System.Runtime.InteropServices.ComSourceInterfacesAttribute y por lo menos una de las interfaces especificadas no se marca con el atributo System.Runtime.InteropServices.InterfaceTypeAttribute establecido en ComInterfaceType.InterfaceIsIDispatch.|
|[CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido de los campos para obtener información que no deba exponerse o que tendrá un impacto no deseado sobre la seguridad o el diseño.|
|[CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|El tipo de datos Boolean tiene varias representaciones en el código no administrado.|
|[CA1415: Declare P/Invoke correctamente](../code-quality/ca1415-declare-p-invokes-correctly.md)|Esta regla busca declaraciones de método de invocación de plataforma que tienen como destino [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] parámetro de la estructura de las funciones que tienen un puntero a un OVERLAPPED y el parámetro administrado correspondiente no es un puntero a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estructura.|