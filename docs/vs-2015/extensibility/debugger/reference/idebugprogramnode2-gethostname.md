---
title: IDebugProgramNode2::GetHostName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b84d51d92e12dfc5fdb744c10d5b6cc13a606d95
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836247"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el nombre del proceso que hospeda el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetHostName (   
   GETHOSTNAME_TYPE dwHostNameType,  
   BSTR*            pbstrHostName  
);  
```  
  
```csharp  
int GetHostName (   
   enum_GETHOSTNAME_TYPE dwHostNameType,  
   out string            pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwHostNameType`  
 [in] Un valor de la [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeración que especifica el tipo de nombre para devolver.  
  
 `pbstrHostName`  
 [out] Devuelve el nombre del proceso de hospedaje.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto que expone el [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz. En este ejemplo pasa por alto el `dwHostNameType` parámetro y devuelve solo el nombre del programa tal y como se toma del nombre de base de la ruta de acceso de archivo del módulo.  
  
```cpp#  
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {    
   // Check for valid argument.    
   if (pbstrHostName)    
   {    
      char szModule[_MAX_PATH];    
  
      // Attempt to assign to szModule the path for the file used  
      // to create the calling process.    
      if (GetModuleFileName(NULL, szModule, sizeof (szModule)))    
      {    
         // If successful then declare several char arrays    
         char  szDrive[_MAX_DRIVE];    
         char  szDir[_MAX_DIR];    
         char  szName[_MAX_FNAME];    
         char  szExt[_MAX_EXT];    
         char  szFilename[_MAX_FNAME + _MAX_EXT];    
         WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];    
  
         // Break the szModule path name into components.    
         _splitpath(szModule, szDrive, szDir, szName, szExt);    
  
         // Copy the base file name szName into szFilename.    
         lstrcpy(szFilename, szName);    
         // Append the field extension szExt into szFilename.    
         lstrcat(szFilename, szExt);    
  
         // Convert the szFilename sequence of multibyte characters    
         // to the wszFilename sequence of wide characters.    
         mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);    
  
         // Assign the wszFilename to the value at *pbstrHostName.    
         *pbstrHostName = SysAllocString(wszFilename);    
  
          return S_OK;    
      }    
   }    
  
    return E_INVALIDARG;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

