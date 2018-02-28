---
title: IDiaFrameData | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9ecbc6d6bd94c3b6ed58b1afe8f1c090aca82e36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedata"></a>IDiaFrameData
Expone los detalles de un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaFrameData`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Recupera el elemento de sección de la dirección de código para el marco.|  
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Recupera el desplazamiento parte de la dirección de código para el marco.|  
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Recupera la imagen dirección virtual relativa (RVA) del código para el marco.|  
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Recupera la dirección virtual (VA) del código para el marco.|  
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Recupera la longitud, en bytes, del bloque de código descrito por el marco.|  
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Recupera el número de bytes de las variables locales que se insertan en la pila.|  
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Recupera el número de bytes de parámetros que se insertan en la pila.|  
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Recupera el número máximo de bytes que se insertan en la pila en el marco.|  
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Recupera el número de bytes del código de prólogo en el bloque.|  
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Recupera el número de bytes de registros guardados insertado en la pila.|  
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Recupera la cadena de programa que se utiliza para calcular el conjunto antes de llamar a la función actual de registros.|  
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Recupera una marca que indica que control de excepciones del sistema está en vigor.|  
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Recupera una marca que indica que control de excepciones de C++ está en vigor.|  
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Recupera una marca que indica que el bloque contiene el punto de entrada de una función.|  
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Recupera una marca que indica que el puntero base se asigna para el código en este intervalo de direcciones. Este método está en desuso.|  
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Recupera el tipo de marco específicos del compilador.|  
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Recupera la interfaz de datos para incluir la función de marco.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Realiza el desenredo de la pila y devuelve el estado actual de registros en una interfaz de marco de recorrido de pila.|  
  
## <a name="remarks"></a>Comentarios  
 Los detalles disponibles para un marco son para los puntos de ejecución dentro del intervalo de dirección indicado por la longitud de dirección y el bloque.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Obtener esta interfaz mediante una llamada a la [idiaenumframedata:: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) o [idiaenumframedata:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) métodos. Consulte la [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaz para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo imprime las propiedades de un `IDiaFrameData` objeto. Consulte la [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) interfaz para obtener un ejemplo de cómo el `IDiaFrameData` se obtiene la interfaz.  
  
```C++  
void PrintFrameData(IDiaFrameData* pFrameData){  
    DWORD dwSect;  
    DWORD dwOffset;  
    DWORD cbBlock;  
    DWORD cbLocals; // Number of bytes reserved for the function locals  
    DWORD cbParams; // Number of bytes reserved for the function arguments  
    DWORD cbMaxStack;  
    DWORD cbProlog;  
    DWORD cbSavedRegs;  
    BOOL  bSEH;  
    BOOL  bEH;  
    BOOL  bStart;  
    BSTR  wszProgram;  
  
    if(pFrameData->get_addressSection(&dwSect) == S_OK &&   
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&  
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&  
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&  
       pFrameData->get_lengthParams(&cbParams) == S_OK &&  
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&  
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&  
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&  
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&  
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&  
       pFrameData->get_functionStart(&bStart) == S_OK )  
    {  
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);  
        wprintf(L"Block size     : 0x%8X\n", cbBlock);  
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);  
        wprintf(L"Parms size     : 0x%8X\n", cbParams);  
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);  
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);  
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);  
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');  
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');  
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');  
  
        if (pFrameData->get_program(&wszProgram) == S_OK)  
        {  
            wprintf(L"Program used for register set: %s\n", wszProgram);  
            SysFreeString(wszProgram);  
        }  
        else  
        {  
            wprintf(L"\n");  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [Idiaenumframedata:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)