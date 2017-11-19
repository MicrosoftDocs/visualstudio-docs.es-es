---
title: "Referencia de Comprobador de directrices de núcleo de C++ de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a129fcc5cfabb46dfa545d7f70e291b121ee5353
ms.sourcegitcommit: 24f81b8fb59722cf4a856005227f6a29bb2990cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="c-core-guidelines-checker-reference"></a>Referencia de Comprobador de instrucciones de C++ principal
Esta sección enumeran las advertencias del corrector de instrucciones de C++ Core. Para obtener información sobre el análisis de código, vea [/ANALYZE (análisis de código)](/cpp/build/reference/analyze-code-analysis) y [inicio rápido: análisis de código para C/C ++](../code-quality/quick-start-code-analysis-for-c-cpp.md).  
  
**Tenga en cuenta**: algunas advertencias pertenecen a más de un grupo y no todas las advertencias tienen un tema de referencia.

## <a name="ownerpointer-group"></a>Grupo de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  Devuelve un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  Restablecer o eliminar explícitamente un propietario\<T > puntero '% variable %'. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  No elimine un propietario\<T > que puede estar en estado no válido. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  No se asignan a un propietario\<T > que puede estar en estado válido. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  No asigna un puntero sin formato a un propietario\<T >. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  Prefieren los objetos con ámbito, no montón-asignar innecesariamente. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  

[C26429 USE_NOTNULL](C26429.md)  
  Para nullness nunca se prueba el símbolo '% símbolo %', se puede marcar como not_null. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  El símbolo '% símbolo %' no está probado para nullness en todas las rutas. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  El tipo de expresión '% expr %' ya está gsl::not_null. No comprobar su nullness. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

## <a name="rawpointer-group"></a>Grupo de RAW_POINTER
 
