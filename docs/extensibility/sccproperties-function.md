---
title: SccProperties (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74eae3272563fb3514bedfd57fb3d94c98d98193
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818854"
---
# <a name="sccproperties-function"></a>SccProperties (Función)
Esta función muestra las propiedades de control de origen para un archivo o proyecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 [in] El nombre de ruta de acceso completa del archivo o proyecto.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Las propiedades se muestran correctamente.|  
|SCC_I_RELOADFILE|El sistema de control de versiones modificó las propiedades del archivo, por lo que el IDE debe volver a cargar este archivo.|  
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto especificado en el control de código fuente.|  
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para ver las propiedades de este archivo o proyecto.|  
|SCC_E_FILENOTCONTROLLED|El archivo especificado o el proyecto no está bajo control de código fuente.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Se ha producido un error desconocido o general.|  
  
## <a name="remarks"></a>Comentarios  
 El complemento de control de código fuente muestra las propiedades en su propio cuadro de diálogo.  
  
 Las propiedades se definen mediante el complemento de control de código fuente y pueden diferir de complemento al complemento. Si el complemento permite al usuario cambiar las propiedades del control de código fuente de un archivo, debe devolver `SCC_I_RELOAD` para señalar el IDE, que es necesario recargar este archivo o proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)