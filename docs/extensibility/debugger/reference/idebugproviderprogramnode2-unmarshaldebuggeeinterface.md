---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c0f09d5b5fb1d420eef6b91ea596adbcab665ded
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtiene una interfaz especificada a través de límites de proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `riid`  
 [in] GUID de la interfaz se debe obtener.  
  
 `ppvObject`  
 [out] Devuelve el objeto que implementa la interfaz deseada. [C++] se puede convertir directamente en el tipo de interfaz deseado. [C#] use la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener la interfaz deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se utiliza cuando el motor de depuración se ejecuta en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espacio del proceso y el programa que se está depurando se ejecuta en su propio espacio de proceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)