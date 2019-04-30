---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417882"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

EN DESUSO. NO USE.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre debe devolver una implementación `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
  
> [!WARNING]
> Como de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], este método ya no se usa y siempre debe devolver `E_NOTIMPL`.  
  
 Este método se llama cuando el depurador se cierra inesperadamente. Cuando se llama a este método, la DE debe reanudarse el programa como si el usuario separa de él. No hay más eventos de depuración se deben enviar. El programa debe estar en un estado donde adjuntable desde otra instancia del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
