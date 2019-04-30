---
title: Referencia de C++ Core Guidelines Comprobador
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 0b725d0ee49590062ebdde9a1ef27f838678ccf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540799"
---
# <a name="c-core-guidelines-checker-reference"></a>Referencia de C++ Core Guidelines Comprobador

Esta sección enumeran las advertencias del Comprobador de C++ Core Guidelines. Para obtener información sobre el análisis de código, vea [/ analyze (análisis de código)](/cpp/build/reference/analyze-code-analysis) y [inicio rápido: Análisis de código para C/C ++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Algunas advertencias que pertenecen a más de un grupo, y no todas las advertencias tienen un tema de referencia completa.

## <a name="ownerpointer-group"></a>Grupo OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) devuelve un objeto de ámbito en lugar de uno asignado por montón si tiene un constructor de movimiento. Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) restablece o elimina explícitamente un elemento owner\<T > puntero "% variable %". Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) no se elimina un elemento owner\<T > que puede estar en estado no válido. Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) no se asigna a un propietario\<T > que puede estar en estado válido. Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) no asigna un puntero sin formato a un propietario\<T >. Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferibles los objetos de ámbito, no montón innecesariamente. Consulte [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) símbolo '% símbolo %' nunca se prueba para obtener su valor null, se puede marcar como not_null. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) símbolo '% símbolo %' no está probado valores NULL en todas las rutas. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) el tipo de expresión '% expr %' ya es gsl:: Not_Null. No se debe probar valores NULL. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>Grupo RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) no asigna el resultado de una llamada de función o una asignación con un propietario\<T > devuelve el valor a un puntero sin formato, use propietario\<T > en su lugar. Consulte [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) no elimine un puntero sin formato que no sea propietaria\<T >. Consulte [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   devuelve un objeto de ámbito en lugar de uno asignado por montón si tiene un constructor de movimiento. Consulte [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) evita usar malloc() y free(), prefiere la versión nothrow de new con delete. Consulte [C++ Core Guidelines R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) evitar llamar a new y delete de forma explícita, use std:: make_unique\<T > en su lugar. Consulte [C++ Core Guidelines R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) símbolo '% símbolo %' nunca se prueba para obtener su valor null, se puede marcar como not_null. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) símbolo '% símbolo %' no está probado valores NULL en todas las rutas. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) el tipo de expresión '% expr %' ya es gsl:: Not_Null. No se debe probar valores NULL. Consulte [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) no usar aritmética de puntero. Use el intervalo en su lugar. Consulte [C++ Core Guidelines Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Expresión "% expr %": Ninguna matriz de decadencia de puntero. Consulte [C++ Core Guidelines Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>Grupo UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) el parámetro "% parámetro %" es una referencia a `const` puntero único, use const T * o const T & en su lugar. Consulte [C++ Core Guidelines R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) el parámetro "% parámetro %" es una referencia a un puntero único y nunca se reasigna ni se restablece, use T * o T & en su lugar. Consulte [C++ Core Guidelines R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Consulte [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parámetro de puntero inteligente '% símbolo %' solo se utiliza para tener acceso a contenidos puntero. Use T * o T & en su lugar. Consulte [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>Grupo SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Consulte [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parámetro de puntero inteligente '% símbolo %' solo se utiliza para tener acceso a contenidos puntero. Use T * o T & en su lugar. Consulte [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parámetro de puntero compartido "% símbolo %" se pasa por referencia rvalue. Pasar por valor en su lugar. Consulte [C++ Core Guidelines R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parámetro de puntero compartido "% símbolo %" se pasa por referencia y no restablecer o reasignado. Use T * o T & en su lugar. Consulte [C++ Core Guidelines R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parámetro de puntero compartido "% símbolo %" no se ha copiado o movido. Use T * o T & en su lugar. Consulte [C++ Core Guidelines R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DECLARACIÓN de grupo

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) inicializador Global llama a una función que no sea constexpr '% símbolo %'. Consulte [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inicializador Global accede a un objeto externo '% símbolo %'. Consulte [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) evite sin nombre objetos con personalizado construcción y destrucción. Consulte [ES.84: No (intente) declara una variable local sin nombre](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>CLASE de grupo

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) si se define o elimina cualquier operación predeterminada en el tipo '% símbolo %', definir o eliminar todos ellos. Consulte [C++ Core Guidelines C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) función "% símbolo %" se debe marcar con "override". Consulte [C.128: Funciones virtuales deben especificar exactamente uno de virtual, invalidación, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) función '% symbol_1% ' oculta una función no virtual '% symbol_2% '. Consulte [C++ Core Guidelines C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) función '% símbolo %' debe especificar exactamente uno de 'virtual', 'override' o 'final'. Consulte [C.128: Funciones virtuales deben especificar exactamente uno de virtual, invalidación, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md) el tipo '% símbolo %' con una función virtual necesita cualquier destructor no virtual público virtual o protegido. Consulte [C++ Core Guidelines C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) no debe utilizar el destructor de invalidación explícita 'override' o 'virtuales' especificadores. Consulte [C.128: Funciones virtuales deben especificar exactamente uno de virtual, invalidación, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>TIPO de grupo

[C26437 DONT_SLICE](C26437.md) no debe segmentarse. Consulte [C++ Core Guidelines ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>ESTILO de grupo

[C26438 NO_GOTO](C26438.md) evitar `goto`. Consulte [C++ Core Guidelines ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funciones

[C26439 SPECIAL_NOEXCEPT](C26439.md) no puede iniciar este tipo de función. Declárela `noexcept`. Consulte [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) se puede declarar la función '% símbolo %' `noexcept`. Consulte [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) se declara la función **noexcept** pero llama a una función que puede generar excepciones.
Consulte [directrices principales de C++:  F.6: Si la función no puede iniciar, declarar noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDAD

[C26441 NO_UNNAMED_GUARDS](C26441.md) se deben denominar los objetos de restricción. Consulte [C++ Core Guidelines cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Grupo CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) el argumento de referencia '% argumento %' para la función "% función %" se puede marcar como `const`. Consulte [C++ Core Guidelines con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): El argumento de puntero '% argumento %' para la función '% función %' puede marcarse como puntero a `const`. Consulte [C++ Core Guidelines con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) el valor señalado por "% variable %" se asigna solo una vez, debe marcarse como puntero a `const`. Consulte [C++ Core Guidelines con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) los elementos de matriz "% matriz %" se asignan solo una vez, marque los elementos `const`. Consulte [C++ Core Guidelines con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) se asignan los valores que apunta a elementos de matriz '% matriz %' en una sola vez, marque los elementos como puntero a `const`. Consulte [C++ Core Guidelines con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) la variable "% variable %" se asigna solo una vez, debe marcarse como `const`. Consulte [C++ Core Guidelines con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) puede marcarse como esta función de función % `constexpr` si se desea la evaluación en tiempo de compilación. Consulte [C++ Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) puede usar esta función función llamada % `constexpr` si se desea la evaluación en tiempo de compilación. Consulte [C++ Core Guidelines con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO de grupo

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) no use `const_cast` para desechar `const`. `const_cast` no es necesario; no se está quitando declaración o volatilidad esta conversión. Consulte [C++ Core Guidelines tipo.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) no use `static_cast` conversiones a tipo heredado. Una conversión de un tipo polimórfico debe usar dynamic_cast. Consulte [C++ Core Guidelines Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) no use `reinterpret_cast`. Puede usar una conversión de void * `static_cast`. Consulte [C++ Core Guidelines Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) no use un `static_cast` para conversiones aritméticas. Utilice llaves, gsl:: narrow_cast o gsl:: narow. Consulte [C++ Core Guidelines Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) no se debe convertir entre tipos de puntero, donde el tipo de origen y el tipo de destino son iguales. Consulte [C++ Core Guidelines Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) no se debe convertir entre tipos de puntero cuando la conversión puede ser implícita. Consulte [C++ Core Guidelines Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) no usar conversiones de C de estilo de función. Consulte [C++ Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) no use `reinterpret_cast`. Consulte [C++ Core Guidelines Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) no use `static_cast` conversiones a tipo heredado. Consulte [C++ Core Guidelines Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) no use `const_cast` para desechar `const`. Consulte [C++ Core Guidelines tipo.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) no usar conversiones de estilo C. Consulte [C++ Core Guidelines Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Variable "% variable %" no está inicializada. Siempre debe inicializarse un objeto. Consulte [C++ Core Guidelines Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Variable "% variable %" no está inicializada. Siempre debe inicializarse una variable de miembro. Consulte [C++ Core Guidelines Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de límites

[C26446 USE_GSL_AT](c26446.md) prefieren usar `gsl::at()` en lugar del operador de subíndice unchecked. Consulte [directrices principales de C++:  Bounds.4: No use la biblioteca estándar de funciones y tipos que no son límites](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
No usar aritmética de puntero. Use el intervalo en su lugar. Consulte [Bounds.1 de C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) indizar solo las matrices usa expresiones constantes. Consulte [Bounds.2 de C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valor % value % está fuera de los límites (0, % dependiente %) de la variable "% variable %". Solo el índice de las matrices usa expresiones constantes en los límites de la matriz. Consulte [Bounds.2 de C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) expresión "% expr %": Ninguna matriz de decadencia de puntero. Consulte [Bounds.3 de C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo de GSL

[C26445 NO_SPAN_REF](c26445.md) una referencia a `gsl::span` o `std::string_view` puede ser un indicio de un problema de duración.
Consulte [C++ Core Guidelines GSL.view: Vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) prefieren usar `gsl::at()` en lugar del operador de subíndice unchecked. Consulte [directrices principales de C++:  Bounds.4: No use la biblioteca estándar de funciones y tipos que no son límites](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md) considere el uso `gsl::finally` si está destinada la acción final. Consulte [directrices principales de C++:  GSL.util: Utilidades](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` o `std::string_view` creado a partir de un archivo temporal se consideran no válidos cuando se invalida temporal. Consulte [directrices principales de C++: GSL.view: Vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Advertencias en desuso

Las siguientes advertencias están presentes en un conjunto de reglas experimental temprana del corrector instrucciones de núcleo, pero están en desuso y pueden omitirse. Las advertencias tienen prioridad las advertencias de la lista anterior.

- DEREF_INVALID_POINTER 26412
- DEREF_NULLPTR 26413
- ASSIGN_NONOWNER_TO_EXPLICIT_OWNER 26420
- ASSIGN_VALID_OWNER 26421
- VALID_OWNER_LEAVING_SCOPE 26422
- ALLOCATION_NOT_ASSIGNED_TO_OWNER 26423
- VALID_ALLOCATION_LEAVING_SCOPE 26424
- ASSIGNING_TO_STATIC 26425
- NO_LIFETIME_TRACKING 26499

## <a name="see-also"></a>Vea también
[Usar los comprobadores de C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
