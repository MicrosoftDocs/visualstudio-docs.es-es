---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
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
  - "IDiaSymbol::get_undecoratedNameEx (método)"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera parte o la totalidad del nombre representativo para C\+\+. adornaron nombre \(de vinculación\).  
  
## Sintaxis  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Parámetros  
 `undecoratedOptions`  
 \[in\]  Especifica una combinación de marcadores que controlan se devuelve qué.  Vea la sección comentarios por valores concretos y su hace.  
  
 `pRetVal`  
 \[out\]  Devuelve el nombre representativo del nombre representativo \+\+ de C\/C\+\+.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 `undecorateOptions` puede ser una combinación de los siguientes indicadores.  
  
> [!NOTE]
>  Los nombres de marcador no se definen en el diámetro SDK, de modo que necesita agregar las declaraciones en el código o utilizar los valores sin formato.  
  
|Marcador|Valor|Descripción|  
|--------------|-----------|-----------------|  
|UNDNAME\_COMPLETE|0x0000|habilita el undecoration completo.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Quita subrayado principales de Microsoft extendidas las palabras clave.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Deshabilita la extensión de Microsoft extendidas las palabras clave.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|Deshabilita la extensión del tipo de valor devuelto para la declaración primaria.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Deshabilita la extensión del modelo de la declaración.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Deshabilita la extensión del especificador de lenguaje de la declaración.|  
|UNDNAME\_RESERVED1|0x0020|RESERVADO.|  
|UNDNAME\_RESERVED2|0x0040|RESERVADO.|  
|UNDNAME\_NO\_THISTYPE|0x0060|Deshabilita todos los modificadores en el tipo de `this` .|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Deshabilita la extensión de los especificadores de acceso para los miembros.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Deshabilita la extensión de “tiro\-firmas” para las funciones y los punteros a funciones.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|Deshabilita la extensión de `static` o los miembros de `virtual` .|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Deshabilita la extensión del modelo de Microsoft para el UDT devuelve.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Nombres representativos de 32 bits de Undecorates.|  
|UNDNAME\_NAME\_ONLY|0x1000|Obtiene únicamente el nombre de la declaración primaria; devuelve solo \[ámbito::\] nombre.  Expanda params de la plantilla.|  
|UNDNAME\_TYPE\_ONLY|0x2000|La entrada es una codificación de tipo; cree un declarador abstracto.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|Los parámetros reales de la plantilla están disponibles.|  
|UNDNAME\_NO\_ECSU|0x8000|Suprime la enumeración o la clase\/struct\/union.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Suprime la comprobación de caracteres de identificador válidos.|  
|UNDNAME\_NO\_PTR64|0x20000|No incluye ptr64 en la salida.|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)