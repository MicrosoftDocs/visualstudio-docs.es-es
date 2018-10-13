---
title: IDiaStackFrame | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ccba9d5b400e553960b1fc1451870d601210a11
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224476"
---
# <a name="idiastackframe"></a>IDiaStackFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Expone las propiedades de un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Estos son los métodos admitidos por esta interfaz:  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Recupera una marca que indica que el puntero base está asignado para el código de este intervalo de direcciones. Este método está en desuso.|  
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Recupera la base de la dirección del marco.|  
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Recupera una marca que indica que el control de excepciones de C++ está en vigor.|  
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Recupera una marca que indica que el bloque contiene el punto de entrada de una función.|  
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Recupera el número de bytes de las variables locales que se insertan en la pila.|  
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Recupera el número de bytes de los parámetros que se insertan en la pila.|  
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Recupera el número de bytes del código de prólogo en el bloque|  
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Recupera el número de bytes de registros guardadas insertado en la pila.|  
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Recupera la base de la dirección de las variables locales.|  
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Recupera el número máximo de bytes que se insertan en la pila en el marco.|  
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Recupera el valor de la variable local especificada como bytes sin formato.|  
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Recupera el valor de un registro especificado.|  
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Recupera la dirección de devolución del marco.|  
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Recupera el tamaño del fotograma en bytes.|  
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Recupera una marca que indica que el control de excepciones del sistema está en vigor.|  
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Recupera el tipo de marco.|  
  
## <a name="remarks"></a>Comentarios  
 Un marco de pila es una abstracción de una llamada de función durante su ejecución.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la [Idiaenumstackframes](../../debugger/debug-interface-access/idiaenumstackframes-next.md) método. Consulte la [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) interfaz para obtener un ejemplo sobre cómo obtener el `IDiaStackFrame` interfaz.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra varios atributos de un marco de pila.  
  
```cpp#  
void PrintStackFrame(IDiaStackFrame* pFrame)  
{  
    if (pFrame != NULL)  
    {  
        ULONGLONG bottom = 0;  
        ULONGLONG top    = 0;  
  
        if (pFrame->get_base(&bottom) == S_OK &&  
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )  
        {  
             printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);  
        }  
  
        ULONGLONG returnAddress = 0;  
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)  
        {  
             printf("return address = 0x%08I64x\n", returnAddress);  
        }  
  
        DWORD lengthFrame     = 0;  
        DWORD lengthLocals    = 0;  
        DWORD lengthParams    = 0;  
        DWORD lengthProlog    = 0;  
        DWORD lengthSavedRegs = 0;  
        if (pFrame->get_size(&lengthFrame) == S_OK &&  
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&  
            pFrame->get_lengthParams(&lengthParams) == S_OK &&  
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&  
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)  
        {  
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);  
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);  
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);  
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);  
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 Archivo DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [Idiaenumstackframes](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



