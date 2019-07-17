---
title: SccWillCreateSccFile (función) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147962"
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
  
 nFiles  
 [in] El número de nombres de archivo incluidos en el `lpFileNames` de matriz, así como la longitud de la `pbSccFiles` matriz.  
  
 lpFileNames  
 [in] Una matriz de nombres de archivo completo para comprobar (matriz debe ser asignada por llamador).  
  
 pbSccFiles  
 [in, out] Matriz en la que se va a almacenar los resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|DESCRIPCIÓN|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función se invoca con una lista de archivos para determinar si el complemento de control de código fuente proporciona soporte técnico en el MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos indicados (para obtener más información sobre la MSSCCPRJ. Archivo de control de código fuente, consulte [MSSCCPRJ. Archivo de SCC](../extensibility/mssccprj-scc-file.md)). Pueden declarar los complementos de control de código fuente si tienen la capacidad de crear MSSCCPRJ. Archivos CCF declarando `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por archivo en el `pbSccFiles` matriz para indicar cuál de los archivos indicados tiene MSSCCPRJ. Soporte técnico de SCC. Si el complemento devuelve un código de éxito de la función, se respetan los valores de la matriz de devolución. En caso de error, se omite la matriz.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
