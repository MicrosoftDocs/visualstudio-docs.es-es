---
title: C++Referencia del comprobador de directrices básicas
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5fe14c1bcb2b375a104a928513134b1789d437
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745960"
---
# <a name="c-core-guidelines-checker-reference"></a>C++Referencia del comprobador de directrices básicas

En esta sección C++ se enumeran las advertencias del comprobador de directrices básicas. Para obtener información sobre el análisis de código, vea [/Analyze (análisis de código)](/cpp/build/reference/analyze-code-analysis) y [Inicio rápido: análisisC++de código para C/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Algunas advertencias pertenecen a más de un grupo y no todas las advertencias tienen un tema de referencia completo.

## <a name="owner_pointer-group"></a>Grupo OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) Devuelve un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) Restablece o elimina explícitamente un propietario \<T > puntero '% variable% '. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) No elimine un propietario \<T > que puede estar en un estado no válido. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) No asigne a un propietario \<T > que puede tener un estado válido. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) No asigne un puntero sin formato a un propietario \<T >. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Prefiere objetos de ámbito, no asignar montones innecesariamente. Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Nunca se ha probado la nulidad del símbolo '% Symbol% ', se puede marcar como not_null. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) No se ha comprobado la nulidad del símbolo '% Symbol% ' en todas las rutas de acceso. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) El tipo de expresión '% expr% ' ya es GSL:: not_null. No lo pruebe para comprobar si hay valores NULL. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Grupo RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) No asigne el resultado de una llamada de función o asignación con un propietario \<T > valor devuelto a un puntero sin formato; en su lugar, utilice el propietario \<T >. Consulte [ C++ las directrices básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) No elimine un puntero sin formato que no sea propietario \<T >. Consulte [ C++ las directrices básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   devuelve un objeto de ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) Evite malloc () y Free (), prefiere la versión nothrow de New con DELETE. Consulte [ C++ directrices básicas R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Evite llamar a New y DELETE explícitamente. Use STD:: make_unique \<T > en su lugar. Consulte [ C++ Core Guidelines R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Nunca se ha probado la nulidad del símbolo '% Symbol% ', se puede marcar como not_null. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) No se ha comprobado la nulidad del símbolo '% Symbol% ' en todas las rutas de acceso. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) El tipo de expresión '% expr% ' ya es GSL:: not_null. No lo pruebe para comprobar si hay valores NULL. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) No utilice aritmética de punteros. En su lugar, use span. Consulte [ C++ los límites de Core Guidelines. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Expresión '% expr% ': no hay decadencia de matriz a puntero. Vea [ C++ los límites de Core Guidelines. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Grupo UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) El parámetro '% Parameter% ' es una referencia a `const` puntero único, use const T * o const T & en su lugar. Consulte [ C++ directrices básicas R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) El parámetro '% Parameter% ' es una referencia a un puntero único y nunca se reasigna ni se restablece. Use T * o T & en su lugar. Consulte [ C++ directrices básicas R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Mueve, copia, reasigna o restablece un puntero inteligente local '% Symbol% '. Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) El parámetro de puntero inteligente '% Symbol% ' solo se utiliza para tener acceso al puntero contenido. En su lugar, use T * o T &. Consulte [ C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Grupo SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Mueve, copia, reasigna o restablece un puntero inteligente local '% Symbol% '. Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) El parámetro de puntero inteligente '% Symbol% ' solo se utiliza para tener acceso al puntero contenido. En su lugar, use T * o T &. Consulte [ C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) La referencia rvalue pasa el parámetro de puntero compartido '% Symbol% '. Pase por valor en su lugar. Consulte [ C++ Core Guidelines R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) El parámetro de puntero compartido '% Symbol% ' se pasa por referencia y no se restablece o reasigna. En su lugar, use T * o T &. Consulte [ C++ directrices básicas R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) El parámetro de puntero compartido '% Symbol% ' no se ha copiado o se ha quitado. En su lugar, use T * o T &. Consulte [ C++ directrices básicas R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Grupo de declaraciones

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) El inicializador global llama a una función no constexpr '% Symbol% '. Consulte [ C++ las directrices básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) El inicializador global tiene acceso al objeto extern '% Symbol% '. Consulte [ C++ las directrices básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Evite objetos sin nombre con construcción y destrucción personalizadas. Vea [es. 84: no (intentar) declarar una variable local sin nombre](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Grupo de clases

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Si define o elimina cualquier operación predeterminada en el tipo '% Symbol% ', defina o elimine todas. Consulte [ C++ las directrices básicas C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) La función '% Symbol% ' debe marcarse con ' override '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) La función '% symbol_1% ' oculta una función no virtual '% symbol_2% '. Consulte [ C++ las directrices básicas C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) La función '% Symbol% ' debe especificar exactamente uno de los símbolos ' virtual ', ' override ' o ' final '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md) El tipo '% Symbol% ' con una función virtual necesita un destructor público virtual o protegido no virtual. Consulte [ C++ las directrices básicas C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) El destructor de invalidación no debe utilizar especificadores explícitos ' override ' o ' virtual '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>Grupo de tipos

