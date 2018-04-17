---
title: Referencia de Comprobador de directrices de núcleo de C++ de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f0b657781981b6204bda42fcbf18f8945fb59004
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="c-core-guidelines-checker-reference"></a>Referencia de Comprobador de instrucciones de C++ principal

Esta sección enumeran las advertencias del corrector de instrucciones de C++ Core. Para obtener información sobre el análisis de código, vea [/ANALYZE (análisis de código)](/cpp/build/reference/analyze-code-analysis) y [inicio rápido: análisis de código para C/C ++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Algunas advertencias pertenecen a más de un grupo, y no todas las advertencias tienen un tema de referencia completa.

## <a name="ownerpointer-group"></a>Grupo de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) devolver un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) restablecer o elimínela explícitamente un propietario\<T > puntero '% variable %'. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) no elimine un propietario\<T > que puede estar en estado no válido. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) no se asignan a un propietario\<T > que puede estar en estado válido. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) no asigna un puntero sin formato a un propietario\<T >. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) prefieren los objetos con ámbito, no montón-asignar innecesariamente. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) para nullness nunca se prueba el símbolo '% símbolo %', se puede marcar como not_null. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) no se ha comprobado el símbolo '% símbolo %' para nullness en todas las rutas. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) el tipo de expresión '% expr %' ya está gsl::not_null. No comprobar su nullness. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>Grupo de RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) no asigna el resultado de una asignación o una llamada de función con un propietario\<T > devuelve el valor a un puntero sin formato, use propietario\<T > en su lugar. Vea [C++ Core directrices I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) no elimine un puntero sin formato que no es un propietario\<T >. Vea [C++ Core directrices I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   devolver un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) evitar funciones malloc() y free(), prefiere la versión nothrow de nuevo con la opción Eliminar. Vea [C++ Core directrices R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) evitar llamar a new y eliminar de forma explícita, use std::make_unique\<T > en su lugar. Vea [C++ Core directrices R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) para nullness nunca se prueba el símbolo '% símbolo %', se puede marcar como not_null. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) no se ha comprobado el símbolo '% símbolo %' para nullness en todas las rutas. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) el tipo de expresión '% expr %' ya está gsl::not_null. No comprobar su nullness. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) no utilizan aritmética de punteros. Utilice en su lugar el intervalo. Vea [Bounds.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
La expresión '% expr %': ninguna matriz de decadencia de puntero. Vea [Bounds.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>Grupo de UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) el parámetro '% parámetro %' es una referencia a `const` puntero único, utilice const T * o const T & en su lugar. Vea [C++ Core directrices R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) el parámetro '% parámetro %' es una referencia al puntero único y nunca se reasigna o se restablece, use T * o T & en su lugar. Vea [C++ Core directrices R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parámetro de puntero inteligente '% símbolo %' solo se utiliza para tener acceso a contenido puntero. Usar T * o T & en su lugar. Vea [C++ Core directrices R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>Grupo de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parámetro de puntero inteligente '% símbolo %' solo se utiliza para tener acceso a contenido puntero. Usar T * o T & en su lugar. Vea [C++ Core directrices R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parámetro de puntero compartido '% símbolo %' se pasa por referencia rvalue. Pasar por valor en su lugar. Vea [C++ Core directrices R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parámetro de puntero compartido '% símbolo %' se pasa por referencia y no restablecer o vuelve a asignar. Usar T * o T & en su lugar. Vea [C++ Core directrices R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parámetro de puntero compartido '% símbolo %' no se copian o se mueven. Usar T * o T & en su lugar. Vea [C++ Core directrices R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Grupo de declaración

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) Global inicializador llama a una función no sea constexpr '% símbolo %'. Vea [C++ Core directrices I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inicializador Global tiene acceso a objetos de extern '% símbolo %'. Vea [C++ Core directrices I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) evitar sin nombre objetos con personalizado construcción y destrucción. Vea [ES.84: no (intente) declara una variable local sin nombre](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>CLASE de grupo

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) si define o eliminar cualquier operación de forma predeterminada en el tipo '% símbolo %', definir o elimínelos todos. Vea [C++ Core directrices C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) función '% símbolo %' debe marcarse con 'override'. Vea [C.128: funciones virtuales deben especificar exactamente uno de reemplazo virtual, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) función '% symbol_1% ' oculta una función no virtual '% symbol_2% '. Vea [C++ Core directrices C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) función '% símbolo %' debe especificar exactamente uno de 'virtual', 'override' o 'final'. Vea [C.128: funciones virtuales deben especificar exactamente uno de reemplazo virtual, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) el tipo '% símbolo %' con una función virtual necesita cualquier destructor no virtual público virtual o protegido. Vea [C++ Core directrices C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) reemplazando destructor no debe utilizar explícita 'override' o 'virtuales' especificadores. Vea [C.128: funciones virtuales deben especificar exactamente uno de reemplazo virtual, o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>TIPO de grupo

[C26437 DONT_SLICE](C26437.md) no segmentar. Vea [C++ Core directrices ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Grupo de estilos

[C26438 NO_GOTO](C26438.md) evitar `goto`. Vea [C++ Core directrices ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funciones

[C26439 SPECIAL_NOEXCEPT](C26439.md) este tipo de función no puede iniciar. Declara `noexcept`. Vea [C++ Core directrices F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) función '% símbolo %' puede declararse `noexcept`. Vea [C++ Core directrices F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) se declara la función **noexcept** , pero llama a una función que puede producir excepciones.
Vea [directrices de núcleo de C++: F.6: si la función no puede iniciar, declárelo noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDAD

[C26441 NO_UNNAMED_GUARDS](C26441.md) objetos de protección deben tener un nombre. Vea [C++ principales directrices cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Grupo CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) el argumento de referencia '% argumento %' para la función '% función %' puede marcarse como `const`. Vea [C++ principales directrices con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): el argumento de puntero '% argumento %' para la función '% función %' puede marcarse como un puntero a `const`. Vea [C++ principales directrices con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) el valor al que apunta a '% variable %' se asigna una sola vez, marque como un puntero a `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) los elementos de matriz '% de matriz' se asignan elementos de la marca de una sola vez, `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) se asignan los valores que apunta a los elementos de matriz '% matriz %' solo una vez, elementos de la marca como puntero a `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) la variable '% variable %' está asignada una sola vez, márquelo como `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) podría marcarse esta función de función % `constexpr` si se desea la evaluación en tiempo de compilación. Vea [C++ Core directrices F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) puede utilizar esta función función llamada % `constexpr` si se desea la evaluación en tiempo de compilación. Vea [C++ principales directrices con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO de grupo

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) no utilice `const_cast` para desechar `const`. `const_cast` no es necesario; no se está quitando constness o volatilidad por esta conversión. Vea [Type.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) no utilice `static_cast` las conversiones de restricción. Una conversión de un tipo polimórfico debe usar dynamic_cast. Vea [Type.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) no use `reinterpret_cast`. Puede usar una conversión de void * `static_cast`. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) no use un `static_cast` para conversiones aritméticas. Use la inicialización de llave, gsl::narrow_cast o gsl::narow. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) no convertir entre tipos de puntero cuando el tipo de origen y el tipo de destino son iguales. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) no convertir entre tipos de puntero cuando la conversión podría ser implícita. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) no usar conversiones de C de estilo de función. Vea [C++ Core directrices ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).
 
[C26490 NO_REINTERPRET_CAST](c26490.md) no use `reinterpret_cast`. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) no utilice `static_cast` las conversiones de restricción. Vea [Type.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) no utilice `const_cast` para desechar `const`. Vea [Type.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) no usar conversiones de estilo C. Vea [Type.4 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).
 
[C26494 VAR_USE_BEFORE_INIT](c26494.md) Variable '% variable %' no está inicializado. Siempre inicializar un objeto. Vea [Type.5 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Variable '% variable %' no está inicializado. Siempre inicializar una variable de miembro. Vea [Type.6 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de límites

[C26446 USE_GSL_AT](c26446.md) prefieren usar `gsl::at()` en lugar del operador de subíndice no está activada. Vea [directrices de núcleo de C++: Bounds.4: no utilizar funciones de la biblioteca estándar y los tipos que no son límites comprueban](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
No utilice aritmética de punteros. Utilice en su lugar el intervalo. Vea [Bounds.1 de directrices de núcleo de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) índice solo en matrices mediante expresiones constantes. Vea [Bounds.2 de directrices de núcleo de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valor % value % está fuera de los límites (0, enlazadas %) de la variable '% variable %'. Solo el índice de matrices mediante expresiones constantes que están dentro de los límites de la matriz. Vea [Bounds.2 de directrices de núcleo de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) expresión '% expr %': ninguna matriz de decadencia de puntero. Vea [Bounds.3 de directrices de núcleo de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo de GSL

[C26445 NO_SPAN_REF](c26445.md) una referencia a `gsl::span` o `std::string_view` puede ser indicativo de un problema de duración.
Vea [GSL.view de directrices de núcleo de C++: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) prefieren usar `gsl::at()` en lugar del operador de subíndice no está activada. Vea [directrices de núcleo de C++: Bounds.4: no utilizar funciones de la biblioteca estándar y los tipos que no son límites comprueban](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) considere la posibilidad de usar `gsl::finally` si se prevé la acción final. Vea [directrices centrales de C++: GSL.util: utilidades](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` o `std::string_view` creado a partir de un archivo temporal se considerarán no válidos cuando se invalida la contraseña. Vea [directrices centrales de C++: GSL.view: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Advertencias en desuso

Las advertencias siguientes están presentes en un conjunto de reglas experimental temprano del corrector directrices de núcleo, pero están en desuso y pueden omitirse. Las advertencias tienen prioridad las advertencias de la lista anterior.

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
[Usar los comprobadores de directrices de núcleo de C++](using-the-cpp-core-guidelines-checkers.md)
