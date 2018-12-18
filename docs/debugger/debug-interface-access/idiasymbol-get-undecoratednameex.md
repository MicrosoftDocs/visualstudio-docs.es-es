---
title: Get_undecoratednameex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de8eb57e8b1e31be835163e67fa12e3cd6556892
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930666"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Recupera parte o todo un nombre no representativo de C++ representativo nombre (vinculación).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `undecoratedOptions`  
 [in] Especifica una combinación de marcas que controlan lo que se devuelve. Consulte la sección Comentarios para los valores específicos y qué hacen.  
  
 `pRetVal`  
 [out] Devuelve que el nombre no representativo de C++ nombre representativo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 El `undecorateOptions` puede ser una combinación de los siguientes indicadores.  
  
> [!NOTE]
>  Los nombres de marca no se definen en el SDK de DIA, por lo que deberá agregar las declaraciones en el código o utilizar los valores sin procesar.  
  
|Marcar|Valor|Descripción|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Habilita undecoration completa.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0 x 0001|Quita los caracteres de subrayado de Microsoft ampliar las palabras clave.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Deshabilita la expansión de extendidas palabras clave de Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Deshabilita la expansión de tipo de valor devuelto para la declaración principal.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Deshabilita la expansión del modelo de declaración.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Deshabilita la expansión del especificador de declaración lenguaje.|  
|UNDNAME_RESERVED1|0x0020|RESERVADO.|  
|UNDNAME_RESERVED2|0x0040|RESERVADO.|  
|UNDNAME_NO_THISTYPE|0x0060|Deshabilita todos los modificadores en el `this` tipo.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0 x 0080|Deshabilita la expansión de especificadores de acceso para los miembros.|  
|UNDNAME_NO_THROW_SIGNATURES|0 x 0100|Deshabilita la expansión de "throw-firmas" para las funciones y punteros a funciones.|  
|UNDNAME_NO_MEMBER_TYPE|0 x 0200|Deshabilita la expansión de `static` o `virtual` miembros.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0 x 0400|Deshabilita la expansión del modelo de Microsoft para UDT se devuelve.|  
|UNDNAME_32_BIT_DECODE|0 x 0800|Undecorates nombres representativos de 32 bits.|  
|UNDNAME_NAME_ONLY|0 x 1000|Obtiene solo el nombre de declaración principal; devuelve simplemente [ámbito::] nombre.  Expande los parámetros de plantilla.|  
|UNDNAME_TYPE_ONLY|0 x 2000|La entrada es un tipo de codificación; crea un declarador abstracto.|  
|UNDNAME_HAVE_PARAMETERS|0 x 4000|Los parámetros de plantilla reales están disponibles.|  
|UNDNAME_NO_ECSU|0 x 8000|Suprime la enumeración, clase, struct o unión.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0 x 10000|Suprime la comprobación de caracteres de identificador válidos.|  
|UNDNAME_NO_PTR64|0 x 20000|No incluye ptr64 en la salida.|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)