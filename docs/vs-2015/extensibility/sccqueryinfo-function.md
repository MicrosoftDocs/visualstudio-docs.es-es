---
title: Función SccQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f951e7ef29fbba7225997276b31bd9f32731efc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199985"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función obtiene información de estado de un conjunto de archivos seleccionados bajo control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 de Estructura de contexto del complemento de control de código fuente.  
  
 N archivos  
 de Número de archivos especificados en la `lpFileNames` matriz y la longitud de la `lpStatus` matriz.  
  
 lpFileNames  
 de Matriz de nombres de los archivos que se van a consultar.  
  
 lpStatus  
 [in, out] Matriz en la que el complemento de control de código fuente devuelve las marcas de estado de cada archivo. Para obtener más información, consulte el [código de estado de archivo](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|La consulta se realizó correctamente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema con el acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Si `lpFileName` es una cadena vacía, actualmente no hay información de estado para actualizar. De lo contrario, es el nombre completo de la ruta de acceso del archivo para el que puede haber cambiado la información de estado.  
  
 La matriz devuelta puede ser una máscara de `SCC_STATUS_xxxx` bits. Para obtener más información, consulte el [código de estado de archivo](../extensibility/file-status-code-enumerator.md). Es posible que un sistema de control de código fuente no admita todos los tipos de bits. Por ejemplo, si `SCC_STATUS_OUTOFDATE` no se ofrece, el bit simplemente no se establece.  
  
 Al usar esta función para desproteger archivos, tenga en cuenta los siguientes `MSSCCI` requisitos de estado:  
  
- `SCC_STATUS_OUTBYUSER` se establece cuando el usuario actual ha desprotegido el archivo.  
  
- `SCC_STATUS_CHECKEDOUT` no se puede establecer a menos que `SCC_STATUS_OUTBYUSER` se establezca.  
  
- `SCC_STATUS_CHECKEDOUT` solo se establece cuando el archivo se desprotege en el directorio de trabajo designado.  
  
- Si el archivo está desprotegido por el usuario actual en un directorio distinto del directorio de trabajo, `SCC_STATUS_OUTBYUSER` se establece pero `SCC_STATUS_CHECKEDOUT` no es.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)
