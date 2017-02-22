---
title: "Jerarqu&#237;a l&#233;xica de tipos de s&#237;mbolos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "símbolos [SDK de DIA], jerarquías de tipo"
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Jerarqu&#237;a l&#233;xica de tipos de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tabla siguiente muestra los tipos de símbolo en la jerarquía léxica.  
  
## Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|---------------------|-----------------|  
|[Anotación](../../debugger/debug-interface-access/annotation.md)|especifica una ubicación anotada en código de programa.|  
|[Bloque](../../debugger/debug-interface-access/block.md)|Especifica anidado ámbitos en funciones.|  
|`Compiland`|Especifica `compiland` vinculado al archivo .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica los datos de compilación que pueden requerir cargar los detalles adicionales de compilación e incurrir en así sobrecarga en tiempo de ejecución para recuperar.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica una variable de entorno adicional significativa a la compilación de compilación.|  
|[Personalizado \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|especifica un símbolo definido por el usuario.|  
|[Datos \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica las variables como parámetros, variables locales, variables globales, y los miembros de clase.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|especifica el ámbito global de los datos; corresponde a un archivo completo .exe o .dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica una función con un punto definido en el que la depuración esté final.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica una función con un punto definido en el que la depuración es iniciar.|  
|[Función \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|especifica una función.|  
|[Etiqueta \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|especifica una ubicación en código de programa.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica un símbolo externo que aparece al compilar el programa ejecutable.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|especifica `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|especifica un identificador de `namespace`.|  
  
> [!NOTE]
>  Las propiedades adicionales de símbolos pueden estar disponibles en función del tipo de token.  Estas propiedades se muestran en temas individuales de símbolos.  
  
## Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)