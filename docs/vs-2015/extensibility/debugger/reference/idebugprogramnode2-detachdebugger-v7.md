---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842790"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

En desuso. NO USE.  
  
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
 Una implementación siempre debe devolver `E_NOTIMPL` .  
  
## <a name="remarks"></a>Notas  
  
> [!WARNING]
> A partir de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , este método ya no se utiliza y siempre debe devolver `E_NOTIMPL` .  
  
 Se llama a este método cuando el depurador se cierra inesperadamente. Cuando se llama a este método, el DE debe reanudar el programa como si el usuario lo desasociara. No se deben enviar más eventos de depuración. El programa debe estar en un estado en el que se pueda adjuntar desde otra instancia del depurador.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
