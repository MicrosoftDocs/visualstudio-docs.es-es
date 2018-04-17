---
title: IDebugExpressionContext2::ParseText | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e95a8a76e7315f8963ea415f88bd9615f3b123a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analiza una expresión en formato de texto para su posterior evaluación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```csharp  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in] Expresión que se puede analizar.  
  
 `dwFlags`  
 [in] Una combinación de indicadores de la [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) enumeración que controla el análisis.  
  
 `nRadix`  
 [in] La base para su uso en análisis cualquier información numérica en `pszCode`.  
  
 `ppExpr`  
 [out] Devuelve el [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) objeto que representa la expresión analizada, que está lista para el enlace y evaluación.  
  
 `pbstrError`  
 [out] Devuelve el mensaje de error si la expresión contiene un error.  
  
 `pichError`  
 [out] Devuelve el índice de carácter del error en `pszCode` si la expresión contiene un error.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, un motor de depuración (Alemania) debe analizar la expresión y validar son correctos. El `pbstrError` y `pichError` se pueden rellenar parámetros si la expresión no es válida.  
  
 Tenga en cuenta que no se evalúa la expresión, solo se analiza. Una llamada posterior a la [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) métodos evalúa la expresión analizada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un sencillo `CEnvBlock` objeto que expone la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. En este ejemplo se considera que la expresión que se va a analizar como el nombre de una variable de entorno y se recupera el valor de esa variable.  
  
```cpp  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)