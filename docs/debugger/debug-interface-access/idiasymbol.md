---
title: "IDiaSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol (interfaz)"
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# IDiaSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Describe las propiedades de una instancia del símbolo.  
  
## Sintaxis  
  
```  
IDiaSymbol : IUnknown  
```  
  
## Métodos en orden alfabético  
 La tabla siguiente se muestran los métodos de `IDiaSymbol`.  
  
> [!NOTE]
>  Los símbolos devolverán datos significativos para solo algunos de estos métodos, dependiendo del tipo de token.  Si un método devuelve `S_OK`, ese método devolvió datos significativos.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Recupera todos los elementos secundarios del símbolo.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Recupera los elementos secundarios de símbolos.  Este método es la versión extendida de [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Recupera los elementos secundarios de símbolos que son válidos en una dirección especificada.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Recupera los elementos secundarios de símbolos que son válidos en una dirección relativa virtual especificada \(RVA\).|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Recupera los elementos secundarios de símbolos que son válidos en una dirección virtual especificada.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección especificada.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección relativa virtual especificada \(RVA\).|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección virtual especificada \(VA\).|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, en este símbolo.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, en este símbolo dentro del intervalo de direcciones especificado.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, en este símbolo dentro de la dirección virtual relativa especificada \(RVA\).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, en este símbolo dentro de la dirección virtual especificada \(VA\).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de los símbolos incluidos en esta función de código auxiliar en una dirección relativa virtual especificada.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Devuelve el número de etiquetas de puntero de aceleradores en la función de código auxiliar de AMP en cuestión.|  
|[IDiaSymbol::get\_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Devuelve todos los valores de etiqueta de puntero de aceleradores que corresponden a la función de código auxiliar de aceleradores de AMP en cuestión.|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Recupera el modificador de acceso de un miembro de clase.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Recupera el desplazamiento de una ubicación de dirección.|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Recupera la parte de la sección de una ubicación de dirección.|  
|[IDiaSymbol::get\_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Recupera una marca que indica si otro símbolo hace referencia a esta dirección.|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Recupera el valor de la edad de una base de datos de programa.|  
|[IDiaSymbol::get\_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Recupera el identificador del tipo de índice de matriz.|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Recupera el identificador del tipo de índice de matriz de símbolos.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Recupera el número de versión principal back\-end.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Recupera el número de versión secundaria del servidor.|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Recupera el número de compilación back\-end.|  
|[IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Recupera el desplazamiento base de datos.|  
|[IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Recupera la ranura base de datos.|  
|[IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Recupera el símbolo de que se basa el puntero.|  
|[IDiaSymbol::get\_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Recupera el id. del token del que se basa el puntero.|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Recupera el tipo de un tipo simple.|  
|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Recupera la posición de bit de una ubicación.|  
|[IDiaSymbol::get\_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Recupera una clase integrada del tipo de HLSL.|  
|[IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Devuelve un indicador de la convención de llamada de un método.|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Recupera una referencia al elemento primario de la clase de símbolos.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Recupera el identificador primario de la clase de símbolos.|  
|[IDiaSymbol::get\_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Recupera una marca que indica si el token hace referencia a un código de dirección.|  
|[IDiaSymbol::get\_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Recupera una marca que indica si el token compilador\- se generó.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Recupera el nombre del compilador utilizado para crear [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene un constructor.|  
|[IDiaSymbol::get\_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Recupera el token que contiene de este símbolo.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es constante.|  
|[IDiaSymbol::get\_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Recupera el número de elementos de una lista o matriz.|  
|[IDiaSymbol::get\_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Recupera el número de intervalos de dirección válidos asociados al símbolo local.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Recupera una marca que indica si la función utiliza una convención de llamada personalizada.|  
|[IDiaSymbol::get\_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Recupera los bytes de datos desde un símbolo de OEM.|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Recupera la clasificación variable de un token de los datos.|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Recupera el marcador que describe las características de editar y Continuar del programa o unidad compilado.|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Recupera una marca que indica si la función utiliza un aún return.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Recupera el número de versión principal front\-end.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Recupera el número de versión secundaria front\-end.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Recupera el número de compilación front\-end.|  
|[IDiaSymbol::get\_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Recupera una marca que indica si el símbolo público hace referencia a una función.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Recupera el GUID del símbolo.|  
|[IDiaSymbol::get\_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Recupera una marca que indica si la función contiene una llamada a `alloca`.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene algunos operadores de asignación definido.|  
|[IDiaSymbol::get\_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene algunos operadores de conversión definido.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Recupera una marca que indica si el compilando contiene alguna información de depuración.|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Recupera una marca que indica si la función tiene el controlador de excepciones de C\+\+. \+\+\-style.|  
|[IDiaSymbol::get\_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Recupera una marca que indica si la función tiene un controlador de excepciones asincrónico.|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Recupera una marca que indica si la función tiene el ensamblado alineado.|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Recupera una marca que indica si la función contiene un comando de longjmp \(parte de excepción de estilo C que administra\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Recupera una marca que indica si el módulo contiene código administrado.|  
|[IDiaSymbol::get\_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Recupera una marca que indica si el tipo de datos definido por el usuario tiene definiciones de tipo anidado.|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Recupera una marca que indica si la función o el compilando tiene comprobaciones de seguridad compiladas en \(mediante el modificador del compilador [\/GS \(Comprobación de seguridad del búfer\)](/visual-cpp/build/reference/gs-buffer-security-check) \).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Recupera una marca que indica si la función tiene control estructurado de excepciones de estilo Win32.|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Recupera una marca que indica si la función contiene un comando setjmp.|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es una clase base virtual indirecta.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Recupera una marca que indica si la función está marcado con el atributo alineado.|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Recupera una marca que indica si la función tiene un retorno de la instrucción de la interrupción.|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Recupera una marca que indica si la función es la función virtual de clase base.|  
|[IDiaSymbol::get\_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Recupera una marca que indica si el token corresponde a una variable local compartida grupo en código compilado para el Acelerador de AMP en cuestión.|  
|[IDiaSymbol::get\_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Recupera una marca que indica si el token corresponde *al símbolo del intervalo de la definición* del componente de la etiqueta de una variable de puntero en el código compilado para el Acelerador de AMP en cuestión.  El símbolo de intervalo de definición es la ubicación de una variable para un intervalo de direcciones.|  
|[IDiaSymbol::get\_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Indica si el token corresponde a un token de nivel superior de la función para un sombreador compilado para un acelerador que corresponde a `parallel_for_each` una llamada.|  
|[IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Recupera una marca que indica si los datos son parte de un agregado de muchos símbolos.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Recupera una marca que indica si el archivo de símbolos contiene C Types.|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Recupera una marca que indica si el módulo se ha convertido de lenguaje intermedio común \(CIL\) a código nativo.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Recupera una marca que indica si los elementos de un tipo de datos definido por el usuario están alineados con un límite específico.|  
|[IDiaSymbol::get\_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Especifica si este símbolo representa los datos de \(HLSL\) de lenguaje de Sombreador de Alto\- nivel.|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Recupera una marca que indica si el módulo se compiló con el modificador del compilador [\/hotpatch \(Crear una imagen a la que se puede aplicar una revisión reciente\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) .|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Recupera una marca que indica si el compilando administrado se ha vinculado con el LTCG del vinculador.|  
|[IDiaSymbol::get\_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Especifica si la matriz es principal de la fila.|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Recupera una marca que indica si el compilando administrado es En.  netmodule \(que solo contiene metadatos\).|  
|[IDiaSymbol::get\_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Especifica si los puntos del puntero de `this` un miembro de datos con herencia múltiple.|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Recupera una marca que indica si la función tiene el atributo de [naked](/visual-cpp/cpp/naked-cpp) .|  
|[IDiaSymbol::get\_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Especifica si la variable está optimizada aún.|  
|[IDiaSymbol::get\_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Especifica si el puntero de `this` está basado en un valor de símbolo.|  
|[IDiaSymbol::get\_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Especifica si este símbolo es un puntero a un miembro de datos.|  
|[IDiaSymbol::get\_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Especifica si este símbolo es un puntero a una función miembro.|  
|[IDiaSymbol::get\_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Especifica si la variable contiene un valor devuelto.|  
|[IDiaSymbol::get\_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Especifica si el módulo está compilado con la opción \/SDL.|  
|[IDiaSymbol::get\_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Especifica si los puntos del puntero de `this` un miembro de datos con herencia única.|  
|[IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Recupera una marca que indica si los datos han dividido en un agregado de símbolos independientes.|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Recupera una marca que indica si una función o un nivel de procesador es estático.|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Recupera una marca que indica si los símbolos privados se han eliminado del archivo de símbolos.|  
|[IDiaSymbol::get\_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Especifica si los puntos del puntero de `this` un miembro de datos con herencia virtual.|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Recupera el idioma de origen.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Recupera el número de bytes de memoria utilizados por el objeto representado por este símbolo.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Recupera una referencia al elemento primario léxico de símbolos.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Recupera el identificador primario léxico de símbolos.|  
|[IDiaSymbol::get\_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Recupera el nombre de archivo de la biblioteca o el archivo objeto del objeto se cargó.|  
|[IDiaSymbol::get\_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Devuelve la longitud del intervalo de dirección en el que el símbolo local es válido.|  
|[IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Devuelve la parte de la sección de intervalos de dirección inicial en el que el símbolo local es válido.|  
|[IDiaSymbol::get\_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Devuelve el desplazamiento de intervalo de dirección inicial en el que el símbolo local es válido.|  
|[IDiaSymbol::get\_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Devuelve el inicio del intervalo del que el símbolo local es válido.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Recupera el tipo de la ubicación de un token de los datos.|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Recupera el enlazado inferior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Recupera el identificador del símbolo de enlazado inferior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Recupera el tipo de destino CPU.|  
|[IDiaSymbol::get\_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Recupera una marca que indica si el token hace referencia a código administrado.|  
|[IDiaSymbol::get\_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Recupera la clase del espacio de memoria.|  
|[IDiaSymbol::get\_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Recupera una marca que indica si el token hace referencia al Lenguaje intermedio de Microsoft \(MSIL\) codificada.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Recupera el nombre de símbolo.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Recupera una marca que indica si anidados al tipo de datos definido por el usuario.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Recupera una marca que indica si la función se marca con el atributo de [noinline](/visual-cpp/cpp/noinline) .|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Recupera una marca que indica si la función se ha declarado con el atributo de [noreturn](/visual-cpp/cpp/noreturn) .|  
|[IDiaSymbol::get\_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Recupera una marca que indica si el ningún orden de pila se podría realizar como parte de comprobar de búfer de la pila.|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Recupera una marca que indica si la función o la etiqueta nunca se tiene acceso.|  
|[IDiaSymbol::get\_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Devuelve el número de etiquetas de puntero de aceleradores en la función de código auxiliar de AMP en cuestión.|  
|[IDiaSymbol::get\_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Recupera el número de modificadores que se aplican al tipo original.|  
|[IDiaSymbol::get\_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Recupera el número de índices de registro.|  
|[IDiaSymbol::get\_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Recupera el número de filas de la matriz.|  
|[IDiaSymbol::get\_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Recupera el número de columnas de la matriz.|  
|[IDiaSymbol::get\_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Recupera el nombre de archivo de objeto.|  
|[IDiaSymbol::get\_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Recupera el tipo de puntero de objeto para un método de clase.|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Recupera el valor de `oemId` de símbolos.|  
|[IDiaSymbol::get\_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Recupera el valor de `oemSymbolId` de símbolos.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Recupera el desplazamiento de la ubicación del símbolo.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Recupera una marca que indica si la función o la etiqueta contiene código junto con información de depuración optimizados.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Recupera una marca que indica si el tipo de datos definido por el usuario ha sobrecargado operadores.|  
|[IDiaSymbol::get\_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Recupera una marca que indica si se empaquetan al tipo de datos definido por el usuario.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Recupera la plataforma escrita para la que el programa o el compilando se compiló.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Recupera una marca que indica si la función es virtual pura.|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Recupera la fila de una matriz multidimensional de FORTRAN.|  
|[IDiaSymbol::get\_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Recupera una marca que indica si un tipo de puntero es una referencia.|  
|[IDiaSymbol::get\_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Recupera el designador de registro de la ubicación.|  
|[IDiaSymbol::get\_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Recupera el tipo de registro.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Recupera la dirección relativa virtual \(RVA\) location.|  
|[IDiaSymbol::get\_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Especifica si el puntero de `this` está marcado como limitado.|  
|[IDiaSymbol::get\_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Recupera la ranura de dechado.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Recupera una marca que indica si el tipo de datos definido por el usuario aparece en un ámbito léxico nonglobal.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Recupera el valor de la signatura de símbolos.|  
|[IDiaSymbol::get\_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Recupera el tamaño de un miembro de un tipo definido por el usuario.|  
|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Recupera el número de ranura de la ubicación.|  
|[IDiaSymbol::get\_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Recupera el nombre del archivo de código fuente.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Recupera el archivo de código fuente y el número de línea que indica dónde se define un tipo definido por el usuario especificado.|  
|[IDiaSymbol::get\_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Recupera el paso grande de matriz o matriz strided.|  
|[IDiaSymbol::get\_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Recupera el tipo sub.|  
|[IDiaSymbol::get\_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Recupera el identificador de tipo sub|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Recupera el nombre de archivo de que los símbolos se cargaron.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Recupera el identificador único del token.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Recupera el clasificador del tipo de token.|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Recupera la sección compensada de un destino del procesador.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Recupera la dirección relativa virtual \(RVA\) de un destino del procesador.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Recupera la sección de dirección de un destino del procesador.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Recupera la dirección virtual \(VA\) de un destino del procesador.|  
|[IDiaSymbol::get\_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Recupera la ranura de textura.|  
|[IDiaSymbol::get\_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Recupera el ajustador lógico de `this` para el método.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Recupera el tipo de procesador de una función.|  
|[IDiaSymbol::get\_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Recupera la marca de tiempo del archivo ejecutable subyacente.|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Recupera el token de metadatos de una función o variable administrada.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Recupera una referencia a la signatura de la función.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Recupera el identificador del tipo de token.|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Recupera una matriz de valores de tipo compilador\- específicos para este símbolo.|  
|[IDiaSymbol::get\_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Recupera una matriz de valores compilador\- específicos de identificador del tipo para este símbolo.|  
|[IDiaSymbol::get\_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Recupera la ranura de uav.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Recupera la variedad de un tipo definido por el usuario \(UDT\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es sin alinear.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Recupera el nombre representativo para C\+\+. representativo, o el acoplamiento, nombre.|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|La extensión del método de `get_undecoratedName` que recupera el nombre representativo basándose en el valor de un campo de extensión.|  
|[IDiaSymbol::get\_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Recupera el id. de original \(sin modificar\) con tipo.|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Recupera el límite superior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Recupera el identificador del símbolo de límite superior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Recupera el valor de una constante.|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Recupera una marca que indica si la función es virtual.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Recupera la dirección virtual \(VA\) location.|  
|[IDiaSymbol::get\_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Recupera una marca que indica si el tipo de datos definido por el usuario es una clase base virtual.|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Recupera el índice a la tabla de desplazamiento de base virtual.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Recupera el desplazamiento en la tabla de función virtual de una función virtual.|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Recupera el desplazamiento del puntero base virtual.|  
|[IDiaSymbol::get\_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Recupera el tipo de un puntero virtual de la tabla base.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Recupera la interfaz del tipo de la tabla virtual de un tipo definido por el usuario.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Recupera el identificador de la tabla de símbolos.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Recupera una marca que indica si el tipo de datos definido por el usuario son volátiles.|  
  
## Comentarios  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando a uno de los métodos siguientes:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## Ejemplo  
 En este ejemplo se muestra cómo mostrar variables locales para una función en una dirección relativa virtual especificada.  También muestra cómo los símbolos de diferentes tipos se relacionan entre sí.  
  
> [!NOTE]
>  `CDiaBSTR` es una clase que contiene `BSTR` y automáticamente identificadores que liberan la cadena cuando la instancia sale del ámbito.  
  
```cpp#  
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
  
## Requisitos  
 `Header:` Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compiland](../../debugger/debug-interface-access/compiland.md)