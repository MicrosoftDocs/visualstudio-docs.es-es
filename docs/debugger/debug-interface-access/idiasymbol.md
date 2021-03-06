---
title: IDiaSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c22e4b5d0fdb965cceb87fdff878c93b76e96b15
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738774"
---
# <a name="idiasymbol"></a>IDiaSymbol
Describe las propiedades de una instancia de símbolo.

## <a name="syntax"></a>Sintaxis

```
IDiaSymbol : IUnknown
```

## <a name="methods-in-alphabetical-order"></a>Métodos en orden alfabético
En la tabla siguiente se muestran los métodos de `IDiaSymbol`.

> [!NOTE]
> Los símbolos devolverán datos significativos solo para algunos de estos métodos, dependiendo del tipo de símbolo. Si un método devuelve `S_OK`, ese método ha devuelto datos significativos.

|Método|Descripción|
|------------|-----------------|
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Recupera todos los elementos secundarios del símbolo.|
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Recupera los elementos secundarios del símbolo. Este método es la versión extendida de [IDiaSymbol:: findchildren (](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Recupera los elementos secundarios del símbolo que son válidos en una dirección especificada.|
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Recupera los elementos secundarios del símbolo que son válidos en una dirección virtual relativa (RVA) especificada.|
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Recupera los elementos secundarios del símbolo que son válidos en una dirección virtual especificada.|
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección determinada.|
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección virtual relativa (RVA) especificada.|
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección virtual especificada (VA).|
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en este símbolo.|
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en este símbolo dentro del intervalo de direcciones especificado.|
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en este símbolo dentro de la dirección virtual relativa (RVA) especificada.|
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en este símbolo dentro de la dirección virtual especificada (VA).|
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de símbolos contenidos en esta función de código auxiliar en una dirección virtual relativa especificada.|
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Devuelve el número de etiquetas de puntero de acelerador en una C++ función de código auxiliar de amp.|
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Devuelve todos los valores de etiqueta de puntero de acelerador que corresponden a una C++ función de código auxiliar de acelerador amp.|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Recupera el modificador de acceso de un miembro de clase.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Recupera la parte de desplazamiento de una ubicación de direcciones.|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Recupera la parte de la sección de una ubicación de dirección.|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Recupera una marca que indica si otro símbolo hace referencia a esta dirección.|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Recupera el valor de edad de una base de datos de programa.|
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Recupera el identificador de símbolos del tipo de índice de matriz.|
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Recupera el identificador de tipo de índice de matriz del símbolo.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Recupera el número de versión principal de back-end.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Recupera el número de versión secundaria de back-end.|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Recupera el número de compilación de back-end.|
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Recupera el desplazamiento de datos base.|
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Recupera la ranura de datos base.|
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Recupera el símbolo del que se basa el puntero.|
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Recupera el identificador de símbolo desde el que se basa el puntero.|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Recupera la etiqueta de tipo de un tipo simple.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Recupera la posición de bit de una ubicación.|
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Recupera una clase integrada del tipo HLSL.|
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Devuelve un indicador de la Convención de llamada de un método.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Recupera una referencia a la clase primaria del símbolo.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Recupera el identificador primario de la clase del símbolo.|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Recupera una marca que indica si el símbolo hace referencia a una dirección de código.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Recupera una marca que indica si el símbolo fue generado por el compilador.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Recupera el nombre del compilador utilizado para crear la [compilación](../../debugger/debug-interface-access/compiland.md).|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene un constructor.|
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Recupera el símbolo contenedor de este símbolo.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es constante.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Recupera el número de elementos de una lista o una matriz.|
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Recupera el número de intervalos de direcciones válidos asociados al símbolo local.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Recupera una marca que indica si la función utiliza una Convención de llamada personalizada.|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Recupera los bytes de datos de un símbolo de OEM.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Recupera la clasificación de variables de un símbolo de datos.|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Recupera la marca que describe las características de edición y continuación del programa o unidad compilada.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Recupera una marca que indica si la función usa una devolución Far.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Recupera el número de versión principal de front-end.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Recupera el número de versión secundaria de front-end.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Recupera el número de compilación de front-end.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Recupera una marca que indica si el símbolo público hace referencia a una función.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Recupera el GUID del símbolo.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Recupera una marca que indica si la función contiene una llamada a `alloca`.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene definido algún operador de asignación.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene definidos operadores de conversión.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Recupera una marca que indica si la operación de compilación contiene información de depuración.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Recupera una marca que indica si la función tiene un C++controlador de excepciones de estilo.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Recupera una marca que indica si la función tiene un controlador de excepciones asincrónico.|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Recupera una marca que indica si la función tiene un ensamblado alineado.|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Recupera una marca que indica si la función contiene un comando longjmp (parte del control de excepciones de estilo C).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Recupera una marca que indica si el módulo contiene código administrado.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene definiciones de tipos anidadas.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Recupera una marca que indica si la función o la operación de compilación tiene comprobaciones de seguridad compiladas en (a través del modificador de compilador [/GS (comprobación de seguridad del búfer)](/cpp/build/reference/gs-buffer-security-check) ).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Recupera una marca que indica si la función tiene un control de excepciones estructurado de estilo Win32.|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Recupera una marca que indica si la función contiene un comando setjmp.|
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es una clase base virtual indirecta.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Recupera una marca que indica si la función se ha marcado con el atributo en línea.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Recupera una marca que indica si la función tiene un valor devuelto de la instrucción de interrupción.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Recupera una marca que indica si la función es la función virtual de clase base.|
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Recupera una marca que indica si el símbolo corresponde a una variable local compartida de grupo en el código compilado para C++ un acelerador de amp.|
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Recupera una marca que indica si el símbolo corresponde al símbolo de *intervalo de definición* para el componente de etiqueta de una variable de puntero en el código C++ compilado para un acelerador de amp. El símbolo de intervalo de definición es la ubicación de una variable para un intervalo de direcciones.|
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Indica si el símbolo corresponde a un símbolo de función de nivel superior para un sombreador compilado para un acelerador que corresponde a una llamada `parallel_for_each`.|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Recupera una marca que indica si los datos forman parte de un agregado de muchos símbolos.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Recupera una marca que indica si el archivo de símbolos contiene tipos de C.|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Recupera una marca que indica si el módulo se ha convertido del lenguaje intermedio común (CIL) a código nativo.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Recupera una marca que indica si los elementos de un tipo de datos definido por el usuario se alinean con un límite específico.|
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Especifica si este símbolo representa datos de lenguaje de sombreado de alto nivel (HLSL).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Recupera una marca que indica si el módulo se compiló con el modificador de compilador [/hotpatch (crear imagen una)](/cpp/build/reference/hotpatch-create-hotpatchable-image) .|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Recupera una marca que indica si la operación de compilación administrada se vinculó con el LTCG del vinculador.|
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Especifica si la matriz es una fila principal.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Recupera una marca que indica si la operación de compilación administrada es un. netmodule (que solo contiene metadatos).|
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Especifica si el puntero `this` apunta a un miembro de datos con herencia múltiple.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Recupera una marca que indica si la función tiene el atributo [naked](/cpp/cpp/naked-cpp) .|
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Especifica si la variable está optimizada.|
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Especifica si el puntero de `this` se basa en un valor de símbolo.|
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Especifica si este símbolo es un puntero a un miembro de datos.|
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Especifica si este símbolo es un puntero a una función miembro.|
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Especifica si la variable contiene un valor devuelto.|
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Especifica si el módulo se compila con la opción/SDL.|
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Especifica si el puntero `this` apunta a un miembro de datos con herencia única.|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Recupera una marca que indica si los datos se han dividido en un agregado de símbolos independientes.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Recupera una marca que indica si una función o una capa de código thunk es estática.|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Recupera una marca que indica si los símbolos privados se han quitado del archivo de símbolos.|
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Especifica si el puntero `this` apunta a un miembro de datos con herencia virtual.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Recupera el idioma del origen.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Recupera el número de bytes de memoria utilizados por el objeto representado por este símbolo.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Recupera una referencia al elemento primario léxico del símbolo.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Recupera el identificador primario léxico del símbolo.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Recupera el nombre de archivo de la biblioteca o del archivo objeto desde el que se cargó el objeto.|
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Devuelve la longitud del intervalo de direcciones en el que el símbolo local es válido.|
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Devuelve la parte de la sección del intervalo de direcciones de inicio en la que el símbolo local es válido.|
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Devuelve la parte de desplazamiento del intervalo de direcciones de inicio en el que el símbolo local es válido.|
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Devuelve el inicio del intervalo de direcciones en el que el símbolo local es válido.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Recupera el tipo de ubicación de un símbolo de datos.|
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Recupera el límite inferior de una dimensión de matriz FORTRAN.|
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Recupera el identificador de símbolos del límite inferior de una dimensión de la matriz FORTRAN.|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Recupera el tipo de la CPU de destino.|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Recupera una marca que indica si el símbolo hace referencia a código administrado.|
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Recupera el tipo de espacio de memoria.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Recupera una marca que indica si el símbolo hace referencia al código del lenguaje intermedio de Microsoft (MSIL).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Recupera el nombre del símbolo.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Recupera una marca que indica si el tipo de datos definido por el usuario está anidado.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Recupera una marca que indica si la función está marcada con el atributo [noinline](/cpp/cpp/noinline) .|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Recupera una marca que indica si la función se ha declarado con el atributo [Return](/cpp/cpp/noreturn) .|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Recupera una marca que indica si no se pudo realizar una ordenación de pila como parte de la comprobación del búfer de pila.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Recupera una marca que indica si la función o la etiqueta nunca se alcanza.|
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Devuelve el número de etiquetas de puntero de acelerador en una C++ función de código auxiliar de amp.|
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Recupera el número de modificadores que se aplican al tipo original.|
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Recupera el número de índices de registro.|
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Recupera el número de filas de la matriz.|
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Recupera el número de columnas de la matriz.|
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Recupera el nombre del archivo objeto.|
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Recupera el tipo del puntero de objeto para un método de clase.|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Recupera el valor de `oemId` del símbolo.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Recupera el valor de `oemSymbolId` del símbolo.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Recupera el desplazamiento de la ubicación del símbolo.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Recupera una marca que indica si la función o la etiqueta contiene código optimizado, así como información de depuración.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene operadores sobrecargados.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Recupera una marca que indica si el tipo de datos definido por el usuario está empaquetado.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Recupera el tipo de plataforma para el que se compiló el programa o la compilación.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Recupera una marca que indica si la función es virtual pura.|
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Recupera el rango de una matriz multidimensional de FORTRAN.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Recupera una marca que indica si un tipo de puntero es una referencia.|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Recupera el designador de registro de la ubicación.|
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Recupera el tipo de registro.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Recupera la dirección virtual relativa (RVA) de la ubicación.|
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Especifica si el puntero de `this` se marca como restringido.|
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Recupera la ranura de muestra.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Recupera una marca que indica si el tipo de datos definido por el usuario aparece en un ámbito léxico no global.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Recupera el valor de firma del símbolo.|
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Recupera el tamaño de un miembro de un tipo definido por el usuario.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Recupera el número de ranura de la ubicación.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Recupera el nombre de archivo del archivo de código fuente.|
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Recupera el archivo de código fuente y el número de línea que indican dónde se define un tipo definido por el usuario especificado.|
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Recupera el intervalo de la matriz o matriz muy progresada.|
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Recupera el subtipo.|
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Recupera el identificador del subtipo.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Recupera el nombre del archivo desde el que se cargaron los símbolos.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Recupera el identificador de símbolo único.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Recupera el clasificador de tipo de símbolo.|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Recupera la sección de desplazamiento de un destino de código thunk.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Recupera la dirección virtual relativa (RVA) de un destino de código thunk.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Recupera la sección de dirección de un destino de código thunk.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Recupera la dirección virtual (VA) de un destino de código thunk.|
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Recupera la ranura de textura.|
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Recupera el Ajustador de `this` lógico para el método.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Recupera el tipo de código thunk de una función.|
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Recupera la marca de tiempo del archivo ejecutable subyacente.|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Recupera el símbolo (token) de metadatos de una función o variable administrada.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Recupera una referencia a la firma de la función.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Recupera el identificador de tipo del símbolo.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Recupera una matriz de valores de tipo específicos del compilador para este símbolo.|
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Recupera una matriz de valores de identificador de tipo específicos del compilador para este símbolo.|
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Recupera la ranura UAV.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Recupera la variedad de un tipo definido por el usuario (UDT).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario no está alineado.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Recupera el nombre no representativo de C++ un nombre representativo o de vinculación.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Extensión del método `get_undecoratedName` que recupera el nombre no representativo basándose en el valor de un campo de extensión.|
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Recupera el identificador del tipo original (sin modificar).|
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Recupera el límite superior de una dimensión de matriz FORTRAN.|
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Recupera el identificador de símbolo del límite superior de una dimensión de matriz FORTRAN.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Recupera el valor de una constante.|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Recupera una marca que indica si la función es virtual.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Recupera la dirección virtual (VA) de la ubicación.|
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es una clase base virtual.|
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Recupera el índice de la tabla de desplazamiento base virtual.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Recupera el desplazamiento en la tabla de función virtual de una función virtual.|
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Recupera el desplazamiento del puntero base virtual.|
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Recupera el tipo de un puntero de tabla base virtual.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Recupera la interfaz de símbolos del tipo de la tabla virtual para un tipo definido por el usuario.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Recupera el identificador de la forma de la tabla virtual del símbolo.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es volatile.|

## <a name="remarks"></a>Comentarios

## <a name="notes-for-callers"></a>Notas para llamadores
Obtenga esta interfaz mediante una llamada a uno de los métodos siguientes:

- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)

- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)

- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)

- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)

- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)

- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)

- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)

- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)

- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo mostrar las variables locales de una función en una dirección virtual relativa determinada. También muestra cómo se relacionan entre sí los símbolos de tipos diferentes.

> [!NOTE]
> `CDiaBSTR` es una clase que contiene un `BSTR` y controla automáticamente la liberación de la cadena cuando la creación de instancias sale del ámbito.

```C++
void DumpLocalVars( DWORD rva, IDiaSession *pSession )
{
    CComPtr< IDiaSymbol > pBlock;
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )
    {
        Fatal( "Failed to find symbols by RVA" );
    }
    CComPtr< IDiaSymbol > pscope;
    for ( ; pBlock != NULL; )
    {
        CComPtr< IDiaEnumSymbols > pEnum;
        // local data search
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )
        {
            Fatal( "Local scope findChildren failed" );
        }
        CComPtr< IDiaSymbol > pSymbol;
        DWORD tag;
        DWORD celt;
        while ( pEnum != NULL &&
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1)
        {
            pSymbol->get_symTag( &tag );
            if ( tag == SymTagData )
            {
                CDiaBSTR name;
                DWORD    kind;
                pSymbol->get_name( &name );
                pSymbol->get_dataKind( &kind );
                if ( name != NULL )
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );
            }
            else if ( tag == SymTagAnnotation )
            {
                CComPtr< IDiaEnumSymbols > pValues;
                // local data search
                wprintf_s( L"\tAnnotation:\n" );
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )
                    Fatal( "Annotation findChildren failed" );
                pSymbol = NULL;
                while ( pValues != NULL &&
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&
                        celt == 1 )
                {
                    CComVariant value;
                    if ( pSymbol->get_value( &value ) != S_OK )
                        Fatal( "No value for annotation data." );
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );
                    pSymbol = NULL;
                }
            }
            pSymbol = NULL;
        }
        pBlock->get_symTag( &tag );
        if ( tag == SymTagFunction )    // stop when at function scope
            break;
        // move to lexical parent
        CComPtr< IDiaSymbol > pParent;
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )
            && pParent != NULL ) {
            pBlock = pParent;
        }
        else
        {
            Fatal( "Finding lexical parent failed." );
        }
    };
}
```

## <a name="requirements"></a>Requisitos
`Header:` Dia2.h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Compiland](../../debugger/debug-interface-access/compiland.md)
