---
title: SccWillCreateSccFile (función) | Documentos de Microsoft
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
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60152353eb7ef41af3abab9fcf06d81f425442dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263002"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función determina si el complemento de control de código fuente admite la creación de la MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos indicados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 n  
 [in] El número de nombres de archivo incluidos en el `lpFileNames` de matriz, así como la longitud de la `pbSccFiles` matriz.  
  
 lpFileNames  
 [in] Una matriz de nombres de archivo completo para comprobar (matriz debe ser asignada por llamador).  
  
 pbSccFiles  
 [in, out] Matriz en la que se va a almacenar los resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca con una lista de archivos para determinar si el complemento de control de código fuente proporciona soporte técnico en el MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos indicados (para obtener más información sobre la MSSCCPRJ. Archivo de control de código fuente, consulte [MSSCCPRJ. Archivo de SCC](../extensibility/mssccprj-scc-file.md)). Pueden declarar los complementos de control de código fuente si tienen la capacidad de crear MSSCCPRJ. Archivos CCF declarando `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por archivo en el `pbSccFiles` matriz para indicar cuál de los archivos indicados tiene MSSCCPRJ. Soporte técnico de SCC. Si el complemento devuelve un código de éxito de la función, se respetan los valores de la matriz de devolución. En caso de error, se omite la matriz.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