[C26437 DONT_SLICE](C26437.md) No segmentar. Consulte [ C++ directrices básicas es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Grupo de estilos

[C26438 NO_GOTO](C26438.md) Evite `goto`. Consulte [ C++ directrices básicas es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funciones

[C26439 SPECIAL_NOEXCEPT](C26439.md) Este tipo de función no puede iniciarse. Declárelo `noexcept`. Consulte [ C++ las directrices básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) La función '% Symbol% ' se puede declarar como `noexcept`. Consulte [ C++ las directrices básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) La función se declara **noexception** , pero llama a una función que puede producir excepciones.
Consulte [ C++ las directrices básicas: F. 6: si es posible que la función no se inicie, declárela noexception](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDAD

[C26441 NO_UNNAMED_GUARDS](C26441.md) Los objetos Guard deben tener nombre. Consulte [ C++ Core Guidelines CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST Group

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) El argumento de referencia '% argument% ' de la función '% function% ' se puede marcar como `const`. Consulte [ C++ directrices básicas con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): el argumento de puntero '% argument% ' de la función '% function% ' se puede marcar como puntero a `const`. Consulte [ C++ directrices básicas con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) El valor al que apunta '% variable% ' se asigna solo una vez, márquelo como puntero a `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) Los elementos de la matriz '% array% ' se asignan solo una vez, Mark Elements `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) Los valores a los que apuntan los elementos de la matriz '% array% ' solo se asignan una vez, marque los elementos como puntero en `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) La variable '% variable% ' se asigna solo una vez, márquela como `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) Esta función% FUNCTION% se puede marcar como `constexpr` si se desea una evaluación en tiempo de compilación. Consulte [ C++ las directrices básicas F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) Esta llamada de función% FUNCTION% puede utilizar `constexpr` si se desea la evaluación en tiempo de compilación. Consulte [ C++ directrices básicas con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Grupo de tipos

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) No utilice `const_cast` para desechar `const`. `const_cast` no es necesario; Esta conversión no está quitando la constante o la volatilidad. Consulte [ C++ las instrucciones básicas Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) No use `static_cast` downcasts. Una conversión de un tipo polimórfico debe usar dynamic_cast. Consulte [ C++ las instrucciones básicas Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) No utilice `reinterpret_cast`. Una conversión de void * puede usar `static_cast`. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) No use un `static_cast` para las conversiones aritméticas. Use la inicialización de llave, GSL:: narrow_cast o GSL:: narow. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) No convierta entre tipos de puntero en los que el tipo de origen y el tipo de destino sean los mismos. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) No convierta entre tipos de puntero cuando la conversión podría ser implícita. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) No use conversiones de estilo de función. Consulte [ C++ directrices básicas es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) No utilice `reinterpret_cast`. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) No use `static_cast` downcasts. Consulte [ C++ las instrucciones básicas Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) No utilice `const_cast` para desechar `const`. Consulte [ C++ las instrucciones básicas Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) No use conversiones de estilo C. Consulte [ C++ las instrucciones básicas tipo. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) La variable '% variable% ' no está inicializada. Inicialice siempre un objeto. Consulte [ C++ instrucciones básicas Type. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) La variable '% variable% ' no está inicializada. Inicialice siempre una variable miembro. Consulte [ C++ las instrucciones básicas Type. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de límites

[C26446 USE_GSL_AT](c26446.md) Prefiere usar `gsl::at()` en lugar de un operador de subíndice sin comprobar. Consulte [ C++ directrices básicas: Bounds. 4: no usar funciones y tipos de la biblioteca estándar que no estén comprobados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
No utilice aritmética de punteros. En su lugar, use span. Consulte [ C++ límites de directrices básicas. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) Solo se indexa en matrices mediante expresiones constantes. Consulte [ C++ límites de las directrices básicas. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) El valor% Value% está fuera de los límites (0,% Bound%) de la variable '% variable% '. Solo se indexa en matrices mediante expresiones constantes que se encuentran dentro de los límites de la matriz. Consulte [ C++ límites de las directrices básicas. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Expresión '% expr% ': no hay decadencia de matriz a puntero. Consulte los límites de las [ C++ directrices básicas. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo GSL

[C26445 NO_SPAN_REF](c26445.md) Una referencia a `gsl::span` o `std::string_view` puede ser una indicación de un problema de duración.
Consulte [ C++ directrices básicas GSL. View: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) Prefiere usar `gsl::at()` en lugar de un operador de subíndice sin comprobar. Consulte [ C++ directrices básicas: Bounds. 4: no usar funciones y tipos de la biblioteca estándar que no estén comprobados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md) Considere la posibilidad de usar `gsl::finally` si la acción final está prevista. Consulte [ C++ directrices básicas: GSL. util: Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` o `std::string_view` creados a partir de un temporal no serán válidos cuando se invalide el temporal. Consulte [ C++ directrices básicas: GSL. View: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Advertencias en desuso

Las siguientes advertencias están presentes en un conjunto de reglas experimentales tempranas del comprobador de directrices básicas, pero ahora están en desuso y se pueden omitir de forma segura. Las advertencias se sustituyen por advertencias de la lista anterior.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Vea también
[Uso de C++ los comprobadores de directrices principales](using-the-cpp-core-guidelines-checkers.md)
