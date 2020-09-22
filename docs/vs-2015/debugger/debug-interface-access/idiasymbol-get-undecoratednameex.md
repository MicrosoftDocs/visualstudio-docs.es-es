---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842891"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera parte o todo un nombre no representativo para un nombre representativo de C++ (vinculación).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `undecoratedOptions`  
 de Especifica una combinación de marcas que controlan lo que se devuelve. Vea la sección Comentarios para conocer los valores específicos y lo que hacen.  
  
 `pRetVal`  
 enuncia Devuelve el nombre no representativo de un nombre representativo de C++.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Notas  
 `undecorateOptions`Puede ser una combinación de las marcas siguientes.  
  
> [!NOTE]
> Los nombres de marca no se definen en el SDK de DIA, por lo que debe agregar las declaraciones al código o usar los valores sin formato.  
  
|Marca|Value|Descripción|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Habilita la desdecoración completa.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Quita los guiones iniciales iniciales de las palabras clave extendidas de Microsoft.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Deshabilita la expansión de las palabras clave extendidas de Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Deshabilita la expansión del tipo de valor devuelto para la declaración principal.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Deshabilita la expansión del modelo de declaración.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Deshabilita la expansión del especificador de lenguaje de declaración.|  
|UNDNAME_RESERVED1|0x0020|RESERVADO.|  
|UNDNAME_RESERVED2|0x0040|RESERVADO.|  
|UNDNAME_NO_THISTYPE|0x0060|Deshabilita todos los modificadores en el `this` tipo.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Deshabilita la expansión de especificadores de acceso para los miembros.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Deshabilita la expansión de las funciones y los punteros a las funciones.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Deshabilita la expansión `static` de `virtual` los miembros o.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Deshabilita la expansión del modelo de Microsoft para las devoluciones UDT.|  
|UNDNAME_32_BIT_DECODE|0x0800|Desdecora los nombres representativos de 32 bits.|  
|UNDNAME_NAME_ONLY|0x1000|Obtiene solo el nombre de la declaración primaria; Devuelve solo [Scope::] name.  Expande los parámetros de la plantilla.|  
|UNDNAME_TYPE_ONLY|0x2000|La entrada es simplemente una codificación de tipos; compone un declarador abstracto.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Los parámetros de plantilla reales están disponibles.|  
|UNDNAME_NO_ECSU|0x8000|Suprime enum/Class/struct/union.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Suprime la comprobación de los caracteres de identificador válidos.|  
|UNDNAME_NO_PTR64|0x20000|No incluye ptr64 en la salida.|  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
