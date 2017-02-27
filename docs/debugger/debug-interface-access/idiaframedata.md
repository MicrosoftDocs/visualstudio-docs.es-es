---
title: "IDiaFrameData | Microsoft Docs"
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
  - "IDiaFrameData (interfaz)"
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaFrameData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

expone los detalles de un marco de pila.  
  
## Sintaxis  
  
```  
IDiaFrameData : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaFrameData`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaFrameData::get\_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Recuperar la parte de la sección de código de dirección para el cuadro.|  
|[IDiaFrameData::get\_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Recupera el desplazamiento del código de la dirección del cuadro.|  
|[IDiaFrameData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Recupera la dirección virtual relativa de la \(RVA\) imagen del cuadro.|  
|[IDiaFrameData::get\_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Recupera la dirección virtual \(VA\) de código para el cuadro.|  
|[IDiaFrameData::get\_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Recupera la longitud, en bytes, del bloque de código descrito en el cuadro.|  
|[IDiaFrameData::get\_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|recupera el número de bytes de variables locales insertadas en la pila.|  
|[IDiaFrameData::get\_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|recupera el número de bytes de parámetros insertados en la pila.|  
|[IDiaFrameData::get\_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|recupera el número de bytes máximo insertados en la pila en el cuadro.|  
|[IDiaFrameData::get\_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Recupera el número de bytes de código de prólogo en el bloque.|  
|[IDiaFrameData::get\_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|recupera el número de bytes de registros guardados insertados en la pila.|  
|[IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Recupera la cadena del programa se utiliza para calcular el conjunto de registros antes de la llamada a la función actual.|  
|[IDiaFrameData::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Recupera un mensaje que indica que el control de excepciones en el sistema está en vigor.|  
|[IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Recupera un mensaje que indica que el control de excepciones de C\+\+ está vigente.|  
|[IDiaFrameData::get\_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Recupera un mensaje que indica que el bloque contiene el punto de entrada de una función.|  
|[IDiaFrameData::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Recupera un mensaje que indica que el puntero base está asignado para el código de este intervalo de direcciones.  Este método es obsoleto.|  
|[IDiaFrameData::get\_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Recupera el tipo de fotograma compilador\-específico.|  
|[IDiaFrameData::get\_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Interfaz de los datos del cuadro de recupera para agregar la función.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Realiza la pila que desenredo y devuelve el estado actual de registros en una interfaz de cuadro de recorrido de pila.|  
  
## Comentarios  
 Los detalles disponibles para un cuadro son para los puntos de ejecución dentro del intervalo de direcciones indicado por la dirección y la longitud de bloque.  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando a los métodos de [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) o de [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) .  Vea la interfaz de [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) para obtener detalles.  
  
## Ejemplo  
 este ejemplo imprime las propiedades de un objeto de `IDiaFrameData` .  Vea la interfaz de [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) para obtener un ejemplo de cómo se obtiene la interfaz de `IDiaFrameData` .  
  
```cpp#  
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
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)