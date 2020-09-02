---
title: Función SccWillCreateSccFile | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147962"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función determina si el complemento de control de código fuente admite la creación de MSSCCPRJ. Archivo SCC para cada uno de los archivos especificados.  
  
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
 de Puntero de contexto del complemento de control de código fuente.  
  
 N archivos  
 de El número de nombres de archivo incluidos en la `lpFileNames` matriz, así como la longitud de la `pbSccFiles` matriz.  
  
 lpFileNames  
 de Una matriz de nombres de archivo completos que se van a comprobar (el llamador debe asignar la matriz).  
  
 pbSccFiles  
 [in, out] Matriz en la que se almacenan los resultados.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a esta función con una lista de archivos para determinar si el complemento de control de código fuente proporciona compatibilidad en MSSCCPRJ. Archivo SCC para cada uno de los archivos especificados (para obtener más información sobre MSSCCPRJ). Archivo SCC, vea [MSSCCPRJ. Archivo SCC](../extensibility/mssccprj-scc-file.md)). Los complementos de control de código fuente pueden declarar si tienen la capacidad de crear MSSCCPRJ. Archivos SCC declarando `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por archivo de la `pbSccFiles` matriz para indicar cuál de los archivos especificados tiene MSSCCPRJ. Compatibilidad con SCC. Si el complemento devuelve un código de éxito de la función, se respetan los valores de la matriz devuelta. En caso de error, se omite la matriz.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
