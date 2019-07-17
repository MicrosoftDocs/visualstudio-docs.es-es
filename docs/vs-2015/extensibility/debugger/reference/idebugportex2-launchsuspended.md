---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188451"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Inicia un archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```csharp  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszExe`  
 [in] El nombre del archivo ejecutable que se iniciará. Esto puede ser una ruta de acceso completa o relativa al directorio de trabajo especificado en el `pszDir` parámetro.  
  
 `pszArgs`  
 [in] Los argumentos para pasar al ejecutable. Puede ser un valor null si no hay ningún argumento.  
  
 `pszDir`  
 [in] El nombre del directorio de trabajo usando el archivo ejecutable. Puede ser un valor null si no se requiere ningún directorio de trabajo.  
  
 `bstrEnv`  
 [in] Bloque de entorno de cadenas terminadas en null, seguido de un terminador NULL adicional.  
  
 `hStdInput`  
 [in] Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere la redirección.  
  
 `hStdOutput`  
 [in] Identificador de un flujo de salida alternativos. Puede ser 0 si no se requiere la redirección.  
  
 `hStdError`  
 [in] Identificador de un flujo de salida de error alternativa. Puede ser 0 si no se requiere la redirección.  
  
 `ppPortProcess`  
 [out] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el proceso iniciado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método debería iniciar el proceso, por lo que TI está suspendida y no se está ejecutando ningún código. El [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) método se llama para reanudar el proceso.  
  
 También se puede iniciar un programa desde un motor de depuración. Para obtener más información, consulte [iniciar un programa](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Inicio de un programa](../../../extensibility/debugger/launching-a-program.md)