[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
No asigne el resultado de una asignación o una llamada de función con un propietario\<T > valor devuelto a un puntero sin formato, use propietario<T> en su lugar. Vea [C++ Core directrices I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
No elimine un puntero sin formato que no es un propietario\<T >. Vea [C++ Core directrices I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   devolver un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Vea [C++ Core directrices R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Evitar funciones malloc() y free(), prefiere la versión nothrow de nuevo con la opción Eliminar. Vea [C++ Core directrices R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  Evitar llamar a new y eliminar de forma explícita, use std::make_unique\<T > en su lugar. Vea [C++ Core directrices R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).  

[C26429 USE_NOTNULL](C26429.md)  
  Para nullness nunca se prueba el símbolo '% símbolo %', se puede marcar como not_null. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  El símbolo '% símbolo %' no está probado para nullness en todas las rutas. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  El tipo de expresión '% expr %' ya está gsl::not_null. No comprobar su nullness. Vea [C++ Core directrices F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  No utilice aritmética de punteros. Utilice en su lugar el intervalo. Vea [Bounds.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  La expresión '% expr %': ninguna matriz de decadencia de puntero. Vea [Bounds.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

## <a name="uniquepointer-group"></a>Grupo de UNIQUE_POINTER
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  El parámetro '% parámetro %' es una referencia a `const` puntero único, utilice const T * o const T & en su lugar. Vea [C++ Core directrices R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  El parámetro '% parámetro %' es una referencia al puntero único y nunca se reasigna o se restablece, use T * o T & en su lugar. Vea [C++ Core directrices R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Parámetro de puntero inteligente '% símbolo %' sólo se utiliza para el puntero de acceso al contenido. Usar T * o T & en su lugar. Vea [C++ Core directrices R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  

## <a name="sharedpointer-group"></a>Grupo de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Mover, copiar, reasignar o restablecer un puntero inteligente local '% símbolo %'. Vea [C++ Core directrices R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Parámetro de puntero inteligente '% símbolo %' sólo se utiliza para el puntero de acceso al contenido. Usar T * o T & en su lugar. Vea [C++ Core directrices R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  Parámetro de puntero compartido '% símbolo %' se pasa por referencia rvalue. Pasar por valor en su lugar. Vea [C++ Core directrices R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  Parámetro de puntero compartido '% símbolo %' se pasa por referencia y no restablecer o vuelve a asignar. Usar T * o T & en su lugar. Vea [C++ Core directrices R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  Parámetro de puntero compartido '% símbolo %' no es copiar o mover. Usar T * o T & en su lugar. Vea [C++ Core directrices R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).  

## <a name="declaration-group"></a>Grupo de declaración
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  Inicializador global llama a una función no sea constexpr '% símbolo %'. Vea [C++ Core directrices I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  Inicializador global tiene acceso a objetos de extern '% símbolo %'. Vea [C++ Core directrices I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
## <a name="class-group"></a>CLASE de grupo
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  Si define o eliminar cualquier operación de forma predeterminada en el tipo '% símbolo %', definir o elimínelos todos. Vea [C++ Core directrices C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).  
  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  Función '% symbol_1% ' oculta una función no virtual '% symbol_2% '. Vea [C++ Core directrices C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).  
  
[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  El tipo '% símbolo %' con una función virtual necesita cualquier destructor no virtual público virtual o protegido. Vea [C++ Core directrices C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).  

## <a name="type-group"></a>TIPO de grupo
    
[C26437 DONT_SLICE](C26437.md)  
  No la segmentación. Vea [C++ Core directrices ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).  

## <a name="style-group"></a>Grupo de estilos  
[C26438 NO_GOTO](C26438.md)  
  Evitar `goto`. Vea [C++ Core directrices ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).  
  
## <a name="function-group"></a>Grupo de funciones
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  Este tipo de función no puede iniciar. Declara `noexcept`. Vea [C++ Core directrices F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  Función '% símbolo %' puede declararse `noexcept`. Vea [C++ Core directrices F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDAD
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 Se deben denominar objetos de protección. Vea [C++ principales directrices cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).  

## <a name="const-group"></a>Grupo CONST
    
C26460 USE_CONST_REFERENCE_ARGUMENTS:  
  El argumento de referencia '% argumento %' para la función '% función %' puede marcarse como `const`. Vea [C++ principales directrices con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26461 USE_CONST_POINTER_ARGUMENTS: el argumento de puntero '% argumento %' para la función '% función %' puede marcarse como un puntero a `const`. Vea [C++ principales directrices con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE:  
  El valor al que apunta a '% variable %' se asigna una sola vez, marque como un puntero a `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26463 USE_CONST_FOR_ELEMENTS:  
  Los elementos de matriz '% de matriz' se asignan elementos de la marca de una sola vez, `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS:  
  Se asignan los valores que apunta a los elementos de matriz '% matriz %' solo una vez, elementos de la marca como puntero a `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  

C26496 USE_CONST_FOR_VARIABLE:  
  La variable '% variable %' está asignada una sola vez, márquelo como `const`. Vea [C++ principales directrices con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION:  
  Esta función de función % podría marcarse `constexpr` si se desea la evaluación en tiempo de compilación. Vea [C++ Core directrices F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL:  
  Puede usar esta función función llamada % `constexpr` si se desea la evaluación en tiempo de compilación. Vea [C++ principales directrices con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).  

## <a name="type-group"></a>TIPO de grupo
C26465 NO_CONST_CAST_UNNECESSARY:  
  No utilice `const_cast` para desechar `const`. `const_cast`no es necesario; no se está quitando constness o volatilidad por esta conversión. Vea [Type.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC:  
  No utilice `static_cast` las conversiones de restricción. Una conversión de un tipo polimórfico debe usar dynamic_cast. Vea [Type.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR:  
  No use `reinterpret_cast`. Puede usar una conversión de void * `static_cast`. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  No use un `static_cast` para conversiones aritméticas. Use la inicialización de llave, gsl::narrow_cast o gsl::narow. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  No convertir entre tipos de puntero cuando el tipo de origen y el tipo de destino son iguales. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  No convertir entre tipos de puntero cuando la conversión podría ser implícita. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  No realice conversiones de C de estilo de función. Vea [C++ Core directrices ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).  
     
C26490 NO_REINTERPRET_CAST:  
  No use `reinterpret_cast`. Vea [Type.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26491 NO_STATIC_DOWNCAST:  
  No utilice `static_cast` las conversiones de restricción. Vea [Type.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26492 NO_CONST_CAST:  
  No utilice `const_cast` para desechar `const`. Vea [Type.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
    
C26493 NO_CSTYLE_CAST:  
  No usar conversiones de estilo C. Vea [Type.4 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type). 
     
C26494 VAR_USE_BEFORE_INIT:  
  La variable '% variable %' no está inicializada. Siempre inicializar un objeto. Vea [Type.5 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26495 MEMBER_UNINIT:  
  La variable '% variable %' no está inicializada. Siempre inicializar una variable de miembro. Vea [Type.6 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
## <a name="bounds-group"></a>Grupo de límites

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  No utilice aritmética de punteros. Utilice en su lugar el intervalo. Vea [Bounds.1 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING:  
  Solo el índice de matrices mediante expresiones constantes. Vea [Bounds.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26483 STATIC_INDEX_OUT_OF_RANGE:  
  Valor de % de valor está fuera de los límites (0, enlazadas %) de la variable '% variable %'. Solo el índice de matrices mediante expresiones constantes que están dentro de los límites de la matriz. Vea [Bounds.2 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  La expresión '% expr %': ninguna matriz de decadencia de puntero. Vea [Bounds.3 de instrucciones de C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
## <a name="see-also"></a>Vea también  
[Usar los comprobadores de directrices de núcleo de C++](using-the-cpp-core-guidelines-checkers.md)
